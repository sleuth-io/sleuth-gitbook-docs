# Statuspage

## About the integration <img src="../../../.gitbook/assets/statuspage_logo.svg" alt="" data-size="line">

Statuspage can easily communicate real-time status to your users. Integrating Statuspage with Sleuth is simple using an API token.

## Setting up the integration

To add the Sleuth Statuspage integration:

* Click **Integrations** in the sidebar.
* Click the _Incidents_ tab, then **add** in the _Statuspage_ card.
* Enter your API token
* Press **Save**.

## Configuring the integration

* Click **Add incident source** and select a Sleuth project that will track Statuspage incidents. All projects within your organization will be displayed in the dropdown.

![](<../../../.gitbook/assets/Screenshot 2021-11-02 at 15.01.46.png>)

* Configure impact source by mapping incidents Statuspage's page and component to Sleuth environment.
* Under advanced settings, you can control the historic data population. If checked Sleuth will populate all incidents that happened in the last 30 days and recalculate the project's Failure Rate and MTTR metrics.

{% hint style="info" %}
Integrations are made at the Sleuth organization level and are available for all projects within that organization. Individual settings for integration are made at the project level.
{% endhint %}

* That's it! Sleuth will now start tracking incidents for pages and components declared in Statuspage.
