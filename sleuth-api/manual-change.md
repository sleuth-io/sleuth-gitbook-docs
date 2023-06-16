---
description: Use this endpoint with the POST method to register manual changes.
---

# Manual Change

Manual changes are any changes not tracked by source code, feature flags, or any other type of change not supported by Sleuth. They are free-form entries that include a name and description. Although the description is optional, the form data in the manual change must contain a name as one of its parameters.

## Path

{% hint style="info" %}
#### ENDPOINT&#x20;

https://app.sleuth.io/api/1/deployments/<mark style="color:red;">`ORG_SLUG`</mark>_/<mark style="color:blue;">`PROJECT_SLUG`</mark>_/register\_manual\_deploy
{% endhint %}

The endpoint path takes **2 slugs** which direct the manual changes to the correct code project:

* <mark style="color:red;">`ORG_SLUG`</mark>: found in the URL of your Sleuth org, immediately following `https://app.sleuth.io/`
* <mark style="color:blue;">`PROJECT_SLUG`</mark>: found in the URL, following the prefix `https://app.sleuth.io/org_slug/`



### Parameters

{% tabs %}
{% tab title="Mandatory parameters" %}
<table><thead><tr><th width="198">Name</th><th width="111">Type</th><th>Comments</th></tr></thead><tbody><tr><td><code>api_key</code><mark style="color:red;">*</mark></td><td>string</td><td>Can be found in the <code>Organization Settings</code> -> <code>Details</code> -> <code>Api Key</code> field in your Sleuth org.</td></tr><tr><td><code>name</code><mark style="color:red;">*</mark></td><td>string</td><td>Title for the manual change.</td></tr></tbody></table>
{% endtab %}

{% tab title="Optional parameters" %}
<table><thead><tr><th width="198">Name</th><th width="111">Type</th><th>Comments</th></tr></thead><tbody><tr><td><code>description</code></td><td>string</td><td>Description for the manual change.</td></tr><tr><td><code>environment</code></td><td>string</td><td>The environment to register the change against. If not provided Sleuth will use the default environment of the Project.</td></tr><tr><td><code>tags</code></td><td>string</td><td>A comma-delimited list of tags. </td></tr><tr><td><code>author</code></td><td>string</td><td>Email address of change author.</td></tr><tr><td><code>email</code></td><td>string</td><td>Email address of the user associated with the project receiving the manual change.</td></tr></tbody></table>
{% endtab %}

{% tab title="Responses" %}
<table><thead><tr><th width="112">Code</th><th width="269">Comments</th><th>Response Text</th></tr></thead><tbody><tr><td><mark style="color:green;"><strong><code>200</code></strong></mark></td><td>Manual change registered successfully.</td><td><code>Success</code></td></tr><tr><td><mark style="color:red;"><strong><code>400</code></strong></mark></td><td>Returned if any of the input parameters are invalid, e.g.:<br>- <code>date</code> format isn't valid<br>- <code>author</code> is not a valid email</td><td><p>The response text will indicate the nature of the error:<br></p><p><code>String of message problem</code></p></td></tr><tr><td><mark style="color:red;"><strong><code>401</code></strong></mark></td><td>Returned if the API key provided doesn't exist.</td><td><code>Unauthorized</code></td></tr><tr><td><mark style="color:red;"><strong><code>404</code></strong></mark></td><td>Returned if the project does not exist.</td><td><code>Project not found</code></td></tr><tr><td><mark style="color:red;"><strong><code>422</code></strong></mark></td><td>Returned if <code>name</code> is not provided</td><td><code>Name is required.</code></td></tr></tbody></table>


{% endtab %}
{% endtabs %}

### Examples

{% hint style="warning" %}
Make sure you **replace the values** surrounded by**`<`** and **`>`**with your **own values**.&#x20;
{% endhint %}

<details>

<summary>cURL with API key in Header</summary>

<pre class="language-bash" data-overflow="wrap" data-line-numbers><code class="lang-bash"><strong>curl -X POST \
</strong>'https://app.sleuth.io/api/1/deployments/&#x3C;ORG_SLUG>/&#x3C;DEPLOYMENT_SLUG>/register_manual_deploy' \
  -H 'Authorization: apikey &#x3C;APIKEY>' \
  -H 'Content-Type: application/json' \
  -d '{
  "name": "&#x3C;NAME>",
  "description": "&#x3C;description>"
}'
</code></pre>

</details>

<details>

<summary>cURL with API key in Body</summary>

{% code overflow="wrap" lineNumbers="true" %}
```bash
curl -X POST \
'https://app.sleuth.io/api/1/deployments/<ORG_SLUG>/<DEPLOYMENT_SLUG>/register_deploy' \
  -H 'Content-Type: application/json' \
  -d '{
  "name": "<NAME>",
  "description": "<DESCRIPTION>",
  "api_key": <API_KEY>
  }'
```
{% endcode %}

</details>

<details>

<summary>PowerShell with API key in Header</summary>

{% code overflow="wrap" lineNumbers="true" %}
```powershell
Invoke-RestMethod -Method POST `
-Uri 'https://app.sleuth.io/api/1/deployments/<ORG_SLUG>/<DEPLOYMENT_SLUG>/register_manual_deploy' `
-Headers @{
    'Authorization' = 'apikey <APIKEY>'
    'Content-Type' = 'application/json'   
} `
-Body '{
    "name": "<NAME>",
    "description": "<description>"
}'
```
{% endcode %}

</details>

<details>

<summary>PowerShell with API key in Body</summary>

{% code overflow="wrap" lineNumbers="true" %}
```powershell
Invoke-RestMethod -Method POST `
-Uri 'https://app.sleuth.io/api/1/deployments/<ORG_SLUG>/<DEPLOYMENT_SLUG>/register_deploy' `
-Headers @{
    'Content-Type' = 'application/json'   
} `
-Body '{
    "api_key": "<API_KEY>",
    "name": "<NAME>",
    "description": "<DESCRIPTION>"
}'
```
{% endcode %}

</details>
