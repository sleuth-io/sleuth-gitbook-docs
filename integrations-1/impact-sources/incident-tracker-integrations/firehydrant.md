# FireHydrant

## About the integration <img src="../../../.gitbook/assets/firehydrant-logo.png" alt="" data-size="line">

FireHydrant takes care of alert handoff, automating incident declaration, and management process. Integrating FireHydrant with Sleuth is simple using a [dedicated bot user](https://app.firehydrant.io/organizations/bots).

## Setting up the integration

To add the Sleuth FireHydrant integration:

* Click **Integrations** in the top right menu.
* Search for FireHydrant and enable.
* Enter your Bot API token.
* Press **Save**.

## Configuring the integration

* Navigate to the desired project and click **Add Impact Source**.

![](<../../../.gitbook/assets/image (5) (2) (2).png>)

* Configure impact source by mapping incidents FireHydrant's environment and service to Sleuth environment.
* Under advanced settings, you can control the historic data population. If checked Sleuth will populate all incidents that happened in the last 30 days and recalculate the project's Failure Rate and MTTR metrics.

{% hint style="info" %}
Integrations are made at the Sleuth organization level and are available for all projects within that organization. Individual settings for integration are made at the project level.
{% endhint %}

* That's it! Sleuth will now start tracking incidents declared in FireHydrant.
