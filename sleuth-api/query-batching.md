# Query batching

Sleuth GQL API supports batching, which allows you to execute multiple queries in a single request. To use it, you need to make two small changes to your requests: use a different API URL and wrap the payload in a list.

The two examples below demonstrate the same query being requested individually or in a batch.&#x20;

### Individual query

#### URL

`https://app.sleuth.io/graphql`&#x20;

#### Request body

```json
{
  "query": "{ organization(orgSlug: \"sleuth\") { name } }",
  "variables": null
}
```

### Batched query

#### URL

`https://app.sleuth.io/graphql-batch`&#x20;

#### Request body

```json
[
  {
    "query": "{ organization(orgSlug: \"sleuth\") { name } }",
    "variables": null
  }
]
```

{% hint style="info" %}
When batching queries, the server response will match the request and return a list of objects instead of a single object.
{% endhint %}
