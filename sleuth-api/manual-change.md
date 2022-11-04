---
description: Use this endpoint with the POST method to register manual changes.
---

# Manual Change

Manual changes are any changes not tracked by source code, feature flags, or any other type of change not supported by Sleuth. They are free-form entries that include a name and description. Although the description is optional, the form data in the manual change must contain a name as one of its parameters.

## Path

{% hint style="info" %}
#### ENDPOINT ****&#x20;

https://app.sleuth.io/api/1/deployments/<mark style="color:red;">`ORG_SLUG`</mark>_/<mark style="color:blue;">`PROJECT_SLUG`</mark>_/register\_manual\_deploy
{% endhint %}

The endpoint path takes **2 slugs** which direct the manual changes to the correct code project:

* <mark style="color:red;">`ORG_SLUG`</mark>: found in the URL of your Sleuth org, immediately following `https://app.sleuth.io/`
* <mark style="color:blue;">`PROJECT_SLUG`</mark>: found in the URL, following the prefix `https://app.sleuth.io/org_slug/`

``

### Parameters

{% tabs %}
{% tab title="Mandatory parameters" %}
| Name                                        | Type   | Comments                                                                                        |
| ------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| `api_key`<mark style="color:red;">\*</mark> | string | Can be found in the `Organization Settings` -> `Details` -> `Api Key` field in your Sleuth org. |
| `name`<mark style="color:red;">\*</mark>    | string | Title for the manual change.                                                                    |
{% endtab %}

{% tab title="Optional parameters" %}
| Name          | Type   | Comments                                                                                                                |
| ------------- | ------ | ----------------------------------------------------------------------------------------------------------------------- |
| `description` | string | Description for the manual change.                                                                                      |
| `environment` | string | The environment to register the change against. If not provided Sleuth will use the default environment of the Project. |
| `tags`        | string | A comma-delimited list of tags.                                                                                         |
| `author`      | string | Email address of change author.                                                                                         |
| `email`       | string | Email address of the user associated with the project receiving the manual change.                                      |
{% endtab %}

{% tab title="Responses" %}
| Code                                        | Comments                                                                                                                                                  | Response Text                                                                                                                 |
| ------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:green;">**`200`**</mark> | Manual change registered successfully.                                                                                                                    | `Success`                                                                                                                     |
| <mark style="color:red;">**`400`**</mark>   | <p>Returned if any of the input parameters are invalid, e.g.:<br>- <code>date</code> format isn't valid<br>- <code>author</code> is not a valid email</p> | <p>The response text will indicate the nature of the error:<br><code></code></p><p><code>String of message problem</code></p> |
| <mark style="color:red;">**`401`**</mark>   | Returned if the API key provided doesn't exist.                                                                                                           | `Unauthorized`                                                                                                                |
| <mark style="color:red;">**`404`**</mark>   | Returned if the project does not exist.                                                                                                                   | `Project not found`                                                                                                           |
| <mark style="color:red;">**`422`**</mark>   | Returned if `name` is not provided                                                                                                                        | `Name is required.`                                                                                                           |


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
}'</code></pre>

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
