---
description: >-
  Use this endpoint with the POST method to register Custom Incident Impact
  values.
---

# Custom Incident Impact Registration

Some teams track incidents outside of traditional Observability tools. [Custom impact sources](../integrations-1/impact-sources/incident-tracker-integrations/custom/) allow you to submit these values to Sleuth and get your Failure Rate and MTTR values.

## Path

{% hint style="info" %}
#### ENDPOINT&#x20;

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
<table><thead><tr><th width="198">Name</th><th width="111">Type</th><th>Comments</th></tr></thead><tbody><tr><td><code>api_key</code><mark style="color:red;">*</mark></td><td>string</td><td>Can be found in the <code>Organization Settings</code> -> <code>Details</code> -> <code>Api Key</code> field in your Sleuth org.</td></tr><tr><td><code>type</code><mark style="color:red;">*</mark></td><td>string</td><td>Valid types are <code>triggered</code>, <code>resolved</code>, and <code>reopened</code>.</td></tr></tbody></table>
{% endtab %}

{% tab title="Optional parameters" %}
<table><thead><tr><th width="198">Name</th><th width="111">Type</th><th>Comments</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>The unique incident identifier from your system.</td></tr><tr><td><code>date</code></td><td>string</td><td>The <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601 </a>date the event occurred. Defaults to the current time.</td></tr><tr><td><code>ended_date</code></td><td>string</td><td><p>The <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO 8601 </a>date the event ended.</p><p>Use it with <code>"type": "triggered"</code> to register past incident event.</p></td></tr><tr><td><code>title</code></td><td>string</td><td>The human-readable title of the incident.</td></tr><tr><td><code>url</code></td><td>string</td><td>URL to the incident in your external system.</td></tr></tbody></table>
{% endtab %}

{% tab title="Responses" %}
<table><thead><tr><th width="112">Code</th><th width="269">Comments</th><th>Response Text</th></tr></thead><tbody><tr><td><mark style="color:green;"><strong><code>200</code></strong></mark></td><td>Manual change registered successfully.</td><td><code>Success</code></td></tr><tr><td><mark style="color:red;"><strong><code>400</code></strong></mark></td><td>Returned if any of the input parameters are invalid, e.g.:<br>- <code>date</code> format isn't valid<br>- <code>value</code> is not a valid float</td><td><p>The response text will indicate the nature of the error:<br></p><p><code>Bad Request - impact value must be a number</code></p></td></tr><tr><td><mark style="color:red;"><strong><code>401</code></strong></mark></td><td>Returned if the API key provided doesn't exist.</td><td><code>Unauthorized</code></td></tr><tr><td><mark style="color:red;"><strong><code>404</code></strong></mark></td><td>Returned if the <mark style="color:red;"><code>IMPACT_ID</code></mark> does not exist.</td><td><code>MetricImpactSource Not Found</code></td></tr><tr><td><mark style="color:red;"><strong><code>429</code></strong></mark></td><td>Returned if your requests are more frequent than one every 120 seconds. A <code>Retry-After</code> header is provided with the number of seconds you should wait until you try again.</td><td><code>You may only register a custom metric once every 120 seconds</code></td></tr></tbody></table>
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
