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

## Authentication

{% hint style="success" %}
Each request must contain an `Authorization` header including an **Access Token**. We recommend using an **Access Token with** **limited scope** which can only be used for deploy registration.&#x20;
{% endhint %}

You can manage your org's tokens it in the `Organization Settings` -> `Access Tokens` page.

## Parameters

{% tabs %}
{% tab title="Mandatory parameters" %}
<table><thead><tr><th width="206.1571906354515">Name</th><th width="109">Type</th><th>Comments</th></tr></thead><tbody><tr><td><code>sha</code><mark style="color:red;">*</mark></td><td>string</td><td>The git SHA of the commit to be registered as a deploy.</td></tr></tbody></table>
{% endtab %}

{% tab title="Optional parameters" %}
<table><thead><tr><th width="198">Name</th><th width="111">Type</th><th>Comments</th></tr></thead><tbody><tr><td><code>environment</code></td><td>string</td><td>The environment to register the deploy against. If not provided Sleuth will use the default environment of the Project.</td></tr><tr><td><code>date</code></td><td>string</td><td>ISO 8601 deployment date and time string</td></tr><tr><td><code>branch</code></td><td>string</td><td>If your code deployment's target environment is mapped to a branch prefix (<em>rather than a specific branch</em>), you must include the deploy’s full branch name as the parameter <code>branch</code>.</td></tr><tr><td><code>tags</code></td><td>string</td><td><p>A single string or a comma-delimited list of tags. Defaults to tags calculated by matching paths defined in your .sleuth/TAGS file.<br><br><span data-gb-custom-inline data-tag="emoji" data-code="2139">ℹ️</span> Please note that tags must start with the <code>#</code> symbol, and can only contain:</p><ul><li>lowercase letters,</li><li>numbers, and </li><li>symbols <code>-</code> and <code>_</code> .</li></ul></td></tr><tr><td><code>ignore_if_duplicate</code></td><td>string</td><td>If the value is provided and set to <code>true</code> Sleuth won't return a 400 error if we see a SHA that has already been registered.</td></tr><tr><td><code>email</code></td><td>string</td><td>Email address of author</td></tr><tr><td><code>links</code></td><td>string</td><td><p>A key/value pair consisting of the link name and the link itself in the following format:</p><p><code>mylink=http://my.link</code></p><p></p><p>If you need to send multiple then send a JSON body POST where the links are a dictionary of values.</p></td></tr><tr><td><code>commits</code></td><td></td><td>A list of commits to use instead of pulling the list of commits from the code repository. See the JSON schema for more details: <a href="https://app.sleuth.io/api/1/schema/register_deploy">https://app.sleuth.io/api/1/schema/register_deploy</a></td></tr><tr><td><code>files</code></td><td></td><td>A list of files included in the deploy, used instead of pulling the list of files from the commits. See the JSON schema for more details: <a href="https://app.sleuth.io/api/1/schema/register_deploy">https://app.sleuth.io/api/1/schema/register_deploy</a></td></tr><tr><td><code>pull_requests</code></td><td></td><td>A list of pull requests to use instead of pulling the list of pull requests from the code repository. See the JSON schema for more details: <a href="https://app.sleuth.io/api/1/schema/register_deploy">https://app.sleuth.io/api/1/schema/register_deploy</a></td></tr></tbody></table>
{% endtab %}

{% tab title="Responses" %}
<table><thead><tr><th width="112">Code</th><th width="269">Comments</th><th>Response Text</th></tr></thead><tbody><tr><td><mark style="color:green;"><strong><code>200</code></strong></mark></td><td>Deploy registered successfully.</td><td><code>Success</code></td></tr><tr><td><mark style="color:red;"><strong><code>400</code></strong></mark></td><td>Returned if any of the input parameters are invalid, e.g.:<br>- <code>sha</code> isn't provided<br>- branch doesn't match the configured branch<br>- <code>date</code> format isn't valid<br>- <code>author</code> is not a valid email<br>- we're unable to validate if the <code>sha</code> exists in the remote system</td><td><p>The response text will indicate the nature of the error:<br></p><p><code>String of message problem</code></p></td></tr><tr><td><mark style="color:red;"><strong><code>401</code></strong></mark></td><td>API key not valid or the deployment is not in the specified organization</td><td><code>String of message problem</code></td></tr></tbody></table>


{% endtab %}
{% endtabs %}



## Examples

{% hint style="warning" %}
Make sure you **replace the values** surrounded b&#x79;**`<`** and **`>`**&#x77;ith your **own values.**
{% endhint %}

<details>

<summary>cURL</summary>

<pre class="language-bash" data-overflow="wrap" data-line-numbers><code class="lang-bash"><strong>curl -X POST \
</strong>'https://app.sleuth.io/api/1/deployments/&#x3C;ORG_SLUG>/&#x3C;DEPLOYMENT_SLUG>/register_deploy' \
  -H 'Authorization: Bearer &#x3C;ACCESS_TOKEN>' \
  -H 'Content-Type: application/json' \
  -d '{
  "sha": "&#x3C;SHA>",
  "environment": "&#x3C;ENVIRONMENT>"
}'
</code></pre>

</details>

<details>

<summary>cURL with optional Tags</summary>

<pre class="language-bash" data-overflow="wrap" data-line-numbers><code class="lang-bash">curl -X POST \
'https://app.sleuth.io/api/1/deployments/&#x3C;ORG_SLUG>/&#x3C;DEPLOYMENT_SLUG>/register_deploy' \
  -H 'Authorization: Bearer &#x3C;ACCESS_TOKEN>' \
  -H 'Content-Type: application/json' \
  -d '{
  "sha": "&#x3C;SHA>",
  "environment": "&#x3C;ENVIRONMENT>",
  "tags": [
    "#tag1",
    "#tag2",
    "#tag3"
    ]
<strong>  }'
</strong></code></pre>

:information\_source: Please note that tags must start with the `#` symbol, must be separated with commas, and cannot contain the `.` symbol.

</details>

<details>

<summary>PowerShell</summary>

<pre class="language-powershell" data-overflow="wrap" data-line-numbers><code class="lang-powershell"><strong>Invoke-RestMethod -Method POST `
</strong><strong>-Uri 'https://app.sleuth.io/api/1/deployments/&#x3C;ORG_SLUG>/&#x3C;DEPLOYMENT_SLUG>/register-deploy' `
</strong><strong>-Headers @{
</strong><strong>      'Authorization' = 'Bearer &#x3C;ACCESS_TOKEN>'
</strong><strong>      'Content-Type' = 'application/json'
</strong>} `
-Body '{
      "environment": "&#x3C;ENVIRONMENT>",
      "sha": "&#x3C;SHA>" 
 }'
</code></pre>

</details>

<details>

<summary>cURL using Custom Git</summary>

{% code overflow="wrap" lineNumbers="true" %}
```bash
curl -X POST -v \
'https://app.sleuth.io/api/1/deployments/<ORG_SLUG>/<DEPLOYMENT_SLUG>/register_deploy' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
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
