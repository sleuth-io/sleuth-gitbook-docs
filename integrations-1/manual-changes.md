# Manual Changes

Manual changes let you enter anything that you want tracked in Sleuth. Such changes are those not tracked by source code, feature flags, or another type of change that Sleuth [currently supports](about-integrations....md). They are a free-form entry that can have any name or description you'd like. 

Examples include: 

* A manual scaling event
* A restart of a service
* An increase in capacity

To add a manual change: 

1. Click **Create** then **Add Manual Change** in the sidebar. 
2. Give the manual change a **Name** and **Description**. 
3. Press **Create**. 

{% hint style="info" %}
Well-formed cURL information with your data filled is displayed on this page \(see screenshot below\). This is useful if you wish to submit manual changes via a POST request, as described below. 
{% endhint %}

![cURL information in Add Manual Change page](../.gitbook/assets/curl_url_dialog.png)

The manual change will display on your [Dashboard](../dashboard.md) and shown just like any other source of change. Manual changes are not tracked by Sleuth; you'll need to update and manage them on your own. 

{% api-method method="post" host="https://app.sleuth.io/api/1/deployments" path="/<organization name>/<project name>/register\_manual\_deploy" %}
{% api-method-summary %}
Submit Manual Change
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="Project Name" type="string" required=false %}
The name of the Project that you wish to add a Manual Change report to. Replace spaces with dashes.  
{% endapi-method-parameter %}

{% api-method-parameter name="Organization Name" type="string" required=false %}
The name of organization in Sleuth. Can be found in Organization Settings. Replace spaces with dashes. 
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
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

```text
curl -X POST -d api_key=YOUR_API_KEY -d https://sleuth.io/api/1/ORG_NAME/PROJECT_NAME/register_deploy
```

Replace `API_KEY`, `TITLE`, `DESCRIPTION`, `ORG_NAME`, and `PROJECT_NAME` with your actual values.

