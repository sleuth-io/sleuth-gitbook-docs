---
description: >-
  The GraphQL API at app.skills.new/graphql is the management surface used by
  the web UI — assets, bots, profiles, installations, change requests, audit
  log, and AI metrics.
---

# GraphQL API

The GraphQL API is the **management surface** for Sleuth Skills. It's the same API the web UI uses, which means anything you can do in the UI you can also script — create bots, issue API keys, install assets to teams, browse the audit log, query AI metrics, approve change requests, and so on.

For the **asset-distribution** side (lock-file resolution, bundle downloads, usage reporting) use the [REST API](rest.md) instead. The REST surface is what `sx` and CI agents call; GraphQL is for control-plane operations.

## Endpoints

| Path | Purpose |
|------|---------|
| `https://app.skills.new/graphql` | Main GraphQL endpoint. Serves [GraphiQL](https://github.com/graphql/graphiql) when opened in a browser. |
| `https://app.skills.new/graphql/batch` | Same schema, accepts an array of operations to run as a single batched request. |

The endpoint is **introspectable** — open it in a signed-in browser tab to explore the full schema interactively in GraphiQL. The schema is large; the sections below give you orientation, but GraphiQL is the source of truth.

## Authentication

GraphQL accepts the same credentials as REST — see [Authentication](authentication.md). Set the `Authorization` header:

```bash
# Bot API key (CI / unattended) or personal access token (acts as you)
curl https://app.skills.new/graphql \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"query": "{ user { display } }"}'
```

In GraphiQL the session cookie is used automatically. For automation use a bot API key; for personal scripts use a [personal access token](authentication.md#personal-access-tokens).

## What's in the schema

The schema covers the full Skills.new feature set. The top-level `Query` and `Mutation` fields relevant to Skills are below — for everything else (DORA metrics, deployments, dashboards, etc.) see GraphiQL or the [DORA GraphQL docs](../../sleuth-api/graphql-examples.md).

### Vault — the asset catalog

```graphql
type Query {
  vault: Vault!
  asset(id: ID!): VaultAsset
  installedAssets(
    userId: ID
    botId: ID
    repositoryId: ID
    assetType: String
    term: String
  ): InstalledAssetsResponse!
  catalogSources(assetType: String): [CatalogSource!]!
  catalogEntries(source: String!, search: String, limit: Int, offset: Int): [CatalogEntry!]
}
```

`vault` is the entry point for every asset in your org. `asset(id:)` looks one up by GID. `installedAssets` resolves the assets that should be on disk for a specific user, bot, or repository — it's the GraphQL equivalent of the REST lock file, returning structured data instead of TOML.

### Asset management

```graphql
type Mutation {
  createAsset(input: CreateAssetInput!): CreateAssetMutation
  updateAsset(input: UpdateAssetInput!): UpdateAssetMutation
  deleteAsset(id: ID!): DeleteAssetMutation
  toggleAssetStatus(id: ID!): ToggleAssetStatusMutation
  activateSkillVersion(assetId: ID!, versionNumber: Int!): ActivateSkillVersionMutation
  renameAsset(input: RenameAssetInput!): RenameAssetMutation
  refreshGitAsset(assetId: ID!): RefreshGitAssetMutation
}
```

### Installation targeting

```graphql
type Mutation {
  setAssetInstallations(input: SetAssetInstallationsInput!): SetAssetInstallationsMutation
  removeAssetInstallations(input: RemoveAssetInstallationsInput!): RemoveAssetInstallationsMutation
  importFromCatalog(source: String!, key: String!, installations: String): ImportFromCatalogMutation
  importAssetAsManaged(assetId: ID!): ImportAssetAsManagedMutation
}
```

`SetAssetInstallationsInput` takes a list of `(entity_type, entity_id)` pairs — `organization`, `team`, `repository`, `user`, or `bot` — so you can pin an asset to a specific distribution target.

### Bots and bot API keys

```graphql
type Query {
  bots: [ManagedBot!]
  bot(slug: String, id: ID): ManagedBot!
}

type Mutation {
  createBot(input: CreateBotInput!): CreateBotMutation
  updateBot(input: UpdateBotInput!): UpdateBotMutation
  deleteBot(id: ID!): DeleteBotMutation
  createBotApiKey(botId: ID!, label: String): CreateBotApiKeyMutation
  deleteBotApiKey(keyId: ID!): DeleteBotApiKeyMutation
  installSkillToBot(botId: ID!, skillId: ID!): InstallSkillToBotMutation
  uninstallSkillFromBot(botId: ID!, skillId: ID!): UninstallSkillFromBotMutation
}
```

`ManagedBot` exposes the bot's slug, teams, installed skills, and `apiKeys: [BotApiKey!]`. Each `BotApiKey` exposes `id`, `label`, `maskedToken` (e.g. `abc12345...wxyz`), and `createdAt`. The raw token is only returned by `createBotApiKey` and only at creation time — copy it then or lose it.

### Pull requests and change requests

```graphql
type Query {
  assetPullRequest(id: ID!): SkillPullRequest!
  assetPullRequests(
    assetId: ID
    status: SkillPullRequestStatusEnum
    creationType: SkillPullRequestCreationTypeEnum
    search: String
  ): SkillPullRequestConnection!
  changeRequests(
    status: ChangeRequestStatusEnum
    changeType: ChangeRequestTypeEnum
    search: String
  ): ChangeRequestConnection!
  installationRequests(status: String): [AssetInstallationRequest!]!
}

type Mutation {
  createAssetPullRequest(input: CreateAssetPullRequestInput!): CreateAssetPullRequestMutation
  addAssetPullRequestFileChange(input: AddAssetPullRequestFileChangeInput!): AddAssetPullRequestFileChangeMutation
  mergeAssetPullRequest(pullRequestId: ID!): MergeAssetPullRequestMutation
  closeAssetPullRequest(pullRequestId: ID!): CloseAssetPullRequestMutation
  createInstallationRequest(input: CreateInstallationRequestInput!): CreateInstallationRequestMutation
  approveInstallationRequest(input: ReviewInstallationRequestInput!): ApproveInstallationRequestMutation
  rejectInstallationRequest(input: ReviewInstallationRequestInput!): RejectInstallationRequestMutation
}
```

### Profiles

```graphql
type Query {
  profiles(name: String, first: Int, after: String): VaultAssetProfileConnection!
  profile(id: ID!): VaultAssetProfile
}

type Mutation {
  createAssetProfile(input: CreateAssetProfileInput!): CreateAssetProfileMutation
  updateAssetProfile(input: UpdateAssetProfileInput!): UpdateAssetProfileMutation
  deleteAssetProfile(input: DeleteAssetProfileInput!): DeleteAssetProfileMutation
  addAssetsToProfile(input: ModifyAssetProfileAssetsInput!): AddAssetsToProfileMutation
  removeAssetsFromProfile(input: ModifyAssetProfileAssetsInput!): RemoveAssetsFromProfileMutation
  setActiveSkillProfile(skillProfileId: ID): SetActiveSkillProfileMutation
}
```

### Audit log and metrics

```graphql
type Query {
  assetAuditLog(
    search: String
    assetTypes: [AssetType!]
    events: [AssetEventType!]
    targetId: ID
    actorId: Int
    dateFrom: DateTime
    dateTo: DateTime
    actorType: String      # "user", "bot", "system"
  ): AssetAuditEventConnection!
}
```

Filter by actor, event type, target, or date range — this is what powers the **Govern → Audit log** page.

### Personal access tokens

```graphql
type User {
  personalTokens(first: Int, after: String): AccessTokenConnection!
}

type Mutation {
  createPersonalToken(label: String!): CreatePersonalTokenMutation
  deletePersonalToken(tokenId: ID!): DeletePersonalTokenMutation
}
```

`createPersonalToken` returns the raw token **once**, in the `token` field of the response — copy it then or lose it. Subsequent reads of `user.personalTokens` return a camouflaged value for identification only. See [Authentication](authentication.md#personal-access-tokens) for the full flow.

## Example: create a bot and issue a key

```graphql
mutation CreateBotWithKey($name: String!, $teamIds: [ID!]) {
  createBot(input: {name: $name, teamIds: $teamIds}) {
    bot {
      id
      slug
      teams { name }
    }
    rawToken            # API key for the auto-created "Default key"
  }
}
```

```json
{
  "name": "CI worker (prod)",
  "teamIds": ["TM...", "TM..."]
}
```

`rawToken` is the bot's first API key — store it immediately. Issue additional keys with `createBotApiKey(botId:, label:)`.

## Example: list a bot's installed assets

```graphql
{
  bot(slug: "ci-worker-prod") {
    name
    teamMemberships { team { name } assetCount }
    installedSkills {
      slug
      assetType
      description
      usageCount
    }
    apiKeys {
      maskedToken
      label
      createdAt
    }
  }
}
```

## Batching

Send multiple operations in one round-trip via `/graphql/batch`. The body is a JSON array of `{query, variables, operationName}` objects, and the response is an array of results in the same order. See [Query batching](../../sleuth-api/query-batching.md) — the mechanics are identical to the DORA endpoint.

## Errors

GraphQL errors are returned in the standard `errors` array of the response body, even on `200 OK`. Authentication failures return `401` at the HTTP level; permission failures (e.g. a bot key trying to mutate org settings) return a GraphQL error with a `PermissionDenied` message inside a `200 OK`.
