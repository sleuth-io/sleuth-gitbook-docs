# SignalFx

## About the integration

SignalFx is an metric monitoring service that helps DevOps teams discover, triage, and prioritize their errors in real-time. Before you start, you should already have a SignalFx account and your environment setup and running. If not, head over to SignalFx to get things started. Once you're done, return to Sleuth so you can complete setup of the integration. 

## Setting up the integration

To add the Sleuth SignalFx integration:

* Click **Integrations** in the sidebar.
* Click the _Metric Trackers_ tab, then **enable** in the SignalFx card.
* Enter your SignalFx API Key and Application Key in the corresponding fields.  
* Press **Save**. 

{% hint style="info" %}

{% endhint %}

 

* Once the SignalFx integration is successful, you will see the message **SignalFx is connected** displayed \(as shown below\). 

## Configuring the integration

* Click **Add impact** to select the Sleuth project that will be processing your application metrics. All projects within the organization will be displayed in the dropdown. 

![Impact entry dialog for SignalFx](../../../.gitbook/assets/sentry-impact-source-entry.png)

{% hint style="info" %}
Integrations are made at the Sleuth organization level, and are available for all projects within that organization. Individual settings for an integration are made at the project level.  
{% endhint %}

* The SignalFx logo in the Change Source card turns to green when the integration is successful. 

That’s it—Sleuth will start displaying SignalFx metrics in your deploys. Read [**Dashboard**](../../../dashboard/) for more information on how metrics are communicated in deploy cards. 

## Removing the integration

#### To dissolve the SignalFx integration for the organization: 

1. Click on **Integrations** in the left sidebar, then on **Metric Trackers**. 
2. In the SignalFx integration card, click **disable**.

The SignalFx integration is disconnected and no longer available to any projects within that organization. Any project-level modifications you made to the SignalFx integration will be lost.

