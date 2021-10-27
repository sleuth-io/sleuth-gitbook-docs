# Shortcut

## About the integration ![](../../.gitbook/assets/shortcut-logo.png)&#x20;

The Shortcut integration allows Sleuth to use Shortcut as a deployment issue tracker. When you deploy, Sleuth will automatically connect your Shortcut **stories** to the deploys, so you can always find the source of your changes later.&#x20;

Integration with Shortcut is made at the Sleuth organization level. More than one [issue tracker](./) can be integrated with an organization. Although you can have multiple projects within an organization, each project can only configured to use a single issue tracker.&#x20;

{% hint style="info" %}
Shortcut uses the term **story **as its standard unit of work. For Sleuth Documentation purposes and throughout the Sleuth application interface, the term **issue** is used instead, and is synonymous with **story**. Shortcut, similar to Jira, is an _issue_ tracker.&#x20;
{% endhint %}

## Setting up the integration

To set up the Sleuth Shortcut integration:

1. Click **Integrations** in the left sidebar, then click **Issue Trackers**.&#x20;
2. In the Shortcut tile, click **enable**.&#x20;
3. Enter the _API Token_ of your Shortcut instance into the corresponding field, then press **Save**. To quickly access your Shortcut instance to obtain an API token, click **generate**. \
   &#x20;![](<../../.gitbook/assets/Screenshot 2021-10-27 at 08.37.10.png>)&#x20;
4. When integration is successful, Shortcut** enabled** is displayed in the tile.\
   &#x20;![](<../../.gitbook/assets/Screenshot 2021-10-27 at 08.37.32.png>)&#x20;

## Configuring the integration

After setting up the Shortcut integration, you must designate which Sleuth project to use as the default issue tracker. If you are configuring the integration immediately after setting it up, you can go directly to step #2 below.&#x20;

### To set the default issue tracker:&#x20;

1. Click on **Integrations** in the left sidebar, then on **Issue Trackers**.&#x20;
2. Click on the Shortcut **Set default issue tracker** dropdown (see screenshot above).
3. All projects in the organization are displayed. Select which project you'd like to set Shortcut as the default issue tracker for.&#x20;

You can also change the default issue tracker at any time.&#x20;

### To change the default issue tracker:&#x20;

1. Click on **Project Settings** in the left sidebar, then select **Details**.&#x20;
2. Select a new default issue tracker. The integration **must be connected** at the organization level before it can be selected.\
   &#x20;![](<../../.gitbook/assets/Screenshot 2021-10-27 at 08.38.11.png>)&#x20;
3. Press **Save**.

### To set a new default issue tracker:&#x20;

1. Click on **Project Settings** in the left sidebar, then select **Details**.&#x20;
2. Select a new default issue tracker. The integration must be connected via the organization before it's displayed here.&#x20;
3. Press **Save**.

## Removing the integration

#### If you wish to dissolve the Jira integration for the organization:&#x20;

1. Click on **Integrations** in the left sidebar, then on **Issue Trackers**.&#x20;
2. In the Shortcut integration card, click **disable**. The message Shortcut** disabled** is displayed in the Shortcut integration card once the integration is dissolved.

The Shortcut integration is disconnected and no longer available to any projects within that organization. You will need to select a new default issue tracker for any projects that used the Shortcut integration. Simply follow the instructions in the section above: **To set a new default issue tracker**.&#x20;
