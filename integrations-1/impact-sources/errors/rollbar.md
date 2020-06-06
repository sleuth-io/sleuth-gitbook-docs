# Rollbar

## About the Integration ![](../../../.gitbook/assets/rollbar-mark-black.png) 

Rollbar is an error monitoring service that helps DevOps teams automate error monitoring and triaging. Before you start, you should already have a [Rollbar](https://rollbar.com/signup/) account and your environment setup and running. If not, head over to Rollbar to get things started. Once you're done, return to Sleuth so you can complete setup of the integration. 

## Setting up the integration

To add the Sleuth Rollbar integration:

* Click **Integrations** in the sidebar.
* Click **connect** in the Rollbar Error Trackers card.
* Enter the Rollbar Auth Token, then press **Save**. 

{% hint style="info" %}
The Rollbar Auth Token can be found in Rollbar, under **Settings** &gt; **{Project Name} &gt; Members &gt; Owners &gt; Acount Access Tokens**, as shown below. **Do not use Project Access Tokens.** The Token must have at least `Read` and `Write` scopes enabled.   
  
[Get more information about Rollbar Account Access Tokens.](https://explorer.docs.rollbar.com/#section/Authentication/Account-Access-Tokens) ![](../../../.gitbook/assets/icon-link-27.png) 
{% endhint %}

![Rollbar Account Access Tokens screen](../../../.gitbook/assets/rollbar-account-access-token-generate.png)

## Configuring the integration

* Once the Rollbar integration is successful, you will see the message **Rollbar enabled** in the **Errors** integration card. 
* Click **Add impact** to select the Sleuth project that will be processing your application errors. All projects within the organization will be displayed in the dropdown. 

{% hint style="info" %}
Integrations are made at the Sleuth organization level, and are available for all projects within that organization. Individual settings for an integration are made at the project level.  
{% endhint %}

{% hint style="info" %}
Click **disconnect** to dissolve the Sleuth-Rollbar integration. You will need to re-authorize Sleuth again if you wish to re-establish the integration.
{% endhint %}

* That’s it—Sleuth will start displaying Rollbar error metrics in your deploys. Read [**Dashboard**](../../../dashboard.md) for more information on how errors are commun~~i~~cated in deploy cards. 

## Removing the integration

#### If you wish to dissolve the Rollbar integration for the organization: 

1. Click on **Integrations** in the left sidebar, then on **Error Trackers**. 
2. In the Rollbar integration card, click **disconnect**.

The Rollbar integration is disconnected and no longer available to any projects within that organization.  Other error trackers that may be connected to your organization are not affected. 

#### If you wish to edit the Rollbar integration for project: 

1. Select the **project** in the project selector in the sidebar. 
2. Click on **Project Settings** in the sidebar. 
3. Click on **Impact**.
4. Click **edit** on the impact source you wish to delete or edit.  
5. Edit the _Name_, _Project_, and/or _Environment_ settings, then press **Save**. 

{% hint style="info" %}
The _Projects_ dropdown is automatically populated with the list of projects in the connected Rollbar account. The _Environment_ field is not validated, but should match the environment values in your Rollbar settings. [Read the Rollbar documentation on Environments](https://docs.rollbar.com/docs/environments) for more information. 
{% endhint %}

