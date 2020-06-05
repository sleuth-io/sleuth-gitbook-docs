# Rollbar

## About the Integration ![](../../../.gitbook/assets/rollbar-mark-black.png) 

Rollbar is an error monitoring service that helps DevOps teams discover, triage, and prioritize their errors in real-time. Before you start, you should already have a Rollbar account and your environment setup and running. If not, head over to Rollbar to get things started. Once you're done, return to Sleuth so you can complete setup of the integration. 

To add the Sleuth Rollbar integration:

* Click **Integrations** in the sidebar.
* Click **connect** in the Rollbar Error Trackers card.
* Enter the Rollbar Auth Token, then press **Save**. 

{% hint style="info" %}
The Rollbar Auth Token can be found in Rollbar, under **Settings** &gt; **{Project Name} &gt; Members &gt; Owners &gt; Acount Access Tokens**, as shown below. **Do not use Project Access Tokens.** The Token must have at least `Read` and `Write` scopes enabled.   
  
[Get more information about Rollbar Account Access Tokens.](https://explorer.docs.rollbar.com/#section/Authentication/Account-Access-Tokens) ![](../../../.gitbook/assets/icon-link-27.png) 
{% endhint %}

![RollRollbar Account Access Tokens screen](../../../.gitbook/assets/rollbar-account-access-token-generate.png)

 

* Once the Rollbar integration is successful, you will see the message **Rollbar enabled** in the **Errors** integration card. 
* Click **Add impact** to select the Sleuth project that will be monitoring your application errors. All projects, regardless of which environment they're in, will be displayed in the Project dropdown. 

{% hint style="warning" %}
Sleuth will not auto-populate the **Environment** field dropdown due to the way the Sentry API handles environment data. Check your Sentry project first before populating this field. Environments are created when a deployed application monitored by Sentry sends environment data \(e.g., in Javascript, the application could send`environment: 'staging'`\) back to Sentry by tagging issues via your SDK.   
  
For more information,[ read more](https://docs.sentry.io/enriching-error-data/environments/?platform=browser#how-to-send-environment-data) about how Sentry receives environment data. 
{% endhint %}

![Impact entry dialog for Sentry](../../../.gitbook/assets/sentry-impact-source-entry.png)

{% hint style="info" %}
Integrations are made at the Sleuth organization level, and are available for all projects within that organization. Individual settings for an integration are made at the project level.  
{% endhint %}

* The Sentry logo in the Change Source card turns to green when the integration is successful. 

{% hint style="info" %}
Click **disconnect** to dissolve the Sleuth-Sentry integration. You will need to re-authorize Sleuth again if you wish to re-establish the integration.
{% endhint %}

* That’s it—Sleuth will start displaying Sentry error metrics in your deploys. Read [**Dashboard**](../../../dashboard.md) for more information on how errors are communicated in deploy cards. 

