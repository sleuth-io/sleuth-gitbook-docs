---
description: Example GraphQL queries with authentication.
---

# GraphQL Queries

### GraphiQL

To get started, login into Sleuth and open [GraphiQL](https://app.sleuth.io/graphql)

#### Logged in user ([example link](https://app.sleuth.io/graphql#query=%7B%0A%20%20user%20%7B%0A%20%20%20%20display%0A%20%20%7D%0A%7D))

{% code title="GraphQL Query" overflow="wrap" lineNumbers="true" %}
```graphql
{
  user {
    display
  }
}
```
{% endcode %}

#### Team metrics recap ([example link](https://app.sleuth.io/graphql#query=query%20GetNumberOfTeamDeploys\(%24orgSlug%3A%20ID!%2C%20%24start%3A%20DateTime!%2C%20%24end%3A%20DateTime!%2C%20%24teamSlugs%3A%20%5BID%5D\)%20%7B%0A%20%20organization\(orgSlug%3A%20%24orgSlug\)%20%7B%0A%20%20%20%20metricsRecap\(start%3A%20%24start%2C%20end%3A%20%24end%2C%20filters%3A%20%7BteamSlugs%3A%20%24teamSlugs%7D\)%20%7B%0A%20%20%20%20%20%20numOfDeploys%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%0A\&operationName=GetNumberOfTeamDeploys\&variables=%7B%0A%20%20%22orgSlug%22%3A%20%22sleuth%22%2C%0A%20%20%22start%22%3A%20%222022-07-01T00%3A00%3A00Z%22%2C%0A%20%20%22end%22%3A%20%222022-07-31T00%3A00%3A00Z%22%2C%0A%20%20%22teamSlugs%22%3A%20%5B%0A%20%20%20%20%22frontend-2%22%0A%20%20%5D%0A%7D))

{% tabs %}
{% tab title="GraphQL Query" %}
{% code overflow="wrap" lineNumbers="true" %}
```graphql
query GetNumberOfTeamDeploys($orgSlug: ID!, $start: DateTime!, $end: DateTime!, $teamSlugs: [ID]) {
  organization(orgSlug: $orgSlug) {
    metricsRecap(start: $start, end: $end, filters: {teamSlugs: $teamSlugs}) {
      numOfDeploys
    }
  }
}
```
{% endcode %}
{% endtab %}

{% tab title="Query Variables (JSON)" %}
{% code overflow="wrap" lineNumbers="true" %}
```json
{
  "orgSlug": "sleuth",
  "start": "2022-07-01T00:00:00Z",
  "end": "2022-07-31T00:00:00Z",
  "teamSlugs": [
    "frontend-2"
  ]
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

#### Project metrics recap ([example link](https://app.sleuth.io/graphql#query=query%20GetNumberOfProjectDeploys\(%24orgSlug%3A%20ID!%2C%20%24start%3A%20DateTime!%2C%20%24end%3A%20DateTime!%2C%20%24projectSlugs%3A%20%5BID%5D\)%20%7B%0A%20%20organization\(orgSlug%3A%20%24orgSlug\)%20%7B%0A%20%20%20%20metricsRecap\(start%3A%20%24start%2C%20end%3A%20%24end%2C%20filters%3A%20%7BprojectSlugs%3A%20%24projectSlugs%7D\)%20%7B%0A%20%20%20%20%20%20numOfDeploys%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%0A\&operationName=GetNumberOfProjectDeploys\&variables=%7B%0A%20%20%22orgSlug%22%3A%20%22sleuth%22%2C%0A%20%20%22start%22%3A%20%222022-07-01T00%3A00%3A00Z%22%2C%0A%20%20%22end%22%3A%20%222022-07-31T00%3A00%3A00Z%22%2C%0A%20%20%22projectSlugs%22%3A%20%5B%0A%20%20%20%20%22sleuth%22%0A%20%20%5D%0A%7D))

{% tabs %}
{% tab title="GraphQL Query" %}
{% code overflow="wrap" lineNumbers="true" %}
```graphql
query GetNumberOfProjectDeploys($orgSlug: ID!, $start: DateTime!, $end: DateTime!, $projectSlugs: [ID]) {
  organization(orgSlug: $orgSlug) {
    metricsRecap(start: $start, end: $end, filters: {projectSlugs: $projectSlugs}) {
      numOfDeploys
    }
  }
}
```
{% endcode %}
{% endtab %}

{% tab title="Query Variables (JSON)" %}
{% code overflow="wrap" lineNumbers="true" %}
```json
{
  "orgSlug": "sleuth",
  "start": "2022-07-01T00:00:00Z",
  "end": "2022-07-31T00:00:00Z",
  "projectSlugs": [
    "sleuth"
  ]
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

### cURL and API key

{% hint style="info" %}
Using cURL you can call Sleuth GraphQL API from any environment.
{% endhint %}

#### Get API Key through GraphiQL ([example link](https://app.sleuth.io/graphql#query=%7B%0A%20%20context%20%7B%0A%20%20%20%20org%20%7B%0A%20%20%20%20%20%20apiKey%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D\&variables=))

{% code title="GraphQL Query" overflow="wrap" lineNumbers="true" %}
```graphql
{
  context {
    org {
      apiKey
    }
  }
}
```
{% endcode %}

Now use API Key in `authorization` header (required headers are `content-type` and `authorization`)

{% code title="" overflow="wrap" lineNumbers="true" %}
```bash
curl 'https://app.sleuth.io/graphql' \
  -H 'content-type: application/json' \
  -H 'authorization: apikey <PASTE-YOUR-API-KEY-HERE>' \
  -d '{"query":"query{organization(orgSlug:\"sleuth\"){metricsRecap(start:\"2022-07-01T00:00:00Z\",end:\"2022-07-31T00:00:00Z\",filters:{teamSlugs:\"frontend-2\"}){numOfDeploys}}}"}'
```
{% endcode %}

{% hint style="danger" %}
Authorization header starts with **apikey** and not **Bearer**!
{% endhint %}
