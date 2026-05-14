---
description: >-
  REST endpoints under /api/skills/ on app.skills.new. These are what sx
  install, sx update, and CI agents call to resolve and download assets.
---

# REST API

The REST API at `https://app.skills.new/api/skills/` is the **asset-distribution surface**. It is what the [`sx`](https://github.com/sleuth-io/sx) CLI uses to resolve which assets a caller should receive, download their bundles, and report usage. CI agents and review bots use it the same way `sx` does, just authenticated as a bot instead of a user.

For management actions (creating bots, editing assets, browsing the audit log, etc.) use the [GraphQL API](graphql.md) instead.

## Conventions

* **Base URL:** `https://app.skills.new`
* **Auth:** every endpoint requires a credential — see [Authentication](authentication.md). Bot API keys are passed with `Authorization: Bearer <token>`.
* **Org scoping:** the credential identifies one organization. There is no `orgSlug` parameter in the URL.
* **Status codes:** `2xx` for success, `400` for invalid input, `401` if the credential is missing or invalid, `404` if the asset/version doesn't exist, `405` for the wrong HTTP method.
* **Caching:** the lock file uses `ETag` / `If-None-Match`; immutable asset bundles set `Cache-Control: public, max-age=31536000, immutable`. Send the `If-None-Match` header on your repeat lock-file requests to get a `304 Not Modified`.

## Endpoint map

| Method | Path | Purpose |
|--------|------|---------|
| `GET` | `/api/skills/sx.lock` | Resolve the full set of assets for the caller. |
| `GET` | `/api/skills/sx.profiles` | List the org's [skill profiles](../manage/skills.md) and the caller's active one. |
| `POST` | `/api/skills/sx.profiles/active` | Set the caller's active skill profile. |
| `GET` | `/api/skills/assets/{name}/list.txt` | List published versions of an asset. |
| `GET` | `/api/skills/assets/{name}/{version}/metadata.toml` | Get the metadata for a specific version. |
| `GET` | `/api/skills/assets/{name}/{version}/{filename}` | Download the asset bundle (a `.zip`). |
| `POST` | `/api/skills/assets` | Upload a new asset version. |
| `POST` | `/api/skills/usage` | Report asset-usage events (JSONL). |
| `POST` | `/api/skills/ai-query/stream` | Stream an AI query against an integration. |

The sections below cover each endpoint.

---

## Lock file

```
GET /api/skills/sx.lock
```

Returns a TOML lock file enumerating every asset the caller should have installed, together with the version pinned for them and a download URL for each. This is the **single source of truth** for what should be on disk after `sx install`.

The lock content is scoped to the caller automatically:

* **User credential** → assets installed to the user, the user's teams, the user's repositories, and the org-wide installs.
* **Bot credential** → assets installed to the bot, the bot's teams, and the org-wide installs.

### Headers

* `If-None-Match: "<etag>"` — recommended. Returns `304 Not Modified` if the lock hasn't changed.
* `x-session-id: <opaque>` — optional. Tagged onto the audit log entry so you can correlate a sequence of calls.
* `user-agent: <client>` — recorded for usage statistics.

### Example

```bash
curl https://app.skills.new/api/skills/sx.lock \
  -H "Authorization: Bearer YOUR_BOT_API_KEY" \
  -H 'If-None-Match: "abc123def456"'
```

Returns `200 OK` with `Content-Type: application/toml` (the lock file) or `304 Not Modified`. The `ETag` response header changes whenever the resolved asset set changes for that caller.

Every successful call is recorded in the [audit log](../govern/audit-log.md) as a `LOCK_FILE_ACCESSED` event with the user agent, client IP, and (for bots) the bot slug and key prefix.

---

## Skill profiles

[Skill profiles](../manage/skills.md) are named subsets of the available asset set — a user (or bot) picks an active profile and the lock file resolves against that profile.

### List profiles

```
GET /api/skills/sx.profiles
```

```json
{
  "profiles": [
    {"title": "Backend",  "slug": "backend",  "description": "Python/Django assets"},
    {"title": "Frontend", "slug": "frontend", "description": "Vue/Nuxt assets"}
  ],
  "active": "backend"
}
```

### Set active profile

```
POST /api/skills/sx.profiles/active
Content-Type: application/json

{"slug": "frontend"}
```

Pass `{"slug": null}` to clear the active profile. Returns the activated profile, or `null` if cleared.

---

## Asset bundles

### List versions

```
GET /api/skills/assets/{asset_name}/list.txt
```

Returns plain text — one published version number per line, newest last. Use it to find the latest version available for an asset before fetching metadata or the bundle.

```
1
2
3
```

### Get version metadata

```
GET /api/skills/assets/{asset_name}/{asset_version}/metadata.toml
```

Returns the TOML metadata for the version: name, description, asset type, dependencies, etc. Bundles are immutable per version, so the response is heavily cached (`Cache-Control: public, max-age=31536000, immutable`).

### Download a bundle

```
GET /api/skills/assets/{asset_name}/{asset_version}/{filename}
```

Returns the zip file. The `{filename}` segment is for HTTP semantics (so browsers and tools pick a sensible filename); the server resolves the bundle from `{asset_name}` and `{asset_version}` alone. Convention is `{name}-{version}.zip`.

```bash
curl -O https://app.skills.new/api/skills/assets/my-skill/3/my-skill-3.zip \
  -H "Authorization: Bearer YOUR_BOT_API_KEY"
```

Each successful download:

1. Queues an install-tracking event (powers the [Adoption](../govern/metrics.md) dashboard).
2. Writes a `DOWNLOADED` event to the [audit log](../govern/audit-log.md) with the caller, the user agent, and (for bots) the key prefix.

### Upload a new version

```
POST /api/skills/assets
Content-Type: multipart/form-data
```

Upload a packaged `.zip` to create a new version of an asset (or the first version of a new asset).

Form fields:

| Field | Required | Description |
|-------|----------|-------------|
| `file` | yes | The `.zip` bundle. Must contain a `metadata.toml` with `name` and `version`. |
| `name` | no | Asset slug. Falls back to `metadata.toml` or the filename. |
| `version` | no | Version string. Used for validation against `metadata.toml`. |
| `type` | no | Asset type — `skill` (default), `agent`, `rule`, `command`, `hook`, `mcp_server`, `plugin`. |
| `installations` | no | JSON array of `{entity_type, entity_id}` objects describing where to install (org, team, repository, user, bot). |
| `owned_by` | no | Legacy fallback if `installations` isn't given — `organization`, `user`, or `repository`. |
| `repository_owner` / `repository_name` | conditional | Required if `owned_by="repository"`. |

Returns `201 Created` with:

```json
{
  "success": true,
  "asset": {
    "name": "my-skill",
    "version": "3",
    "url": "https://app.skills.new/api/skills/assets/my-skill/3/my-skill-3.zip",
    "skill_id": "AS...",
    "is_first_version": false
  }
}
```

---

## Usage reporting

```
POST /api/skills/usage
Content-Type: application/x-ndjson
```

Reports asset-usage events. The body is JSONL — one JSON object per line — with each line describing a single invocation:

```jsonl
{"asset_name": "github-mcp", "asset_version": "1.2.3", "asset_type": "mcp"}
{"asset_name": "django-admin", "asset_version": "2.0.0", "asset_type": "skill"}
```

Returns `204 No Content` once events are queued (processing is async). An empty body is also a valid `204`. Invalid JSONL returns `400`.

Events feed the [Govern / Usage](../govern/metrics.md) dashboards.

---

## AI query stream

```
POST /api/skills/ai-query/stream
Content-Type: application/json
```

Streams the result of a natural-language query against an integration provider (used by the `sx` AI-query subcommands).

Request:

```json
{
  "query": "Find open PRs blocked on review",
  "provider": "GITHUB",
  "context": {
    "repo_url":   "https://github.com/owner/repo",
    "branch":     "main",
    "commit_sha": "abc1234..."
  }
}
```

* `provider` is one of the configured integration providers — `GITHUB`, `CIRCLECI`, `LINEAR`, etc.
* `context.repo_url` is required. `branch` and `commit_sha` may be empty strings.

Returns `Content-Type: text/event-stream`. Each event is a serialized tool call, intermediate result, or — as the final frame — `{"type": "done", "result": {...}}`. Errors arrive as `{"type": "error", "error": "..."}`.

---

## A complete `sx`-style flow

The typical machine flow when an agent comes online (and roughly what `sx install` does):

```bash
TOKEN="YOUR_BOT_API_KEY"
BASE="https://app.skills.new"

# 1. Resolve the asset set for this caller.
LOCK=$(curl -s "$BASE/api/skills/sx.lock" -H "Authorization: Bearer $TOKEN")

# 2. For each asset in the lock, download its bundle. (Pseudo-loop.)
for asset in $(echo "$LOCK" | parse-lock); do
  name="$(echo "$asset" | jq -r .name)"
  ver="$(echo  "$asset" | jq -r .version)"
  curl -s -O "$BASE/api/skills/assets/$name/$ver/$name-$ver.zip" \
       -H "Authorization: Bearer $TOKEN"
done

# 3. Periodically report what was invoked.
curl -s "$BASE/api/skills/usage" \
  -H "Authorization: Bearer $TOKEN" \
  --data-binary @- <<'JSONL'
{"asset_name": "my-skill", "asset_version": "3", "asset_type": "skill"}
JSONL
```

In practice, prefer running `sx` itself with a bot's API key — it implements the caching, retry, and on-disk layout correctly.
