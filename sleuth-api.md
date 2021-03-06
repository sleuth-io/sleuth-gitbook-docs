# Sleuth API

‌The Sleuth REST API provides methods that enables users to:‌

* Register their deploys
* Create [manual changes](modeling-your-deployments/manual-changes.md)
* Register [custom impact values](integrations-1/impact-sources/metrics/custom.md)

Sleuth's main public API is built using GraphQL. It's the same API we use internally for developing our applications.

If you're new to GraphQL, Apollo has [resources for beginners](https://blog.apollographql.com/the-basics-of-graphql-in-5-links-9e1dc4cac055). [The official documentation](https://graphql.org/) is another good starting point.

{% hint style="info" %}
NOTE: the GraphQL API is still under heavy development and is subject to change
{% endhint %}

Sleuth's GraphQL endpoint is:

```text
https://app.sleuth.io/graphql
```

We expose the [GraphiQL](https://github.com/graphql/graphiql) client so you can explore and query the API.

## ‌Authentication‌

The Sleuth REST API requires authentication using the API key from your Sleuth [organization](settings/organization/details.md).

## Organization and Deployment Slugs‌

Note that the organization and deployment slugs are not the semantic name of your organization and deployment as shown in the organization settings, which can contain spaces and capitalized characters.

The slugs displayed are the URL of your organization and deployment, with spaces replaced by a hyphen \(-\) and non-alphabetical characters \(e.g., \(\)@\#$%^, etc.\) ignored.For example, if you're viewing a deployment called plugin picker \(dev\) and your organization is called Amazing Software, the URL will display as [https://app.sleuth.io/amazing-software/deployments/plugin-picker-dev](https://app.sleuth.io/amazing-software/deployments/plugin-picker-dev). Thus, the organization slug is amazing-software, the deployment slug is plugin-picker-dev.

## Errors

* Codes in the `2xx` range indicate success
* Codes in the `4xx` range indicate incorrect or incomplete parameters
* Codes in the `5xx` range indicate an error with Sleuth servers

## REST API Details

{% api-method method="post" host="https://app.sleuth.io" path="/api/1/<Organization Slug>/<Deployment Slug>/register\_deploy" %}
{% api-method-summary %}
Deploy Registration
{% endapi-method-summary %}

{% api-method-description %}
Register your deploys via the Sleuth API. 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="Organization Slug" type="string" required=true %}
Slug of the organization parent of the affected code deployment
{% endapi-method-parameter %}

{% api-method-parameter name="Deployment Slug" type="string" required=true %}
Slug of the code deployment
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="ignore\_if\_duplicate" type="string" required=false %}
If the value is provided and set to "true" Sleuth won't return a 400 if we see a SHA that has already been registered
{% endapi-method-parameter %}

{% api-method-parameter name="tags" type="string" required=false %}
A comma-delimited list of tags. Defaults to tags calculated by matching paths defined in your .sleuth/TAGS file
{% endapi-method-parameter %}

{% api-method-parameter name="environment" type="string" required=false %}
String defining the environment to register the deploy against. If not provided Sleuth will use the default environment of the Project
{% endapi-method-parameter %}

{% api-method-parameter name="email" type="string" required=false %}
Email address of author
{% endapi-method-parameter %}

{% api-method-parameter name="date" type="string" required=false %}
ISO 8601 deployment date string
{% endapi-method-parameter %}

{% api-method-parameter name="api\_key" type="string" required=true %}
Located in the _Organization Settings &gt; Details &gt; Api Key_ field
{% endapi-method-parameter %}

{% api-method-parameter name="sha" type="string" required=true %}
The git SHA of the deployment, located in the deploy card of the deployment
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
Success
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Input date problem, including if SHA doesn't exist or has already been reported.
{% endapi-method-response-example-description %}

```text
String of message problem
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
API key not valid or the deployment is not in the specific organization
{% endapi-method-response-example-description %}

```text
String of message problem
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://app.sleuth.io" path="/api/1/deployments/<Organization Slug>/<Project Slug>/register\_manual\_deploy" %}
{% api-method-summary %}
Manual Change
{% endapi-method-summary %}

{% api-method-description %}
Manual changes are those not tracked by source code, feature flags, or any other type of change not supported by Sleuth. They are a free-form entry that includes a name and description. Although the description is optional, the form data in the manual change must contain a name as one of its parameters.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="Organization Slug" type="string" required=true %}
Slug of the organization parent of the affected code deployment
{% endapi-method-parameter %}

{% api-method-parameter name="Project Slug" type="string" required=true %}
Slug of the project that you're registering a deploy to
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="tags" type="string" required=false %}
A comma-delimited list of tag
{% endapi-method-parameter %}

{% api-method-parameter name="api\_key" type="string" required=true %}
Located in the _Organization Settings &gt; Details &gt; Api Key_ field
{% endapi-method-parameter %}

{% api-method-parameter name="email" type="string" required=false %}
Email address of the user associated with the project receiving the manual change
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
Title for the manual change
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}
Description for the manual change
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Success
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Returned if the author or date are in the wrong format
{% endapi-method-response-example-description %}

```
Invalid date format.  Must be in ISO 8601 format
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
Returned if the API key provided doesn't allow access to the deployment
{% endapi-method-response-example-description %}

```
Unauthorized
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Returned if the project isn't found
{% endapi-method-response-example-description %}

```
Project not found
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Name is required.
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://app.sleuth.io" path="/api/1/impact/<Impact ID>/register\_impact" %}
{% api-method-summary %}
Custom Impact Registration
{% endapi-method-summary %}

{% api-method-description %}
You can submit custom impact values to Sleuth. Sleuth will perform its anomaly detection on these values and they will inform the health of your deploys. Values can represent any metric that matters to you and must be represented via a float.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="Impact ID" type="integer" required=false %}
Uniquely identifies the Impact Source to register a value against
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="api\_key" type="string" required=true %}
Located in the _Organization Settings -&gt; Details -&gt; API Key field_
{% endapi-method-parameter %}

{% api-method-parameter name="date" type="string" required=false %}
ISO 8601 date that indicates when the Impact value was collection. If not provided the date defaults to now
{% endapi-method-parameter %}

{% api-method-parameter name="value" type="number" required=true %}
Float value that is the metric Sleuth will collect
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Success
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Returned if the value or date are malformed
{% endapi-method-response-example-description %}

```
Bad Request - impact value must be a number
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
Returned if the API key provided doesn't allow you to access the Impact source
{% endapi-method-response-example-description %}

```
Unauthorized
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Returned if the Impact ID doesn't exist
{% endapi-method-response-example-description %}

```
MetricImpactSource <Impact ID> Not Found
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=429 %}
{% api-method-response-example-description %}
Returned if your requests are more frequent than one every 120 seconds. A \`Retry-After\` header is provided with the number of seconds you should wait until you try again
{% endapi-method-response-example-description %}

```
You may only register a custom metric once every 120 seconds
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

