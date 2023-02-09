---
description: Use this endpoint with the POST method to register deploys.
---

# Deploy Registration

## Path

{% hint style="info" %}
#### ENDPOINT ****&#x20;

https://app.sleuth.io/api/1/deployments/<mark style="color:red;">`ORG_SLUG`</mark>_/<mark style="color:blue;">`DEPLOYMENT_SLUG`</mark>_/register\_deploy
{% endhint %}

The endpoint path takes **2 slugs** which direct the deploy to the correct code deployment:

* <mark style="color:red;">`ORG_SLUG`</mark>: found in the URL of your Sleuth org, immediately following `https://app.sleuth.io/`
* <mark style="color:blue;">`DEPLOYMENT_SLUG`</mark>: found in the URL, following the prefix `https://app.sleuth.io/org_slug/deployments/`

## Parameters

{% tabs %}
{% tab title="Mandatory parameters" %}
| Name                                        | Type   | Comments                                                                                        |
| ------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| `api_key`<mark style="color:red;">\*</mark> | string | Can be found in the `Organization Settings` -> `Details` -> `Api Key` field in your Sleuth org. |
| `sha`<mark style="color:red;">\*</mark>     | string | The git SHA of the commit to be registered as a deploy.                                         |
{% endtab %}

{% tab title="Optional parameters" %}
| Name                  | Type   | Comments                                                                                                                                                                                                                                                   |
| --------------------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `environment`         | string | The environment to register the deploy against. If not provided Sleuth will use the default environment of the Project.                                                                                                                                    |
| `date`                | string | ISO 8601 deployment date and time string                                                                                                                                                                                                                   |
| `tags`                | string | A comma-delimited list of tags. Defaults to tags calculated by matching paths defined in your .sleuth/TAGS file.                                                                                                                                           |
| `ignore_if_duplicate` | string | If the value is provided and set to `true` Sleuth won't return a 400 error if we see a SHA that has already been registered.                                                                                                                               |
| `email`               | string | Email address of author                                                                                                                                                                                                                                    |
| `links`               | string | <p>A key/value pair consisting of the link name and the link itself in the following format:</p><p><code>mylink=http://my.link</code></p><p></p><p>If you need to send multiple then send a JSON body POST where the links are a dictionary of values.</p> |
{% endtab %}

{% tab title="Responses" %}
| Code                                        | Comments                                                                                                                                                                                                                                                                                                                         | Response Text                                                                                                                 |
| ------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:green;">**`200`**</mark> | Deploy registered successfully.                                                                                                                                                                                                                                                                                                  | `Success`                                                                                                                     |
| <mark style="color:red;">**`400`**</mark>   | <p>Returned if any of the input parameters are invalid, e.g.:<br>- <code>sha</code> isn't provided<br>- branch doesn't match the configured branch<br>- <code>date</code> format isn't valid<br>- <code>author</code> is not a valid email<br>- we're unable to validate if the <code>sha</code> exists in the remote system</p> | <p>The response text will indicate the nature of the error:<br><code></code></p><p><code>String of message problem</code></p> |
| <mark style="color:red;">**`401`**</mark>   | API key not valid or the deployment is not in the specified organization                                                                                                                                                                                                                                                         | `String of message problem`                                                                                                   |


{% endtab %}
{% endtabs %}

## Examples

{% hint style="warning" %}
Make sure you **replace the values** surrounded by**`<`** and **`>`**with your **own values.**
{% endhint %}

<details>

<summary>cURL with API key in Header</summary>

<pre class="language-bash" data-overflow="wrap" data-line-numbers><code class="lang-bash"><strong>curl -X POST \
</strong>'https://app.sleuth.io/api/1/deployments/&#x3C;ORG_SLUG>/&#x3C;DEPLOYMENT_SLUG>/register_deploy' \
  -H 'Authorization: apikey &#x3C;APIKEY>' \
  -H 'Content-Type: application/json' \
  -d '{
  "sha": "&#x3C;SHA>",
  "environment": "&#x3C;ENVIRONMENT>"
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
  "sha": "<SHA>",
  "environment": "<ENVIRONMENT>",
  "api_key": "<API_KEY>"
  }'
```
{% endcode %}

</details>

<details>

<summary>PowerShell with API key in Header</summary>

<pre class="language-powershell" data-overflow="wrap" data-line-numbers><code class="lang-powershell"><strong>Invoke-RestMethod -Method POST `
</strong><strong>-Uri 'https://app.sleuth.io/api/1/deployments/&#x3C;ORG_SLUG>/&#x3C;DEPLOYMENT_SLUG>/register-deploy' `
</strong><strong>-Headers @{
</strong><strong>      'Authorization' = 'apikey &#x3C;API_KEY>'
</strong><strong>      'Content-Type' = 'application/json'
</strong>} `
-Body '{
      "environment": "&#x3C;ENVIRONMENT>",
      "sha": "&#x3C;SHA>" 
 }'
</code></pre>

</details>

<details>

<summary>PowerShell with API key in Body</summary>

{% code overflow="wrap" lineNumbers="true" %}
```powershell
Invoke-RestMethod -Method POST `
-Uri 'https://app.sleuth.io/api/1/deployments/<ORG_SLUG>/<DEPLOYMENT_SLUG>/register-deploy' `
-Headers @{
    'Content-Type' = 'application/json'
} `
-Body '{
    "api_key": "<API_KEY>",
    "environment": "<ENVIRONMENT>",
    "sha": "<SHA>"
}'
```
{% endcode %}

</details>

<details>

<summary>cURL using Custom Git</summary>

{% code overflow="wrap" lineNumbers="true" %}
```bash
curl -X POST -v \
'https://app.sleuth.io/api/1/deployments/<ORG_SLUG>/<DEPLOYMENT_SLUG>/register_deploy' \
  -H 'Authorization: apikey <APIKEY>' \
  -H 'Content-Type: application/json' \
  -d '{
    "sha": "<SHA>",
    "environment": "<ENVIRONMENT>",
    "ignore_if_duplicate": "true",
    "commits": [
      {
        "revision": "<COMMIT SHA>",
        "message": "<YOUR COMMIT MESSAGE>",
        "author": {
          "name": "Jane",
          "email": "jane@email.com",
          "username": "jane@email.com"
        },
        "date": "2022-08-01T00:10:10+00:00",
        "files": [
          "/some/path/to/a/file.txt"
        ],
        "parents": [
          "<PARENT SHA>"
        ],
        "url": "http://www.commits/aaa"
      }
    ],
    "files": [
      {
        "path": "http://www.example.com/some/path.txt",
        "additions": 3,
        "deletions": 0,
        "url": "http://www.example.com"
      }
    ]
  }'
```
{% endcode %}

</details>
