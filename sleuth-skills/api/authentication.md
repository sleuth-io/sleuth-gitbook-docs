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
| **Org API key** (legacy) | `Authorization: apikey <token>` | An org-level admin principal. | Legacy integrations migrating from the DORA API key. New integrations should use a bot. |
| **User session / OAuth** | Browser session cookie, or `Authorization: Bearer <user-token>` | The signed-in user, with their RBAC role. | The web UI and `sx` running on a developer's laptop. |

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

## Org API keys (legacy)

Each organization has a single legacy org-level API key, the same one used by the Sleuth DORA API. It authenticates as an admin principal for the org. To use it on Skills.new:

```bash
curl https://app.skills.new/graphql \
  -H "Authorization: apikey YOUR_ORG_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"query": "{ vault { assets(first: 5) { nodes { name } } } }"}'
```

{% hint style="info" %}
Note the scheme is **`apikey`**, not **`Bearer`**, for this credential type.
{% endhint %}

For new integrations, prefer a bot API key. The org-level key is broader than most callers need, harder to rotate (there is only one), and the GraphQL `Organization.apiKey` field is deprecated in favor of [scoped access tokens](#scoped-access-tokens).

### Scoped access tokens

You can also issue **org-level scoped access tokens** via the web UI or GraphQL. These behave like the legacy API key but are individually labeled, rotatable, and scoped:

* **`ALL`** — full admin access for the org.
* **`REGISTER_DEPLOY`** — limited to registering deploys (DORA only, not used by Skills.new).

Create one in the web UI under **Settings → Organization → Access Tokens**, or with the `createAccessToken` GraphQL mutation. Pass it the same way as a bot key, with the `Bearer` scheme:

```bash
curl https://app.skills.new/api/skills/sx.lock \
  -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
```

When the token's scope is `ALL` and it isn't tied to a bot, the API treats it as the org-level admin principal.

## User credentials

When `sx` runs on a developer's laptop, it authenticates as **that user** — so `sx.lock` returns the assets installed to the user, the user's teams, and the user's repositories. You typically don't construct user credentials by hand; they are issued by the [`sx login`](https://github.com/sleuth-io/sx) flow.

In the browser, the web UI authenticates via session cookie. GraphiQL inherits that cookie automatically, so once you're signed in at [skills.new](https://skills.new) you can explore the API at [https://app.skills.new/graphql](https://app.skills.new/graphql) without any extra setup.

## Picking the right credential

* **Building a CI integration?** Create a bot in the UI, add it to the teams whose assets it needs, issue one API key per CI environment.
* **Building a one-off admin script?** Use an org-level scoped access token labeled for the script. Delete the token when the script is retired.
* **Writing a developer tool that runs as the user?** Use the `sx` login flow rather than asking users to paste tokens.
* **Migrating from the DORA org API key?** Issue a new scoped access token, use it with the `Bearer` scheme on `app.skills.new`, and leave the DORA key untouched.
