# Jira

## About the integration ![](../../.gitbook/assets/jira-software-2x-blue%20%281%29.png) 

The Jira integration allows Sleuth to use Jira as a deployment issue tracker. When you deploy, Sleuth will automatically connect your Jira issues to the deploys, so you can always find the source of your changes later. Direct links to related Jira projects are provided in the deploy cards, allowing you to quickly see the Jira issues that affect your deploys. 

Integration with Jira is made at the Sleuth organization level. More than one [issue tracker](./) can be integrated with an organization. Although you can have multiple projects within an organization, each project can only configured to use a single issue tracker. Bitbucket, due to its own integration with Jira, can be used as one of those since Bitbucket can automatically connect to your Jira issues as long as both of those Atlassian products are both logged in with the same account. Bitbucket can also serve as a code deployment source change. 

Once Jira is configured as the issue tracker, every time the Jira issue key is included in a deploy's commit message, Sleuth will automatically link that deploy with the corresponding issue in Jira.

{% hint style="info" %}
Check out the Sleuth for Jira integration [in the Atlassian Marketplace](https://marketplace.atlassian.com/apps/1223369/sleuth-for-jira?hosting=cloud&tab=overview). 
{% endhint %}

## Setting up the integration

To set up the Sleuth Jira integration:

1. Click **Integrations** in the left sidebar, then click **Issue Trackers**. 
2. In the _Jira_ tile, click **enable**. 
3. Enter the _API Token_, _Username_, and fully qualified _URL_ of your Jira instance into the corresponding fields, then press **Save**. To quickly access your Jira instance to obtain an API key, click **generate**.   ![](../../.gitbook/assets/jira-api-key-generate.png) 
4. The message **Jira enabled** is displayed in the tile.

![Successful integration!](../../.gitbook/assets/screen-shot-2020-06-02-at-3.05.34-pm.png)

## Configuring the integration

After setting up the Jira integration, you must designate which Sleuth project to use as the default issue tracker. If you are configuring the integration immediately after setting it up, you can go directly to step \#2 below. 

### To set the default issue tracker: 

1. Click on **Integrations** in the left sidebar, then on **Issue Trackers**. 
2. Click on the Jira **Set default issue tracker** dropdown \(see screenshot above\).
3. All projects in the organization are displayed. Select which project you'd like to set Jira as the default issue tracker for. 

You can also change the default issue tracker at any time. 

### To change the default issue tracker: 

1. Click on **Project Settings** in the left sidebar, then select **Details**. 
2. Select a new default issue tracker. The integration **must be connected** at the organization level before it can be selected.  ![](../../.gitbook/assets/jira-default-issue-tracker.png) 
3. Press **Save**. 

## Removing the integration

#### If you wish to dissolve the Jira integration for the organization: 

1. Click on **Integrations** in the left sidebar, then on **Issue Trackers**. 
2. Click **disable**. The message **Jira disabled** is displayed in the Jira integration card once the integration is dissolved.

The Jira integration is disconnected and no longer available to any projects within that organization. Any projects that used the Jira integration will need a new default issue tracker selected. 

#### To set a new default issue tracker: 

1. Click on **Project Settings** in the left sidebar, then select **Details**. 
2. Select a new default issue tracker. The integration must be connected via the organization before it's displayed here. 
3. Press **Save**.

The Jira integration is disconnected and no longer available to any projects within that organization. You will need to select a new default issue tracker for any projects that used the Jira integration. Simply follow the instructions in the section above: **To set a new default issue tracker**. 

