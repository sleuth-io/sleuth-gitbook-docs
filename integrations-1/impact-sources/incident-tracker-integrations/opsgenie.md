# Opsgenie

## About the integration&#x20;

Opsgenie is an on-call and alert management tool. Integrating Opsgenie with Sleuth is simple using an API token.

## Setting up the integration

To add the Sleuth Opsgenie integration:

* Click **Integrations** in the sidebar.
* Click the _Incidents_ tab, then **add** in the _Opsgenie_ card.
* Enter your API token. Ensure the token has `Read` and `Configuration Access` scopes
* If your Opsgenie instance is in Europe, enable _My Opsgenie servers are in the EU_ checkbox. Leave this unchecked if you are unsure.
* Press **Save**.

## Configuring the integration

* Click **Add incident source** and select a Sleuth project that will track Opsgenie incidents. All projects within your organization will be displayed in the dropdown.

![](<../../../.gitbook/assets/Screenshot 2022-01-13 at 09.31.29.png>)

* Configure impact source first by marking if Sleuth should track Opsgenie alerts or incidents.
* If impact source will be tracking incidents  (did not enable the option to track alerts), you can filter incidents by affected service.
* Configure minimum priority threshold. Any alert or incident that will have equal or higher priority will be considered a failure in Sleuth.
* Under advanced settings, you can control the historic data population. If checked Sleuth will populate all incidents that happened in the last 30 days and recalculate the project's Failure Rate and MTTR metrics.

{% hint style="info" %}
Integrations are made at the Sleuth organization level and are available for all projects within that organization. Individual settings for integration are made at the project level.
{% endhint %}

* That's it! Sleuth will now start tracking incidents or alerts affecting the selected service declared in Opsgenie.
