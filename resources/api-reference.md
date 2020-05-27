# API Reference

The Sleuth REST API provides methods that allow access for project and deploy manipulation. 

### Authentication

The Sleuth REST API requires authentication using the API key from your Sleuth [project](../projects.md).

{% api-method method="post" host="https://app.sleuth.io" path="api/1/<Organization Slug>/<Deployment Slug>/register\_deploy" %}
{% api-method-summary %}
Manual Deploy Registration
{% endapi-method-summary %}

{% api-method-description %}
This allows users to manually register their deploys. 
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
Deployment code SHA that defines the deployment. Look in copy for tracking your deploys page
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
Input date problem, including if SHA doesn't exist or has already been reported. 
{% endapi-method-response-example-description %}

```
String of message problem
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
API key not valid or the deployment is not in the specific organization
{% endapi-method-response-example-description %}

```
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
Manual changes are those not tracked by source code, feature flags, or any other type of change not supported by Sleuth. They are a free-form entry that can have any name or description you'd like. 
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
Success.
{% endapi-method-response-example-description %}

```
Success.
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=302 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

