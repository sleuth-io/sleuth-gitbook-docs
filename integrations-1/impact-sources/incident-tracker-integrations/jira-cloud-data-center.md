# Jira (Cloud/Data Center)

## About the integration <img src="../../../.gitbook/assets/jira-software-2x-blue (1).png" alt="" data-size="line">

The Jira incident integration allows Sleuth to use Jira (Cloud and Datacenter) as a source for incidents.

## Setting up the integration

Follow instructions for [Jira Cloud](../../issue-trackers/jira.md#setting-up-the-integration) or [Jira Datacenter](../../issue-trackers/jira-datacenter.md#setting-up-the-integration) to establish the integration. Note that if you already added the integration to track your issues, you do **not** need to create another integration - Sleuth will use already existing one to also track incidents.



## Configuring the integration

* Click **Add incident source** and select a Sleuth project that will track Jira incidents. All projects within your organization will be displayed in the dropdown.

![](<../../../.gitbook/assets/Screenshot 2021-11-15 at 15.17.30.png>)

* Configure impact source by pasting JQL query that represents your **active incidents**. When an issue matching the query exists, Sleuth will treat this as an incident state to calculate Failure rate and MTTR

{% hint style="info" %}
Integrations are made at the Sleuth organization level and are available for all projects within that organization. Individual settings for integration are made at the project level.
{% endhint %}

* That's it! Sleuth will now start tracking incidents from Jira issues.





