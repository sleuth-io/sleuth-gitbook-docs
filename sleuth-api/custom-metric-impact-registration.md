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
| Name                                        | Type   | Comments                                                                                        |
| ------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| `api_key`<mark style="color:red;">\*</mark> | string | Can be found in the `Organization Settings` -> `Details` -> `Api Key` field in your Sleuth org. |
| `value`<mark style="color:red;">\*</mark>   | float  | The metric value to be registered.                                                              |
{% endtab %}

{% tab title="Optional parameters" %}
| Name   | Type   | Comments                                                                                                                                                                                 |
| ------ | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `date` | string | The date and time at which the metric value should be registered. If left blank, it defaults to the current time. Must be in [ISO-8601](https://en.wikipedia.org/wiki/ISO\_8601) format. |
{% endtab %}

{% tab title="Responses" %}
| Code                                        | Comments                                                                                                                                                                   | Response Text                                                                                                                      |
| ------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:green;">**`200`**</mark> | Manual change registered successfully.                                                                                                                                     | `Success`                                                                                                                          |
| <mark style="color:red;">**`400`**</mark>   | <p>Returned if any of the input parameters are invalid, e.g.:<br>- <code>date</code> format isn't valid<br>- <code>value</code> is not a valid float</p>                   | <p>The response text will indicate the nature of the error:<br></p><p><code>Bad Request - impact value must be a number</code></p> |
| <mark style="color:red;">**`401`**</mark>   | Returned if the API key provided doesn't exist.                                                                                                                            | `Unauthorized`                                                                                                                     |
| <mark style="color:red;">**`404`**</mark>   | Returned if the <mark style="color:red;">`IMPACT_ID`</mark> does not exist.                                                                                                | `MetricImpactSource Not Found`                                                                                                     |
| <mark style="color:red;">**`429`**</mark>   | Returned if your requests are more frequent than one every 120 seconds. A `Retry-After` header is provided with the number of seconds you should wait until you try again. | `You may only register a custom metric once every 120 seconds`                                                                     |
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
  -H 'Authorization: apikey &#x3C;APIKEY>'
  -H 'Content-Type: application/json' \
  -d '{
  "value": &#x3C;METRIC_VALUE>
}'
</code></pre>

</details>

<details>

<summary>cURL with API key in Body</summary>

```bash
curl -X POST \
'https://app.sleuth.io/api/1/impact/<IMPACT_ID>/register_impact' \
  -H 'Content-Type: application/json' \
  -d '{
  "value": <METRIC_VALUE>,
  "api_key": "<APIKEY>"
}'
```

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

</details>
