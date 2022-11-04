# Sleuth API

‌The Sleuth REST API provides methods that enables users to:‌

* Register or import their deploys
* Create [manual changes](../modeling-your-deployments/manual-changes.md)
* Register [custom impact values](../integrations-1/impact-sources/metrics/custom.md)

Sleuth's main public API is built using GraphQL. It's the same API we use internally for developing our applications.

If you're new to GraphQL, Apollo has [resources for beginners](https://blog.apollographql.com/the-basics-of-graphql-in-5-links-9e1dc4cac055). [The official documentation](https://graphql.org) is another good starting point.

{% hint style="info" %}
NOTE: the GraphQL API is still under heavy development and is subject to change
{% endhint %}

Sleuth's GraphQL endpoint is:

```
https://app.sleuth.io/graphql
```

We expose the [GraphiQL](https://github.com/graphql/graphiql) client so you can explore and query the API.

{% hint style="info" %}
See [GraphQL examples](graphql-examples.md) to see how to authenticate your requests using Sleuth API Key.
{% endhint %}

## ‌Authentication‌

The Sleuth REST API requires authentication using the API key from your Sleuth [organization](../settings/organization/details.md).

## Provisioning Sleuth with Terraform

For Organizations with many [Projects](../modeling-your-deployments/projects/), [Code Deployments](../modeling-your-deployments/code-deployments/) and [Impact Sources](../integrations-1/impact-sources/) configuring Sleuth via the UI can be cumbersome. The Sleuth API can be used to provision resources directly. However, many teams already rely on [Terraform](https://www.terraform.io/) to provision their infrastructure and other resources.

Instead of using the API directly to provision Sleuth resources, you can use Terraform and our [terraform provider](https://registry.terraform.io/providers/sleuth-io/sleuth/latest).

## Organization and Deployment Slugs‌

Note that the organization and deployment slugs are not the semantic name of your organization and deployment as shown in the organization settings, which can contain spaces and capitalized characters.

The slugs displayed are the URL of your organization and deployment, with spaces replaced by a hyphen (-) and non-alphabetical characters (e.g., ()@#$%^, etc.) ignored.For example, if you're viewing a deployment called plugin picker (dev) and your organization is called Amazing Software, the URL will display as [https://app.sleuth.io/amazing-software/deployments/plugin-picker-dev](https://app.sleuth.io/amazing-software/deployments/plugin-picker-dev). Thus, the organization slug is amazing-software, the deployment slug is plugin-picker-dev.

## Errors

* Codes in the `2xx` range indicate success
* Codes in the `4xx` range indicate incorrect or incomplete parameters
* Codes in the `5xx` range indicate an error with Sleuth servers

## REST API Details and Examples

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><ul><li><a href="deploy-registration.md">Deploy Registration</a></li><li><a href="deploy-import.md">Deploy Import</a></li></ul></td><td></td><td></td><td><a href="../.gitbook/assets/Code Deploys.png">Code Deploys.png</a></td></tr><tr><td><ul><li><a href="manual-change.md">Manual Changes</a></li></ul></td><td></td><td></td><td><a href="../.gitbook/assets/Manual Changes.png">Manual Changes.png</a></td></tr><tr><td><ul><li><a href="custom-incident-impact-registration.md">Custom Incident Impact Source</a></li><li><a href="custom-metric-impact-registration.md">Custom Metric Impact Source</a></li></ul></td><td></td><td></td><td><a href="../.gitbook/assets/Impact Sources.png">Impact Sources.png</a></td></tr></tbody></table>
