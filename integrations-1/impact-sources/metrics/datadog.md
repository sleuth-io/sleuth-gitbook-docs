# Datadog

## About the integration

Datadog is an metric monitoring service that helps DevOps teams discover, triage, and prioritize their errors in real-time. Before you start, you should already have a Datadog account and your environment setup and running. If not, head over to Datadog to get things started. Once you're done, return to Sleuth so you can complete setup of the integration. 

## Setting up the integration

To add the Sleuth Datadog integration:

* Click **Integrations** in the sidebar.
* Click the _Metric Trackers_ tab, then **enable** in the Datadog card.
* Enter your Datadog API Key and Application Key in the corresponding fields. 
* If your Datadog servers' are in the EU, enable the _My Datadog servers are in the EU_ checkbox. Leave this unchecked if you are unsure.  
* Press **Save**. 

{% hint style="info" %}
The Datadog API Key and Application Key can be found under **Integrations** &gt; **API**, as shown below. Or, you can click on the **generate** link, which will take you directly to the APIs page in your Datadog console, where you can then generate the keys Sleuth needs to complete the integration.  
{% endhint %}

 

![The API Keys section of the Datadog control panel](../../../.gitbook/assets/datadog.png)

![API and Application Key entry in Sleuth](../../../.gitbook/assets/datadog-integration-api-key.png)

* Once the Datadog integration is successful, you will see the message **Datadog is connected** displayed \(as shown below\). 

![](../../../.gitbook/assets/datadog-integration.png)

## Configuring the integration

* Click **Add impact** to select the Sleuth project that will be processing your application metrics. All projects within the organization will be displayed in the dropdown. 

![Impact entry dialog for Datadog](../../../.gitbook/assets/sentry-impact-source-entry.png)

{% hint style="info" %}
Integrations are made at the Sleuth organization level, and are available for all projects within that organization. Individual settings for an integration are made at the project level.  
{% endhint %}

* The Datadog logo in the Change Source card turns to green when the integration is successful. 

That’s it—Sleuth will start displaying Datadog metrics in your deploys. Read [**Dashboard**](../../../dashboard.md) for more information on how metrics are communicated in deploy cards. 

## Removing the integration

#### To dissolve the **Datadog** integration for the organization: 

1. Click on **Integrations** in the left sidebar, then on **Metric Trackers**. 
2. In the Datadog integration card, click **disable**.

The Datadog integration is disconnected and no longer available to any projects within that organization. Any project-level modifications you made to the Datadog integration will be lost.

