---
description: >-
  Every Skills.new API call is authenticated and scoped to a single
  organization. The credential you pass determines whether the caller acts as
  a user, an org-level service account, or a bot.
---

# Authentication

Every call to `https://app.skills.new` is authenticated. There is no public/anonymous surface — even the lock-file lookup requires an authenticated principal so it can resolve which assets that principal should receive.

Skills.new accepts three credential types:

| Credential | Header | Acts as | Best for |
|------------|--------|---------|----------|
| **Bot API key** | `Authorization: Bearer <token>` | A specific [bot](../distribute/bots.md) — inherits the assets installed to the bot's teams and direct installs. | Unattended automation: CI runs, scheduled loops, review workers. |
| **Personal access token** | `Authorization: Bearer <token>` | The user that created the token, with their RBAC role. | Personal scripts, GraphQL exploration, and CLI tools that should act _as you_. |
| **User session** | Browser session cookie | The signed-in user, with their RBAC role. | The web UI and GraphiQL. |

## Bot API keys (recommended)

Bots are first-class principals in Skills.new. A bot can join teams, have assets installed against it, and authenticate via one or more API keys. This is the credential type you want for any non-human caller — CI agents, scheduled loops, review bots, the `sx` running on a build worker.

### Issuing a key

In the web UI, open the bot's detail page and click the **API Keys** tab. Choose **Create**, give the key a label (e.g. `ci-worker-prod`), and copy the token. **The full token is only shown once at creation time** — afterward, the UI only displays the prefix and suffix for identification.

You can also create a key over GraphQL (you must be a user with admin permissions, not a bot):

```graphql
mutation CreateKey($botId: ID!, $label: String) {
  createBotApiKey(botId: $botId, label: $label) {
    rawToken          # shown ONCE — copy immediately into a secret manager
    apiKey {
      id
      label
      maskedToken     # e.g. "abc12345...wxyz" for later identification
      createdAt
    }
  }
}
```

The raw token is an [OAuth2 access token](https://datatracker.ietf.org/doc/html/rfc6749#section-1.4) with the `ALL` scope, valid for 20 years. Each bot can hold multiple keys so you can rotate without downtime — issue a new key, redeploy CI to use it, then delete the old one.

### Passing a key

Send the token in the `Authorization` header with the `Bearer` scheme:

```bash
curl https://app.skills.new/api/skills/sx.lock \
  -H "Authorization: Bearer YOUR_BOT_API_KEY"
```

For GraphQL:

```bash
curl https://app.skills.new/graphql \
  -H "Authorization: Bearer YOUR_BOT_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"query": "{ bot(slug: \"my-bot\") { name installedSkills { slug } } }"}'
```

When the server authenticates a bot key, it sets both the bot context and the org context on the request — so calls like `/api/skills/sx.lock` return the lock file scoped to **that bot's** teams and direct installs, not a user's.

### Revoking a key

Open the bot's **API Keys** tab and click **Delete** on the row, or call the GraphQL mutation:

```graphql
mutation { deleteBotApiKey(keyId: "BK...") { ok } }
```

Revocation is immediate — in-flight requests using that key will fail on next call. Deleting the bot itself revokes all of its keys.

{% hint style="warning" %}
**Never share a bot key across bots.** Each bot's keys grant access to that bot's installed asset set. If two CI workers need different asset sets, give them different bots; if they need the same set, put them on the same teams and give each its own key.
{% endhint %}

## Personal access tokens

A **personal access token** (PAT) is an OAuth2 token tied to your individual user account, scoped to a single organization. Use one when you want a script or CLI tool to act _as you_ — it inherits your RBAC role and your asset installs. PATs are the recommended credential for ad-hoc GraphQL queries, personal automation, and anywhere you'd otherwise be tempted to copy a session cookie.

### Issuing a PAT

In the web UI, open the user settings (top-right avatar) and choose **Personal Access Tokens**. Click **Add access token**, give the token a descriptive name (e.g. `local-graphiql`, `home-laptop-sx`), and **copy the value when it's shown** — the full token is only displayed once at creation time. Afterward, the table shows an obfuscated value (`••••••••…`) for identification.

You can also create one over GraphQL while signed in:

```graphql
mutation CreatePAT($label: String!) {
  createPersonalToken(label: $label) {
    token            # the raw token — returned ONCE
    errors
  }
}
```

```graphql
{
  user {
    personalTokens(first: 50) {
      edges { node { id label token created expires applicationName } }
    }
  }
}
```

The `token` field on the listing is camouflaged; only the response of `createPersonalToken` returns the raw value.

### Passing a PAT

PATs use the standard `Bearer` scheme:

```bash
curl https://app.skills.new/graphql \
  -H "Authorization: Bearer YOUR_PERSONAL_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"query": "{ user { display } vault { assets(first: 5) { nodes { name } } } }"}'
```

They work the same way on REST:

```bash
curl https://app.skills.new/api/skills/sx.lock \
  -H "Authorization: Bearer YOUR_PERSONAL_TOKEN"
```

Because the token represents _you_, the response is scoped to _your_ installs — `sx.lock` returns the assets installed to you, your teams, and the repositories you have access to.

### PAT scope and lifetime

* **Scope** — a PAT acts with the issuing user's RBAC role in the org it was created in. It cannot escalate beyond what you can do in the web UI, and it cannot be used against a different org.
* **Lifetime** — 10 years. Rotate by issuing a new one and deleting the old one.
* **Revocation** — immediate when you click **Delete** in the settings UI (or call `deletePersonalToken(tokenId:)`).

### When to use a PAT vs a bot key

| Use a **PAT** when... | Use a **bot API key** when... |
|-----------------------|--------------------------------|
| The work runs interactively or under your account. | The work runs unattended in CI, a scheduled loop, or a review worker. |
| The assets should resolve to **your** team/repo membership. | The assets should resolve to a service account's team membership. |
| Revoking it shouldn't affect your colleagues. | Revoking it shouldn't affect any individual person. |
| You'd otherwise be copying a browser session cookie. | You'd otherwise be sharing a human's PAT across CI runners. |

{% hint style="warning" %}
**Don't share PATs across people or environments.** A PAT carries one user's permissions across one organization — treat it like a password. For shared automation, create a [bot](../distribute/bots.md) and use a bot key.
{% endhint %}

## User sessions

In the browser, the web UI authenticates via session cookie. GraphiQL at [https://app.skills.new/graphql](https://app.skills.new/graphql) inherits that cookie automatically, so once you're signed in at [skills.new](https://skills.new) you can explore the API interactively without setting any headers.

For programmatic access from a tool running on your behalf — including the [`sx`](https://github.com/sleuth-io/sx) CLI — use a [PAT](#personal-access-tokens). `sx login` walks you through obtaining one and storing it locally.

## Picking the right credential

* **Building a CI integration or unattended automation?** Create a [bot](../distribute/bots.md), add it to the teams whose assets it needs, issue one bot API key per environment.
* **Writing a personal script or exploring the API from cURL?** Issue a PAT from your user settings and delete it when the script is retired.
* **Running the `sx` CLI on your own machine?** Use `sx login` — it manages a PAT for you.
* **Just clicking around in GraphiQL?** Sign in at [skills.new](https://skills.new) and your session cookie is all you need.
