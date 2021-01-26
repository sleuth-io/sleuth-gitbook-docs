# Sleuth API

‌The Sleuth REST API provides methods that enables users to:‌

* Manually register their deploys
* Submit manual changes

## ‌Authentication‌

The Sleuth REST API requires authentication using the API key from your Sleuth [project](https://github.com/sleuth-io/sleuth-gitbook-docs/tree/dac6bb1d50bf6db9b82e70f093d6c196b818030a/@sleuth/s/sleuth/~/drafts/-M8WXrzvQ-fp5VsbiE8G/v/v3/projects/README.md).

## Errors

* Codes in the `2xx` range indicate success
* Codes in the `4xx` range indicate incorrect or incomplete parameters \(e.g., parameter  omitted, etc.\)
* Codes in the `5xx` range indicate an error with Sleuth servers

{% api-method method="post" host="https://app.sleuth.io" path="/api/1/<Organization Slug>/<Deployment Slug>/register\_deploy" %}
{% api-method-summary %}
Manual Deploy Registration
{% endapi-method-summary %}

{% api-method-description %}
Manually register your deploys via the Sleuth API.Note that the organization and deployment slugs are not the semantic name of your organization and deployment as shown in the organization settings, which can contain spaces and capitalized characters. The slugs displayed are the URL of your organization and deployment, with spaces replaced by a hyphen \(-\) and non-alphabetical characters \(e.g., **\(\)@\#$%^**, etc.\) ignored.For example, if you're viewing a deployment called **plugin picker \(dev\)** and your organization is called **Amazing Software**, the URL will display as https://app.sleuth.io/amazing-software/deployments/plugin-picker-dev. Thus, the organization slug is **amazing-software**, the deployment slug is **plugin-picker-dev**.
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
Manual changes are those not tracked by source code, feature flags, or any other type of change not supported by Sleuth. They are a free-form entry that includes a name and description. Although the description is optional, the form data in the manual change must contain a name as one of its parameters.Keep in mind that the organization and project slugs are not the semantic name of your organization and project as shown in your organization and project settings, which can contain spaces and capitalized characters. Rather, they're the slugs as displayed in the URL of your organization and project, with spaces replaced by a hyphen \(-\); non-alphabetical characters \(e.g., \(\)@\#$%^, etc.\) are ignored.For example, if you're viewing a project called **Software Selector** and your organization is called **Amazing Software**, the URL will display as https://app.sleuth.io/amazing-software/software-selector. The organization slug is **amazing-software**, the project slug is **software-selector**.
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

```text

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://app.sleuth.io" path="api/1/deployments/sleuth/production-app/register\_deploy" %}
{% api-method-summary %}
Environment Deploy Registration
{% endapi-method-summary %}

{% api-method-description %}
If there is one environment defined and the parameter isn’t provided, Sleuth will register the deploy against that one environment. For multiple defined environments in which the parameter isn’t provided, Sleuth will register the deploy against the _default_ environment \(there can only be one default environment\). If the `environment` is provided and it matches a configured environment, Sleuth will register the deploy against that environment.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

