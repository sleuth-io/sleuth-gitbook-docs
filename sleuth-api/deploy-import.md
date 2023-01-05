---
description: Use this endpoint to import deploys using a CSV file.
---

# Deploy import

Delete all existing deploys in your Code Deployment and create a new history with only the deploys you specify via a CSV file. This might be useful if you wish to populate more than the default 28-days' worth of data when creating a new Code Deployment in Sleuth, or when you want to only import specific deploys, and don't want to register them individually.

## Path

{% hint style="info" %}
#### ENDPOINT ****&#x20;

https://app.sleuth.io/api/1/deployments/<mark style="color:red;">`ORG_SLUG`</mark>_/<mark style="color:blue;">`DEPLOYMENT_SLUG`</mark>_/import\_deploys
{% endhint %}

The endpoint path takes **2 slugs** which direct the deploys to the correct code deployment:

* <mark style="color:red;">`ORG_SLUG`</mark>: found in the URL of your Sleuth org, immediately following `https://app.sleuth.io/`
* <mark style="color:blue;">`DEPLOYMENT_SLUG`</mark>: found in the URL, following the prefix `https://app.sleuth.io/org_slug/deployments/`

``

## Parameters

{% tabs %}
{% tab title="Mandatory parameters" %}
| Name                                         | Type   | Comments                                                                                        |
| -------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| `api_key`<mark style="color:red;">\*</mark>  | string | Can be found in the `Organization Settings` -> `Details` -> `Api Key` field in your Sleuth org. |
| `csv_file`<mark style="color:red;">\*</mark> | file   | The attached CSV file containing the list of deploys to import.                                 |
| `environment`                                | string | The Sleuth environment slug. Defaults to the primary environment of the project.                |
{% endtab %}

{% tab title="Responses" %}
| Code                                        | Comments                                                                                                                                                                                                                                                                                                                         | Response Text                                                                                                                 |
| ------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:green;">**`200`**</mark> | Deploys imported successfully.                                                                                                                                                                                                                                                                                                   | `Success`                                                                                                                     |
| <mark style="color:red;">**`400`**</mark>   | <p>Returned if any of the input parameters are invalid, e.g.:<br>- <code>sha</code> isn't provided<br>- branch doesn't match the configured branch<br>- <code>date</code> format isn't valid<br>- <code>author</code> is not a valid email<br>- we're unable to validate if the <code>sha</code> exists in the remote system</p> | <p>The response text will indicate the nature of the error:<br><code></code></p><p><code>String of message problem</code></p> |
| <mark style="color:red;">**`401`**</mark>   | API key not valid or the deployment is not in the specified organization                                                                                                                                                                                                                                                         | `String of message problem`                                                                                                   |
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
