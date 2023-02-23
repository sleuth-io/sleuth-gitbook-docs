# Jira Cloud

## About the integration ![](<../../.gitbook/assets/jira-software-2x-blue (1).png>)

The Jira integration allows Sleuth to use Jira Cloud as a deployment issue tracker. When you deploy, Sleuth will automatically connect your Jira issues to the deploys, so you can always find the source of your changes later. Direct links to related Jira projects are provided in the deploy cards, allowing you to quickly see the Jira issues that affect your deploys.

Integration with Jira Cloud is made at the Sleuth organization level. More than one [issue tracker](./) can be integrated with an organization. Although you can have multiple projects within an organization, each project can only configured to use a single issue tracker. Bitbucket, due to its own integration with Jira Cloud, can be used as one of those since Bitbucket can automatically connect to your Jira issues as long as both of those Atlassian products are both logged in with the same account. Bitbucket can also serve as a code deployment source change.

Once Jira Cloud is configured as the issue tracker, every time the Jira issue key is included in a deploy's commit message, Sleuth will automatically link that deploy with the corresponding issue in Jira Cloud.

{% hint style="info" %}
Check out the Sleuth for Jira integration [in the Atlassian Marketplace](https://marketplace.atlassian.com/apps/1223369/sleuth-for-jira?hosting=cloud\&tab=overview).
{% endhint %}

## Setting up the integration

To set up the Sleuth Jira Cloud integration:

1. Click your **avatar** in the top-right of the navigation bar and click **Integrations** in the **Organization** section.
2. In the **Jira Cloud** tile, click **Enable**.
3. Enter the **fully qualified URL** of your Jira Cloud instance, the authorized User's **Email**, and the corresponding **API Token** into the respective fields, then click **Save**. To quickly access your Jira Cloud instance to obtain an API token, click the **generate** link in the title.\
   ![](../../.gitbook/assets/image.png)

### Custom HTTP headers

If you using Jira on-premise behind Cloudflare access or similar, Sleuth might need to include some HTTP headers in order to reach your instance. In order to set Sleuth to send any custom HTTP headers when making requests:

1. In the Jira dialog, click on the **Advanced setting**
2. Enter comma separated list of custom headers you want Sleuth to include

![](<../../.gitbook/assets/image (2).png>)

## Using the integration

Setting up the Jira Cloud integration represents the groundwork for later issue tracking. To actually start tracking issues, you need to **configure your Projects** to use the integration for that purpose.

### To set Jira as the issue tracker on a Project:

1. Navigate to the Project you wish to use Jira as issue tracker with&#x20;
2. Click on **Settings** in the left sidebar, then select the **Details** tab.
3. Select your **Jira** **integration** from the list in the **Issue Integration Provider** dropdown. Please note that the integration must **** first be **set up** **at the organization level** before it can be selected.\
   \
   ![](<../../.gitbook/assets/image (1).png>)
4. Click **Save**.

{% hint style="info" %}
The **Issue Integration Provider** setting is defined on a **Project-level basis**, so it needs to be applied to **each Project individually**.
{% endhint %}

## Removing the integration

#### If you wish to disconnect the Jira Cloud integration for the organization:

1. Click your **avatar** in the top-right of the navigation bar and click **Integrations** in the **Organization** section.
2. In the **Jira Cloud** tile, click the **∨** symbol to expand the tile.
3. A list of all of your Jira connections should be displayed.
4. Click **Remove** for each of the connections you wish to remove.

Once a connection is removed, it is no longer available for any projects within the organization. Any projects that used that particular Jira Cloud connection will need to have a [new issue tracker connection or a completely different issue tracker selected](jira.md#to-set-jira-as-the-issue-tracker-on-a-project).

{% hint style="info" %}
The **integration is fully disconnected** once all Jira Cloud connections are removed.
{% endhint %}
