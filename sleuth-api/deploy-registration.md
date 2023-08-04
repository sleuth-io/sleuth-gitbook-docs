---
description: Use this endpoint with the POST method to register deploys.
---

# Deploy Registration

## Path

{% hint style="info" %}
#### ENDPOINT&#x20;

https://app.sleuth.io/api/1/deployments/<mark style="color:red;">`ORG_SLUG`</mark>_/<mark style="color:blue;">`DEPLOYMENT_SLUG`</mark>_/register\_deploy
{% endhint %}

The endpoint path takes **2 slugs** which direct the deploy to the correct code deployment:

* <mark style="color:red;">`ORG_SLUG`</mark>: found in the URL of your Sleuth org, immediately following `https://app.sleuth.io/`
* <mark style="color:blue;">`DEPLOYMENT_SLUG`</mark>: found in the URL, following the prefix `https://app.sleuth.io/org_slug/deployments/`

## Parameters

{% tabs %}
{% tab title="Mandatory parameters" %}
<table><thead><tr><th width="206.1571906354515">Name</th><th width="109">Type</th><th>Comments</th></tr></thead><tbody><tr><td><code>api_key</code><mark style="color:red;">*</mark></td><td>string</td><td>Can be found in the <code>Organization Settings</code> -> <code>Details</code> -> <code>Api Key</code> field in your Sleuth org.</td></tr><tr><td><code>sha</code><mark style="color:red;">*</mark></td><td>string</td><td>The git SHA of the commit to be registered as a deploy.</td></tr></tbody></table>
{% endtab %}

{% tab title="Optional parameters" %}
<table><thead><tr><th width="198">Name</th><th width="111">Type</th><th>Comments</th></tr></thead><tbody><tr><td><code>environment</code></td><td>string</td><td>The environment to register the deploy against. If not provided Sleuth will use the default environment of the Project.</td></tr><tr><td><code>date</code></td><td>string</td><td>ISO 8601 deployment date and time string</td></tr><tr><td><code>tags</code></td><td>string</td><td>A comma-delimited list of tags. Defaults to tags calculated by matching paths defined in your .sleuth/TAGS file.<br><br><span data-gb-custom-inline data-tag="emoji" data-code="2139">ℹ</span> Please note that tags must start with the <code>#</code> symbol, must be separated with commas, and cannot contain the <code>.</code> symbol.</td></tr><tr><td><code>ignore_if_duplicate</code></td><td>string</td><td>If the value is provided and set to <code>true</code> Sleuth won't return a 400 error if we see a SHA that has already been registered.</td></tr><tr><td><code>email</code></td><td>string</td><td>Email address of author</td></tr><tr><td><code>links</code></td><td>string</td><td><p>A key/value pair consisting of the link name and the link itself in the following format:</p><p><code>mylink=http://my.link</code></p><p></p><p>If you need to send multiple then send a JSON body POST where the links are a dictionary of values.</p></td></tr></tbody></table>


{% endtab %}

{% tab title="Responses" %}
<table><thead><tr><th width="112">Code</th><th width="269">Comments</th><th>Response Text</th></tr></thead><tbody><tr><td><mark style="color:green;"><strong><code>200</code></strong></mark></td><td>Deploy registered successfully.</td><td><code>Success</code></td></tr><tr><td><mark style="color:red;"><strong><code>400</code></strong></mark></td><td>Returned if any of the input parameters are invalid, e.g.:<br>- <code>sha</code> isn't provided<br>- branch doesn't match the configured branch<br>- <code>date</code> format isn't valid<br>- <code>author</code> is not a valid email<br>- we're unable to validate if the <code>sha</code> exists in the remote system</td><td><p>The response text will indicate the nature of the error:<br></p><p><code>String of message problem</code></p></td></tr><tr><td><mark style="color:red;"><strong><code>401</code></strong></mark></td><td>API key not valid or the deployment is not in the specified organization</td><td><code>String of message problem</code></td></tr></tbody></table>


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

<summary>cURL with API key in Body and optional Tags</summary>

<pre class="language-bash" data-overflow="wrap" data-line-numbers><code class="lang-bash">curl -X POST \
'https://app.sleuth.io/api/1/deployments/&#x3C;ORG_SLUG>/&#x3C;DEPLOYMENT_SLUG>/register_deploy' \
  -H 'Content-Type: application/json' \
  -d '{
  "sha": "&#x3C;SHA>",
  "environment": "&#x3C;ENVIRONMENT>",
  "tags": [
    "#tag1",
    "#tag2",
    "#tag3"
  ],
  "api_key": "&#x3C;API_KEY>"
<strong>  }'
</strong></code></pre>

:information\_source: Please note that tags must start with the `#` symbol, must be separated with commas, and cannot contain the `.` symbol.

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
