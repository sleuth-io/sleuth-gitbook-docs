---
description: Example GraphQL mutations with authentication.
---

# GraphQL Mutations

To get started, login into Sleuth and open [GraphiQL](https://app.sleuth.io/graphql).

#### Create new Code Deployment

{% tabs %}
{% tab title="Mutation Example" %}
{% code overflow="wrap" lineNumbers="true" %}
```graphql
mutation CreateCodeDeployment($input: CreateCodeChangeSourceMutationInput!) {
  createCodeChangeSource(input: $input) {
    changeSource {
      name
      slug
      repository {
        provider
        owner
        name
        url
      }
      notifyInSlack
      includeInDashboard   
    }
  }
}
```
{% endcode %}
{% endtab %}

{% tab title="Variables (with webhooks)" %}
{% code overflow="wrap" lineNumbers="true" %}
```json
{
  "input": {
    "projectSlug": "<test-project>",
    "repository": {
      "name": "<repo-name>",
      "owner": "<repo-owner>",
      "url": "https://gitlab.com/<repo-owner>/<repo-name>",
      "provider": "GITLAB"
    },
    "name": "Test Code Deployment",
    "deployTrackingType": "MANUAL",
    "environmentMappings": {
      "environmentSlug": "production",
      "branch": "main"
    },
    "environmentMappings": {
      "environmentSlug": "staging",
      "branch": "main"
    }
  }
}
```
{% endcode %}

{% hint style="info" %}
Supported values for the **provider** field are **AZURE**, **BITBUCKET**, **CUSTOM\_GIT**, **GITHUB**, **GITHUB\_ENTERPRISE**, or **GITLAB**.
{% endhint %}
{% endtab %}

{% tab title="Variables (with build tracking)" %}
{% code overflow="wrap" lineNumbers="true" %}
```json
{
  "input": {
    "projectSlug": "<test-project>",
    "repository": {
      "name": "<repo-name>",
      "owner": "<repo-owner>",
      "url": "https://gitlab.com/<repo-owner>/<repo-name>",
      "provider": "GITLAB"
    },
    "name": "Test Code Deployment",
    "deployTrackingType": "BUILD",
    "environmentMappings": {
      "environmentSlug": "production",
      "branch": "main"
    },
    "environmentMappings": {
      "environmentSlug": "staging",
      "branch": "main"
    },
    "
  }
}
```
{% endcode %}

{% hint style="info" %}
Supported values for the **provider** field are **AZURE**, **BITBUCKET**, **CUSTOM\_GIT**, **GITHUB**, **GITHUB\_ENTERPRISE**, or **GITLAB**.
{% endhint %}
{% endtab %}
{% endtabs %}
