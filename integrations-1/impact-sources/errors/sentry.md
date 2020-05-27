# Sentry

## About the Integration ![](../../../.gitbook/assets/sentry-glyph-dark.png) 

Sentry is an error monitoring service that helps DevOps teams discover, triage, and prioritize their errors in real-time. 

Before you start, you should already have a Sentry account, and your environment setup and running. If not, head over to [Sentry](https://sentry.io/signup/) to get things started. 

To add the Sentry integration:

* Click **Integrations** in the sidebar.
* Click **connect** in the Sentry Error Trackers card.
* Enter the Sentry Auth Token, then press **Save**. 

{% hint style="info" %}
The Sentry Auth Token can be found in Sentry, under **Settings &gt; Account Details &gt; API &gt; Auth Token**. ****
{% endhint %}

 

![](../../../.gitbook/assets/sentry-auth-token-screen.png)

![](../../../.gitbook/assets/sentry-auth-token-enter-dialog.png)

* Once the Sentry integration is successful, you will see the message, "Sentry is connected" displayed. 
* Click **Add impact** to select the Sentry project that will be monitoring your application errors. All projects, regardless of which Sentry environment they're in, will be displayed in the 

![](../../../.gitbook/assets/sentry-enable-success.png)

![Impact entry dialog for Sentry](../../../.gitbook/assets/sentry-impact-source-entry.png)

{% hint style="info" %}
Integrations are made at the Sleuth organization level, and are available for all projects within that organization. Individual settings for an integration are made at the project level.  
{% endhint %}

* The Sentry logo in the Change Source card turns to green when the integration is successful. 

{% hint style="info" %}
Click **disconnect** to dissolve the Sleuth-Sentry integration. You will need to re-authorize Sleuth again if you wish to re-establish the integration.
{% endhint %}

* That’s it—Sleuth will start displaying Sentry error metrics in your deploys. Read [**Dashboard**](../../../dashboard.md) for more information on how errors are communicated in your Project’s deploy cards. 

