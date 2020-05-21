# API Reference

The Sleuth REST API provides methods that allow access for project and deploy manipulation. 

### Authentication

The Sleuth REST API requires authentication using the API key from your Sleuth [project](../projects.md).

{% api-method method="post" host="https://app.sleuth.io" path="api/1/<Organization Name>/<Project Name>/register\_deploy" %}
{% api-method-summary %}
Manual Deploy Registration
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="Organization Name" type="string" required=true %}
Sleuth organization that contains the affected project. 
{% endapi-method-parameter %}

{% api-method-parameter name="Project Name" type="string" required=true %}
Name of the project that you're registering a deploy to. 
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="YOUR\_SHA" type="string" required=true %}
The Git commit hash of the deploy you're manually registering. 
{% endapi-method-parameter %}

{% api-method-parameter name="YOUR\_API\_KEY" type="string" required=true %}
Your Sleuth organization's API key, which can be found in your Project Settings. 
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Success
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://app.sleuth.io" path="/api/1/deployments/<Organization Name>/<Project Name>/register\_manual\_deploy" %}
{% api-method-summary %}
Manual Change
{% endapi-method-summary %}

{% api-method-description %}
Manual changes are those not tracked by source code, feature flags, or any other type of change not supported by Sleuth. They are a free-form entry that can have any name or description you'd like. 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="Organization Name" type="string" required=true %}
Sleuth organization that contains the affected project. 
{% endapi-method-parameter %}

{% api-method-parameter name="Project Name" type="string" required=true %}
Name of the project that you're registering a deploy to. 
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="api\_key" type="string" required=true %}
Your Sleuth organization's API key, which can be found in your Project Settings. 
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="email" type="string" required=true %}
The email address of the user associated with the project receiving the manual change.  
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=false %}
The title for your manual change. 
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}
The description of your manual change. 
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

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Could not find the project and/or organization. 
{% endapi-method-response-example-description %}

```
404
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

