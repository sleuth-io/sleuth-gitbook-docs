# Sleuth API

The Sleuth REST API provides methods that enables users to:

* Manually register their deploys
* Submit manual changes

### Authentication

The Sleuth REST API requires authentication using the API key from your Sleuth [project](../projects.md).

{% api-method method="post" host="https://app.sleuth.io" path="api/1/<Organization Slug>/<Deployment Slug>/register\_deploy" %}
{% api-method-summary %}
Manual Deploy Registration
{% endapi-method-summary %}

{% api-method-description %}
Manually register your deploys via the Sleuth API. Keep in mind that the organization and deployment slugs are not the semantic name of your organization and deployment as shown in the organization settings, which can contains spaces and capitalized characters. Rather, they're the slugs as displayed in the URL of your organization and deployment, with spaces and replaced by a hyphen \(**-**\); non-alphabetical characters \(e.g., **\(\)@\#$%^**, etc.\) are ignored.   
  
For example, if you're viewing a deployment called _plugin picker \(dev\)_ and your organization is called _Amazing Software_, the URL will display as **https://app.sleuth.io/amazing-software/deployments/plugin-picker-dev**. The organization slug is **amazing-softwar**e, the deployment slug is **plugin-picker-dev**. 
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
Manual changes are those not tracked by source code, feature flags, or any other type of change not supported by Sleuth. They are a free-form entry that includes a **name** and **description**. Although the description is optional, the form data in the manual change must contain a name as one of its parameters.   
  
For example, if you're viewing a project called _Software Selector_ and your organization is called _Amazing Software_, the URL will display as **https://app.sleuth.io/amazing-software/software-selector**. The organization slug is **amazing-software**, the project slug is **software-selector**.
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
