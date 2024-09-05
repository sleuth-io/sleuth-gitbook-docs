---
description: Use this endpoint to import deploys using a CSV file.
---

# Deploy import

Delete all existing deploys in your Code Deployment and create a new history with only the deploys you specify via a CSV file. This might be useful if you wish to populate more than the default 28-days' worth of data when creating a new Code Deployment in Sleuth, or when you want to only import specific deploys, and don't want to register them individually.

## Path

{% hint style="info" %}
#### ENDPOINT&#x20;

https://app.sleuth.io/api/1/deployments/<mark style="color:red;">`ORG_SLUG`</mark>_/<mark style="color:blue;">`DEPLOYMENT_SLUG`</mark>_/import\_deploys
{% endhint %}

The endpoint path takes **2 slugs** which direct the deploys to the correct code deployment:

* <mark style="color:red;">`ORG_SLUG`</mark>: found in the URL of your Sleuth org, immediately following `https://app.sleuth.io/`
* <mark style="color:blue;">`DEPLOYMENT_SLUG`</mark>: found in the URL, following the prefix `https://app.sleuth.io/org_slug/deployments/`



## Parameters

{% tabs %}
{% tab title="Mandatory parameters" %}
<table><thead><tr><th width="198">Name</th><th width="111">Type</th><th>Comments</th></tr></thead><tbody><tr><td><code>api_key</code><mark style="color:red;">*</mark></td><td>string</td><td>Can be found in the <code>Organization Settings</code> -> <code>Details</code> -> <code>Api Key</code> field in your Sleuth org.</td></tr><tr><td><code>csv_file</code><mark style="color:red;">*</mark></td><td>file</td><td>The attached CSV file containing the list of deploys to import.</td></tr><tr><td><code>environment</code></td><td>string</td><td>The Sleuth environment slug. Defaults to the primary environment of the project.</td></tr></tbody></table>
{% endtab %}

{% tab title="Responses" %}
<table><thead><tr><th width="112">Code</th><th width="269">Comments</th><th>Response Text</th></tr></thead><tbody><tr><td><mark style="color:green;"><strong><code>200</code></strong></mark></td><td>Deploys imported successfully.</td><td><code>Success</code></td></tr><tr><td><mark style="color:red;"><strong><code>400</code></strong></mark></td><td>Returned if any of the input parameters are invalid, e.g.:<br>- <code>sha</code> isn't provided<br>- branch doesn't match the configured branch<br>- <code>date</code> format isn't valid<br>- <code>author</code> is not a valid email<br>- we're unable to validate if the <code>sha</code> exists in the remote system</td><td><p>The response text will indicate the nature of the error:<br></p><p><code>String of message problem</code></p></td></tr><tr><td><mark style="color:red;"><strong><code>401</code></strong></mark></td><td>API key not valid or the deployment is not in the specified organization</td><td><code>String of message problem</code></td></tr></tbody></table>
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
Importing deploys into a pre-populated code deployment will **delete all existing deploys** in that code deployment and **create a new history** with only the deploys specified in the CSV file.&#x20;
{% endhint %}

## CSV File Structure

The deploys should be imported using a **CSV file** that is uploaded as part of the request. The CSV file should contain the headers `sha` and `date`, the `sha` column should contain the **full SHA** of the commits at the point of release, and the `date` column should contain the **date and time** of the deploy in the [ISO 8601](https://en.wikipedia.org/wiki/ISO\_8601) format.

{% code title="Example CSV file" lineNumbers="true" %}
```csv
sha,date 
3c02378,2002-04-03T08:34:02 
6f0d7cf,2002-04-01T15:03:55
```
{% endcode %}

## Examples

{% hint style="warning" %}
Make sure you **replace the values** surrounded by**`<`** and **`>`**with your **own values**. Adjust the `csv_file` path accordingly or run the command from the directory that contains the `csv_file`.
{% endhint %}

{% hint style="warning" %}
When using the Organization API token found under **Organization Settings > Details**, the `Authorization` header needs to pass the API key via `apikey` e.g. `Authorization: apikey <APIKEY>`

When using API tokens created under **Organization Settings > Access Tokens** the `Authorization` header needs to pass the API token via `Bearer` e.g. `Authorization: Bearer <API_TOKEN>`
{% endhint %}

<details>

<summary>cURL with API key in Header</summary>

{% code overflow="wrap" lineNumbers="true" %}
```bash
curl \
'https://app.sleuth.io/api/1/deployments/<ORG_SLUG>/<DEPLOYMENT_SLUG>/import_deploys' \
  -H 'Authorization: apikey <APIKEY>' \
  -F 'csv_file=@<FILENAME>.csv'
```
{% endcode %}

</details>

<details>

<summary>cURL with API key in Body</summary>

{% code overflow="wrap" lineNumbers="true" %}
```bash
curl \
'https://app.sleuth.io/api/1/deployments/<ORG_SLUG>/<DEPLOYMENT_SLUG>/import_deploys' \
  -F 'api_key=<API_KEY>' \
  -F 'csv_file=@<FILENAME>.csv'
```
{% endcode %}

</details>
