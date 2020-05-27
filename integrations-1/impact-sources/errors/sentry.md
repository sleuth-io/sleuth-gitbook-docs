# Sentry

## About the Integration ![](../../../.gitbook/assets/sentry-glyph-dark.png) 

Sentry is an error monitoring service that helps DevOps teams discover, triage, and prioritize their errors in real-time. 

Before you start, you should already have a Sentry account, and your environment setup and running. If not, head over to [Sentry](https://sentry.io/signup/) to get things started. 

To add the Sentry integration:

* Click **Integrations** in the sidebar.
* Click **enable** in the Sentry Error Trackers card.

{% hint style="info" %}
Integrations are made at the Sleuth organization level, and are available for all projects within that organization. Individual settings for an integration are made at the project level.  
{% endhint %}

* The Sentry logo in the Change Source card turns to green when the integration is successful. 

![](../../../.gitbook/assets/screen-shot-2020-03-31-at-3.52.19-pm.png)

{% hint style="info" %}
Click **disconnect** to dissolve the Sleuth-LaunchDarkly integration. You will need to re-authorize Sleuth again if you wish to re-establish the integration.
{% endhint %}

* That’s it—Sleuth will now track your feature flags as a source of change. Read [**Dashboard**](../../../dashboard.md) for more information on how feature flag issues are communicated in your Project’s deploy cards. 

