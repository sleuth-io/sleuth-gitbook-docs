# Sleuth API

{% api-method method="post" host="https://sleuth.io" path="/api/1/ORG\_NAME/PROJECT\_NAME/register\_deploy" %}
{% api-method-summary %}
Manual Deploy
{% endapi-method-summary %}

{% api-method-description %}
This method allows you to make a manual deploy to Sleuth using a Git commit SHA or tag via POST. 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="Org Name" type="string" required=false %}
The name of your Sleuth Organization
{% endapi-method-parameter %}

{% api-method-parameter name="Project Name" type="string" required=false %}
The name of the Sleuth Project within the Organization
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

```
curl -X POST -d api_key=YOUR_API_KEY -d sha=YOUR_SHA https://sleuth.io/api/1/ORG_NAME/PROJECT_NAME/register_deploy
```

Replace `YOUR_API_KEY`, `YOUR_SHA`, `ORG_NAME` and `PROJECT_NAME` with your actual information.

**You can find `YOUR_SHA` with the commands:**

```text
git checkout YOUR_BRANCH
git rev-parse HEAD
```



