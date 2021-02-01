# GitHub

## About the integration ![](../../.gitbook/assets/github-mark-120px-plus.png)

Integrating GitHub with Sleuth is simple. If you're setting connecting to a personal GitHub repo, you just need your credentials. If you're part of a GitHub organization and aren't the owner, you will need permission to allow Sleuth to connect to the repo \(after you connect you'll be able to select individual private or public repositories\).

If you are using GitHub issues to track issues, Sleuth will automatically discover your referenced issues once the integration is configured. You can still use other [issue tracker integrations](../issue-trackers/) if you don't use GitHub issues.

{% hint style="info" %}
Check out the Sleuth app in the [GitHub marketplace](https://github.com/marketplace/sleuth-deployment-tracking).
{% endhint %}

## Setting up the integration

To set up the Sleuth GitHub integration: 

1. Click **Integrations** in the left sidebar, then click **Change Sources**. 
2. In the _GitHub_ tile, click **enable**. 
3. Sign in to your GitHub account. If enabled, enter your 2FA code and click **Verify**. Don't worry, you'll select the GitHub repo to connect to your Sleuth project later.   ![](../../.gitbook/assets/github-signin.png)  ![](../../.gitbook/assets/github-2fa.png) 
4. Upon successful integration, you'll see **GitHub enabled \(Connected as** _**&lt;GitHub user account&gt;**_**\)** displayed in the GitHub tile. You'll next configure the code deployment to connect your repo to a project.  ![](../../.gitbook/assets/github-enabled.png) 

## Configuring the integration

You now need to add a GitHub repo to a Sleuth project. This source of change is the repo the configured Sleuth project will monitor and report in the [Dashboard]() on each and every deploy you make to that repo, along with any other change sources you have connected to your project. 

To configure the GitHub integration: 

1. After step \#4 above, you will be taken back to the GitHub integration tile. On the GitHub tile, click the **Add code deployment** dropdown.   ![](../../.gitbook/assets/github-add-code-deployment.png) 
2. Select the [Sleuth project](../../modeling-your-deployments/projects/) you wish to add a chance source to from the dropdown list.   ![](../../.gitbook/assets/github-add-code-deployment-withdropdown.png) 
3. Follow the instructions for [setting up a new code deployment __](../../settings/project/code-deployments.md)\_\_

## Removing the integration

#### If you wish to dissolve the GitHub integration for the organization: 

1. Click on **Integrations** in the left sidebar, then on **Change Sources**. 
2. In the GitHub integration card, click **disable**. The message **GitHub disabled** is displayed in the GitHub integration card once the integration is dissolved.

The GitHub integration is disconnected and no longer available to any projects within that organization. 

