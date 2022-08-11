# Sleuth API

‌The Sleuth REST API provides methods that enables users to:‌

* Register their deploys
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

For Organizations with many [Projects](../modeling-your-deployments/projects/), [Code Deployments](../modeling-your-deployments/code-deployments/) and [Impact Sources](../integrations-1/impact-sources/) configuring Sleuth via the UI can be cumbersome. The Sleuth API can be used to provision resources directly. However, many teams already rely on [Terraform](https://www.terraform.io/) to provision their infrastructure and other resources.&#x20;

Instead of using the API directly to provision Sleuth resources, you can use Terraform and our [terraform provider](https://registry.terraform.io/providers/sleuth-io/sleuth/latest).

## Organization and Deployment Slugs‌

Note that the organization and deployment slugs are not the semantic name of your organization and deployment as shown in the organization settings, which can contain spaces and capitalized characters.

The slugs displayed are the URL of your organization and deployment, with spaces replaced by a hyphen (-) and non-alphabetical characters (e.g., ()@#$%^, etc.) ignored.For example, if you're viewing a deployment called plugin picker (dev) and your organization is called Amazing Software, the URL will display as [https://app.sleuth.io/amazing-software/deployments/plugin-picker-dev](https://app.sleuth.io/amazing-software/deployments/plugin-picker-dev). Thus, the organization slug is amazing-software, the deployment slug is plugin-picker-dev.

## Errors

* Codes in the `2xx` range indicate success
* Codes in the `4xx` range indicate incorrect or incomplete parameters
* Codes in the `5xx` range indicate an error with Sleuth servers

## REST API Details

{% swagger baseUrl="https://app.sleuth.io" path="/api/1/deployments/<Organization Slug>/<Deployment Slug>/register_deploy" method="post" summary="Deploy Registration" %}
{% swagger-description %}
Register your deploys via the Sleuth API.
{% endswagger-description %}

{% swagger-parameter in="path" name="Organization Slug" type="string" required="false" %}
Slug of the organization parent of the affected code deployment
{% endswagger-parameter %}

{% swagger-parameter in="path" name="Deployment Slug" type="string" required="false" %}
Slug of the code deployment
{% endswagger-parameter %}

{% swagger-parameter in="body" name="ignore_if_duplicate" type="string" required="false" %}
If the value is provided and set to "true" Sleuth won't return a 400 if we see a SHA that has already been registered
{% endswagger-parameter %}

{% swagger-parameter in="body" name="tags" type="string" required="false" %}
A comma-delimited list of tags. Defaults to tags calculated by matching paths defined in your .sleuth/TAGS file
{% endswagger-parameter %}

{% swagger-parameter in="body" name="environment" type="string" required="false" %}
String defining the environment to register the deploy against. If not provided Sleuth will use the default environment of the Project
{% endswagger-parameter %}

{% swagger-parameter in="body" name="email" type="string" required="false" %}
Email address of author
{% endswagger-parameter %}

{% swagger-parameter in="body" name="date" type="string" required="false" %}
ISO 8601 deployment date string
{% endswagger-parameter %}

{% swagger-parameter in="body" name="api_key" type="string" required="false" %}
Located in the

_Organization Settings > Details > Api Key_

field
{% endswagger-parameter %}

{% swagger-parameter in="body" name="sha" type="string" required="false" %}
The git SHA of the deployment, located in the deploy card of the deployment
{% endswagger-parameter %}

{% swagger-parameter in="body" name="links" type="string" %}
A key/value pair which is the link name and the link itself of the form:



mylink=http://my.link



If you need to send multiple then send a JSON body POST and this is a dictionary of values.
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
Success
```
{% endswagger-response %}

{% swagger-response status="400" description="Input date problem, including if SHA doesn" %}
```
String of message problem
```
{% endswagger-response %}

{% swagger-response status="401" description="API key not valid or the deployment is not in the specific organization" %}
```
String of message problem
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://app.sleuth.io" path="/api/1/deployments/<Organization Slug>/<Project Slug>/register_manual_deploy" method="post" summary="Manual Change" %}
{% swagger-description %}
Manual changes are those not tracked by source code, feature flags, or any other type of change not supported by Sleuth. They are a free-form entry that includes a name and description. Although the description is optional, the form data in the manual change must contain a name as one of its parameters.
{% endswagger-description %}

{% swagger-parameter in="path" name="Organization Slug" type="string" required="false" %}
Slug of the organization parent of the affected code deployment
{% endswagger-parameter %}

{% swagger-parameter in="path" name="Project Slug" type="string" required="false" %}
Slug of the project that you're registering a deploy to
{% endswagger-parameter %}

{% swagger-parameter in="body" name="api_key" type="string" required="false" %}
Located in the

_Organization Settings > Details > Api Key_

field
{% endswagger-parameter %}

{% swagger-parameter in="body" name="author" type="string" required="false" %}
Email address of author
{% endswagger-parameter %}

{% swagger-parameter in="body" name="description" type="string" required="false" %}
Description for the manual change
{% endswagger-parameter %}

{% swagger-parameter in="body" name="email" type="string" required="false" %}
Email address of the user associated with the project receiving the manual change
{% endswagger-parameter %}

{% swagger-parameter in="body" name="environment" type="string" required="false" %}
String defining the environment to register the change against
{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" type="string" required="true" %}
Title for the manual change
{% endswagger-parameter %}

{% swagger-parameter in="body" name="tags" type="string" required="false" %}
A comma-delimited list of tag
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
Success
```
{% endswagger-response %}

{% swagger-response status="400" description="Returned if the author or date are in the wrong format" %}
```
Invalid date format.  Must be in ISO 8601 format
```
{% endswagger-response %}

{% swagger-response status="401" description="Returned if the API key provided doesn" %}
```
Unauthorized
```
{% endswagger-response %}

{% swagger-response status="404" description="Returned if the project does not exist" %}
```
Project not found
```
{% endswagger-response %}

{% swagger-response status="422" description="Returned if name is not provided" %}
```
Name is required.
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://app.sleuth.io" path="/api/1/impact/<Impact ID>/register_impact" method="post" summary="Custom Impact Registration" %}
{% swagger-description %}
You can submit custom impact values to Sleuth. Sleuth will perform its anomaly detection on these values and they will inform the health of your deploys. Values can represent any metric that matters to you and must be represented via a float.
{% endswagger-description %}

{% swagger-parameter in="path" name="Impact ID" type="integer" required="false" %}
Uniquely identifies the Impact Source to register a value against
{% endswagger-parameter %}

{% swagger-parameter in="body" name="api_key" type="string" required="false" %}
Located in the

_Organization Settings -> Details -> API Key field_
{% endswagger-parameter %}

{% swagger-parameter in="body" name="date" type="string" required="false" %}
ISO 8601 date that indicates when the Impact value was collection. If not provided the date defaults to now
{% endswagger-parameter %}

{% swagger-parameter in="body" name="value" type="number" required="false" %}
Float value that is the metric Sleuth will collect
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
Success
```
{% endswagger-response %}

{% swagger-response status="400" description="Returned if the value or date are malformed" %}
```
Bad Request - impact value must be a number
```
{% endswagger-response %}

{% swagger-response status="401" description="Returned if the API key provided doesn" %}
```
Unauthorized
```
{% endswagger-response %}

{% swagger-response status="404" description="Returned if the Impact ID doesn" %}
```
MetricImpactSource <Impact ID> Not Found
```
{% endswagger-response %}

{% swagger-response status="429" description="Returned if your requests are more frequent than one every 120 seconds. A `Retry-After` header is provided with the number of seconds you should wait until you try again" %}
```
You may only register a custom metric once every 120 seconds
```
{% endswagger-response %}
{% endswagger %}
