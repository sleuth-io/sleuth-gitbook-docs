# PagerDuty

## About the integration ![](../../.gitbook/assets/pagerduty-logo.png)

PagerDuty centralizes, simplifies, and automates your incident response process to help you resolve issues quickly and efficiently. Integrating PagerDuty with Sleuth is simple using OAuth2.

## Setting up the integration

To add the Sleuth PagerDuty integration:

* Click **Integrations** in the sidebar.
* Click the \_Incidents \_tab, then **enable** in the PagerDuty card.
* Select the PagerDuty account you want to use
* Upon successful integration, you'll see **PagerDuty enabled (Connected as \_\<PagerDuty user account>)**displayed in the PagerDuty tile. You'll next configure the impact sources.

![](<../../.gitbook/assets/screenshot-2021-10-05-at-15.10.07 (1) (1).png>)

## Configuring the integration

* Click **Add incident source** and select a Sleuth project that will track PagerDuty incidents. All projects within your organization will be displayed in the dropdown.
* Configure impact source by selecting desired PagerDuty services and urgencies to track with Sleuth.
* Under advanced settings, you can control the historic data population. If checked Sleuth will populate all incidents that happened in the last 30 days and recalculate the project's Failure Rate and MTTR metrics.

{% hint style="info" %}
Integrations are made at the Sleuth organization level and are available for all projects within that organization. Individual settings for integration are made at the project level.
{% endhint %}

* That's it! Sleuth will now start tracking incidents declared in PagerDuty.
