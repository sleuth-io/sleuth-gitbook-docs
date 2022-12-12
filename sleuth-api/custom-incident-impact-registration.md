---
description: >-
  Use this endpoint with the POST method to register Custom Incident Impact
  values.
---

# Custom Incident Impact Registration

Some teams track incidents outside of traditional Observability tools. [Custom impact sources](../integrations-1/incident-tracker-integrations/custom.md) allow you to submit these values to Sleuth and get your Failure Rate and MTTR values.

## Path

{% hint style="info" %}
#### ENDPOINT ****&#x20;

https://app.sleuth.io/api/1/deployments/<mark style="color:red;">`ORG_SLUG`</mark>/<mark style="color:blue;">`PROJECT_SLUG`</mark>/<mark style="color:green;">`ENVIRONMENT_SLUG`</mark>/<mark style="color:orange;">`IMPACT_SOURCE_SLUG`</mark>/register\_impact/`APIKEY`
{% endhint %}

The endpoint path takes **4 slugs** which direct the manual changes to the correct code project:

* <mark style="color:red;">`ORG_SLUG`</mark>: found in the URL of your Sleuth org, immediately following `https://app.sleuth.io/`
* <mark style="color:blue;">`PROJECT_SLUG`</mark>: found in the URL, following the prefix `https://app.sleuth.io/org_slug/`
* <mark style="color:green;">`ENVIRONMENT_SLUG`</mark>: found at the end of the URL of your Sleuth org when navigating to the target project and selecting the target custom incident impact source: `env_slug=`<mark style="color:green;">`ENVIRONMENT_SLUG`</mark>
* <mark style="color:orange;">`IMPACT_SOURCE_SLUG`</mark>: found in the URL of your Sleuth org when navigating to the target project and selecting the target custom incident impact source, just before the `?env_slug`

The `API key` must also be added to the **end of the path** in this instance.

### Parameters

{% tabs %}
{% tab title="Mandatory parameters" %}
| Name                                        | Type   | Comments                                                                                        |
| ------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| `api_key`<mark style="color:red;">\*</mark> | string | Can be found in the `Organization Settings` -> `Details` -> `Api Key` field in your Sleuth org. |
| `type`<mark style="color:red;">\*</mark>    | string | Valid types are `triggered`, `resolved`, and `reopened`.                                        |
{% endtab %}

{% tab title="Optional parameters" %}
| Name    | Type   | Comments                                                                                                       |
| ------- | ------ | -------------------------------------------------------------------------------------------------------------- |
| `id`    | string | The unique incident identifier from your system.                                                               |
| `date`  | string | The [ISO 8601 ](https://en.wikipedia.org/wiki/ISO\_8601)date the event occurred. Defaults to the current time. |
| `title` | string | The human-readable title of the incident.                                                                      |
| `url`   | string | URL to the incident in your external system.                                                                   |
{% endtab %}

{% tab title="Responses" %}
| Code                                        | Comments                                                                                                                                                                   | Response Text                                                                                                                                   |
| ------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:green;">**`200`**</mark> | Manual change registered successfully.                                                                                                                                     | `Success`                                                                                                                                       |
| <mark style="color:red;">**`400`**</mark>   | <p>Returned if any of the input parameters are invalid, e.g.:<br>- <code>date</code> format isn't valid<br>- <code>value</code> is not a valid float</p>                   | <p>The response text will indicate the nature of the error:<br><code></code></p><p><code>Bad Request - impact value must be a number</code></p> |
| <mark style="color:red;">**`401`**</mark>   | Returned if the API key provided doesn't exist.                                                                                                                            | `Unauthorized`                                                                                                                                  |
| <mark style="color:red;">**`404`**</mark>   | Returned if the <mark style="color:red;">`IMPACT_ID`</mark> does not exist.                                                                                                | `MetricImpactSource Not Found`                                                                                                                  |
| <mark style="color:red;">**`429`**</mark>   | Returned if your requests are more frequent than one every 120 seconds. A `Retry-After` header is provided with the number of seconds you should wait until you try again. | `You may only register a custom metric once every 120 seconds`                                                                                  |
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
Make sure you **replace the values** surrounded by**`<`** and **`>`**with your **own values**.&#x20;
{% endhint %}

<details>

<summary>cURL with API key in Path</summary>

<pre class="language-bash" data-overflow="wrap" data-line-numbers><code class="lang-bash"><strong>curl -X POST \
</strong>'https://app.sleuth.io/api/1/deployments/&#x3C;ORG_SLUG>/&#x3C;PROJECT_SLUG>/&#x3C;ENVIRONMENT>/&#x3C;IMPACT_ID>/register_impact/&#x3C;APIKEY>' \
  -H 'Content-Type: application/json' \
  -d '{
  "type": "&#x3C;TYPE>"
}'
</code></pre>

</details>

<details>

<summary>PowerShell with API key in Path</summary>

{% code overflow="wrap" lineNumbers="true" %}
```powershell
Invoke-RestMethod -Method POST `
-Uri 'https://app.sleuth.io/api/1/deployments/<ORG_SLUG>/<PROJECT_SLUG>/<ENVIRONMENT>/<IMPACT_ID>/register_impact/<APIKEY>' `
-Headers @{
    'Content-Type' = 'application/json'
} `
-Body '{
    "type": "<TYPE>"
}'
```
{% endcode %}

</details>
