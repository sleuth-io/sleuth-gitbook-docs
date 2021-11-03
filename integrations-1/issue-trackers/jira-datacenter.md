# Jira Data Center/Server

## About the integration ![](<../../.gitbook/assets/jira-software-2x-blue (1).png>) 

The Jira Data Center integration allows Sleuth to use Jira Data Center as a deployment issue tracker. When you deploy, Sleuth will automatically connect your Jira Data Center issues to the deploys, so you can always find the source of your changes later. Direct links to related Jira Data Center projects are provided in the deploy cards, allowing you to quickly see the Jira issues that affect your deploys. 

Integration with Jira Data Center is made at the Sleuth organization level. More than one [issue tracker](./) can be integrated with an organization. Although you can have multiple projects within an organization, each project can only configured to use a single issue tracker. Bitbucket, due to its own integration with Jira Data Center, can be used as one of those since Bitbucket can automatically connect to your Jira Data Center issues as long as both of those Atlassian products are both logged in with the same account. Bitbucket can also serve as a code deployment source change. 

Once Jira Data Center is configured as the issue tracker, every time the Jira issue key is included in a deploy's commit message, Sleuth will automatically link that deploy with the corresponding issue in Jira Data Center.

{% hint style="info" %}
Check out the Sleuth for Jira integration [in the Atlassian Marketplace](https://marketplace.atlassian.com/apps/1223369/sleuth-for-jira?hosting=cloud\&tab=overview). 
{% endhint %}

## Setting up the integration

To set up the Sleuth Jira Data Center integration:

1. Click **Integrations** in the left sidebar, then click **Issue Trackers**. 
2. In the _Jira Data Center_ tile, click **enable**. 
3. Enter the _API Token_, _Email_, and fully qualified _URL_ of your Jira Data Center instance into the corresponding fields, then press **Save**. To quickly access your Jira Data Center instance to obtain an API token, click **generate**. \
    ![](../../.gitbook/assets/screenshot-from-2021-08-23-16-37-29.png) 
4. The message **Jira enabled** is displayed in the tile.

![Successful integration!](../../.gitbook/assets/screen-shot-2020-06-02-at-3.05.34-pm.png)

## Configuring the integration

After setting up the Jira Data Center integration, you must designate which Sleuth project to use as the default issue tracker. If you are configuring the integration immediately after setting it up, you can go directly to step #2 below. 

### To set the default issue tracker: 

1. Click on **Integrations** in the left sidebar, then on **Issue Trackers**. 
2. Click on the Jira Data Center **Set default issue tracker** dropdown (see screenshot above).
3. All projects in the organization are displayed. Select which project you'd like to set Jira Data Center as the default issue tracker for. 

You can also change the default issue tracker at any time. 

### To change the default issue tracker: 

1. Click on **Project Settings** in the left sidebar, then select **Details**. 
2. Select a new default issue tracker. The integration **must be connected** at the organization level before it can be selected.\
    ![](../../.gitbook/assets/jira-default-issue-tracker.png) 
3. Press **Save**. 

## Removing the integration

#### If you wish to disconnect the Jira Data Center integration for the organization: 

1. Click on **Integrations** in the left sidebar, then on **Issue Trackers**. 
2. Click **disable**. The message **Jira disabled** is displayed in the Jira Data Center integration card once the integration is dissolved.

The Jira Data Center integration is disconnected and no longer available to any projects within that organization. Any projects that used the Jira Data Center integration will need a new default issue tracker selected. 

#### To set a new default issue tracker: 

1. Click on **Project Settings** in the left sidebar, then select **Details**. 
2. Select a new default issue tracker. The integration must be connected via the organization before it's displayed here. 
3. Press **Save**.

The Jira Data Center integration is disconnected and no longer available to any projects within that organization. You will need to select a new default issue tracker for any projects that used the Jira Data Center integration. Simply follow the instructions in the section above: **To set a new default issue tracker**. 
