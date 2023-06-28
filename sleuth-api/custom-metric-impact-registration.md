---
description: >-
  Use this endpoint with the POST method to register Custom Metric Impact
  values.
---

# Custom Metric Impact Registration

You can submit custom metric impact values to Sleuth. Sleuth will perform its anomaly detection on these values and they will inform the health of your deploys. Values can represent any metric that matters to you and must be represented via a float.

## Path

{% hint style="info" %}
#### ENDPOINT&#x20;

https://app.sleuth.io/api/1/impact/<mark style="color:red;">`IMPACT_ID`</mark>_/_register\_impact
{% endhint %}

The endpoint path takes **1 ID** which uniquely identifies the Impact Source to register a value against:

* <mark style="color:red;">`IMPACT_ID`</mark>: must be an `integer`, you can find the full path (_including the ID_) in your Sleuth org by navigating to your [**Custom Metric Impact Source**](https://help.sleuth.io/integrations-1/impact-sources/metrics/custom), clicking the **gearwheel icon** in the top-right corner, and selecting "**Show register details**"

### Parameters

{% tabs %}
{% tab title="Mandatory parameters" %}
<table><thead><tr><th width="198">Name</th><th width="111">Type</th><th>Comments</th></tr></thead><tbody><tr><td><code>api_key</code><mark style="color:red;">*</mark></td><td>string</td><td>Can be found in the <code>Organization Settings</code> -> <code>Details</code> -> <code>Api Key</code> field in your Sleuth org.</td></tr><tr><td><code>value</code><mark style="color:red;">*</mark></td><td>float</td><td>The metric value to be registered. </td></tr></tbody></table>
{% endtab %}

{% tab title="Optional parameters" %}
<table><thead><tr><th width="198">Name</th><th width="111">Type</th><th>Comments</th></tr></thead><tbody><tr><td><code>date</code></td><td>string</td><td>The date and time at which the metric value should be registered. If left blank, it defaults to the current time. Must be in <a href="https://en.wikipedia.org/wiki/ISO_8601">ISO-8601</a> format.</td></tr></tbody></table>
{% endtab %}

{% tab title="Responses" %}
<table><thead><tr><th width="112">Code</th><th width="269">Comments</th><th>Response Text</th></tr></thead><tbody><tr><td><mark style="color:green;"><strong><code>200</code></strong></mark></td><td>Manual change registered successfully.</td><td><code>Success</code></td></tr><tr><td><mark style="color:red;"><strong><code>400</code></strong></mark></td><td>Returned if any of the input parameters are invalid, e.g.:<br>- <code>date</code> format isn't valid<br>- <code>value</code> is not a valid float</td><td><p>The response text will indicate the nature of the error:<br></p><p><code>Bad Request - impact value must be a number</code></p></td></tr><tr><td><mark style="color:red;"><strong><code>401</code></strong></mark></td><td>Returned if the API key provided doesn't exist.</td><td><code>Unauthorized</code></td></tr><tr><td><mark style="color:red;"><strong><code>404</code></strong></mark></td><td>Returned if the <mark style="color:red;"><code>IMPACT_ID</code></mark> does not exist.</td><td><code>MetricImpactSource Not Found</code></td></tr><tr><td><mark style="color:red;"><strong><code>429</code></strong></mark></td><td>Returned if your requests are more frequent than one every 120 seconds. A <code>Retry-After</code> header is provided with the number of seconds you should wait until you try again.</td><td><code>You may only register a custom metric once every 120 seconds</code></td></tr></tbody></table>
{% endtab %}
{% endtabs %}

### Examples

{% hint style="warning" %}
Make sure you **replace the values** surrounded by**`<`** and **`>`**with your **own values**.&#x20;
{% endhint %}

<details>

<summary>cURL with API key in Header</summary>

<pre class="language-bash" data-overflow="wrap" data-line-numbers><code class="lang-bash"><strong>curl -X POST \
</strong>'https://app.sleuth.io/api/1/impact/&#x3C;IMPACT_ID>/register_impact' \
  -H 'Authorization: apikey &#x3C;APIKEY>' \
  -H 'Content-Type: application/json' \
  -d '{
  "value": &#x3C;METRIC_VALUE>
}'
</code></pre>

</details>

<details>

<summary>cURL with API key in Body</summary>

{% code overflow="wrap" lineNumbers="true" %}
```bash
curl -X POST \
'https://app.sleuth.io/api/1/impact/<IMPACT_ID>/register_impact' \
  -H 'Content-Type: application/json' \
  -d '{
  "value": <METRIC_VALUE>,
  "api_key": "<APIKEY>"
}'
```
{% endcode %}

</details>

<details>

<summary>PowerShell with API key in Header</summary>

{% code overflow="wrap" lineNumbers="true" %}
```powershell
Invoke-RestMethod -Method POST `
-Uri 'https://app.sleuth.io/api/1/impact/<IMPACT_ID>/register_impact' `
-Headers @{
    'Authorization' = 'apikey <APIKEY>'                              
    'Content-Type' = 'application/json' 
} `
-Body '{ 
    "value": <METRIC_VALUE> 
}'
```
{% endcode %}

</details>

<details>

<summary>PowerShell with API key in Body</summary>

{% code overflow="wrap" lineNumbers="true" %}
```powershell
Invoke-RestMethod -Method POST `
-Uri 'https://app.sleuth.io/api/1/impact/<IMPACT_ID>/register_impact' `
-Headers @{
    'Content-Type' = 'application/json'                              
} `
-Body '{ 
    "api_key": "<APIKEY>",
    "value": <METRIC_VALUE> 
}'
```
{% endcode %}

</details>
