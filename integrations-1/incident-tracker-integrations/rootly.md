# Rootly

## About the integration

Rootly is a cloud-based incident management tool. This integration allows Sleuth to source incident data from Rootly and evaluate how those incidents impact the overall health of your deploys.

## Enabling the integration (Organization-level)

To set up the the Rootly integration, you'll first need to enable it globally (i.e. for your Sleuth Organization).&#x20;

{% hint style="info" %}
Integrations are enabled at the Sleuth Organization level and are then available for all Projects within your Organization. Project-level settings for impact integrations are configured by adding an Impact Source to one or more Sleuth Projects. Project-level configuration for Rootly Impact Sources is covered in the next section.
{% endhint %}

To enable the Rootly integration for your Organization, perform the following steps:

* Click **Integrations** in Sleuth's left-hand sidebar.
* Select **Incident** from the drop-down to filter the list of available integrations (optional).
* Locate the _Rootly_ card and click **Enable**
* Next, you'll need to enter a service-level Rootly API key to authenticate the connection. If you don't already have that key handy, click **generate** to navigate directly to Rootly's API keys management page, where you can generate a new API token or retrieve an existing one.

<figure><img src="../../.gitbook/assets/image (6) (3) (1).png" alt=""><figcaption></figcaption></figure>

## Configuring the integration (Project-level)

In order to leverage the Rootly integration within a given Sleuth Project, you'll need to add a Rootly Impact Source to that Project, where you can specify the unique filter criteria that will determine which specific Rootly incidents Sleuth will associate with that Project.&#x20;

To add Rootly as an Impact Source for a specific Project, perform the following steps:

* From the left-hand-navigation panel, select the Project to which you'd like to add a new Rootly Impact Source
* Expand the **More** drawer, click **+ Add**, and select **Impact Source**
* In the **How do you track change failure** drop-down, leave the default selection in place:  _Incident management (recommended)_
* Under the **Choose your service** heading, select the _Rootly_ tile.&#x20;
* Click **Enable and continue**
* Provide a **Name** for your new Impact Source. Note that you might need to add multiple Rootly Impact Sources to cover all of the desired filter criteria combinations that you'd like to include in the Project
* Configure the Impact Source by selecting the desired filters for the Rootly incident attributes that you would like to include in this Project.&#x20;
  * The **Remote Severity** filter will include all Rootly Incidents with a Severity _greater than or equal to_ the selected value. Note that the **Remote Severity** drop-down presents Rootly's 4 static, back-end Severity categories. If you've configured custom Severity values in Rootly, you can view how those custom values map back to Rootly's four canonical Severity levels by visiting Rootly's [Severity configuration page](https://rootly.com/account/severities)&#x20;
  * The **Remote Team**, **Remote Service**, and **Remote Environment** filters are currently single-select, so if you'd like to include additional values for either attribute, you can do so by adding additional Rootly Impact Sources to the Project.
* Under **Advanced Settings**, you can control historical data population. If checked, Sleuth will populate all incidents that happened in the last 30 days and recalculate the project's Failure Rate and MTTR metrics.
* Click **Test Connection** to validate that the new Impact Source is returning the expected incidents from Rootly.
* Click **Save**

## Viewing Rootly Incidents in Sleuth

Once you've configured a Rootly Impact Source, you'll see that Impact Source and its health status listed on each new Deploy within the Project (as well as for the last 30 days of Deploys if you selected that option in the Rootly Impact Source).

You can also open the Rootly Impact Source to view a timeline chart showing all Rootly incidents from the last 14 days (and their health status).
