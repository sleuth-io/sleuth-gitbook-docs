# Jira metrics (Cloud / Data Center)

## About the integration

Jira is an issue tracking tool that integrates with Sleuth in support of various use cases (as a general [deployment tracking issue integration](../../issue-trackers/jira.md), as an [incident impact source](../../incident-tracker-integrations/jira-cloud-data-center.md), etc.). This article is specific to using Jira as a _**metric impact source**_, which allows you to define a JQL query that returns a count of matching Jira issues and compare those against user-defined environment health thresholds. A common example here would be retuning the number of currently open bug tickets in Jira as an indicator of health. &#x20;

## Setting up the Jira integration for your Sleuth organization

If you've already set up the Jira integration for your Sleuth organization in support of any of the aforementioned use cases, you can skip ahead to [Configuring Jira as a Metric Impact Source](https://app.gitbook.com/o/-M1gHTBLHOo121mCa7Tk/s/-M1bR\_-Od0islbiOl4G0/\~/changes/702/integrations-1/impact-sources/metrics/datadog-1#configuring-jira-as-a-metric-impact-source) below.&#x20;

Otherwise, follow instructions for [Jira Cloud](../../issue-trackers/jira.md#setting-up-the-integration) or [Jira Datacenter](../../issue-trackers/jira-datacenter.md#setting-up-the-integration) to establish the integration, and then proceed to the next section to configure the impact source.

## Configuring Jira as a Metric Impact Source

Once the Jira integration has been enabled for your Sleuth organization, perform the following steps to configure it as a Metric impact source.

* Navigate to the Sleuth Project for which you'd like to add Jira as a metric impact source.
* From the Project's left-hand menu, click **Impact sources** and select **+ Add impact source**![](<../../../.gitbook/assets/image (30).png>)
* In the field titled **How do you track change failure?**, select **Metrics**
*   If the Jira integration has been properly enabled for your Sleuth organization, the integration tile will show "enabled". \


    <figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>
* Click the tile to configure the Jira metric impact source.
*   In the following screen, give your metric impact source a name, specify which environment it's for, and enter a JQL query that returns a count.\


    <figure><img src="../../../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>
* Optionally, under **Advanced settings**, you can specify a threshold under which the count returned by the metric impact source will be considered healthy.![](<../../../.gitbook/assets/image (3).png>)
* Test the connection to verify it's retuning the expected counts, and click **Save**.&#x20;
*   That's it! Sleuth will now start verifying your deploys' health by tracking the values from your Jira metric. To view the new metric, simply choose your new impact source from the Project's left-hand navigation. \


    <figure><img src="../../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

## Removing the integration

#### To remove the Jira metric impact source from your Sleuth Project:

1. Open the metric impact source from the Project's left-hand navigation menu.
2.  Click the cog in the upper-left-hand side of the screen and click **Delete**

    <figure><img src="../../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>
