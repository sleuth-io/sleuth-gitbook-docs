# Slack integration

Sleuth's Slack integration provides you a [mission control for your deploys](../slack-mission-control/), right from Slack.

Before you start, you should already have a Slack account. Additionally, you should create channels that you plan to use for notifications in Slack before setting up the integration. Sleuth will ask for the Slack channel where it should send its notifications. You can create as many channels necessary to target notifications for individual environments.

Slack integration is setup and configured in a Sleuth organization. When a channel is [configured with a Sleuth project](../settings/project/slack-notifications.md), anyone who follows that Slack channel will receive all messages sent to that channel. Sleuth can also be setup to send [personal Slack notifications](../slack-mission-control/personal-notifications.md). 

## Setting up the integration

1. Click **Integrations** in the sidebar.
2. In the **Chat Ops** &gt; **Slack** card, click **enable**. 
3. Click **Allow** to make the integration. 

{% hint style="info" %}
You must add Sleuth as an Authorized Application in Slack. For more information, [read the Slack documentation](https://api.slack.com).
{% endhint %}

{% hint style="warning" %}
Adding a third-party integration to Slack must be authorized by your Slack App Manager. Slack allows you to message the App Manager directly from the _Request to install_ dialog, as shown below. Once authorization is granted, you can proceed with the integration.
{% endhint %}

![Adding Slack third-party integrations might require your App Manager&apos;s approval.](../.gitbook/assets/slack-request-to-install-screen%20%281%29.png)

4. Upon a succesful connection to your Sleuth account, the message **Slack enabled \(Connected to workspace** _**&lt;workspace name&gt;**_**\)** is displayed in the tile. 

![](../.gitbook/assets/slack-integration-connected.png)

{% hint style="info" %}
The Slack integration is done at the organization level. Since multiple [projects](../modeling-your-deployments/projects/) can exist within an organization, you'll want to go in to each [project and configure notifications](../settings/project/slack-notifications.md) individually. 
{% endhint %}

## Configuring the integration

To setup team notifications for a project see

{% page-ref page="../settings/project/slack-notifications.md" %}

To setup personal notifications for yourself see

{% page-ref page="../settings/account/notifications.md" %}

## Removing the integration

#### If you wish to dissolve the **Slack** integration for the organization: 

1. Click on **Integrations** in the left sidebar, then on **Chat Ops**. 
2. In the Slack integration card, click **disable**. The message **Slack disabled** is displayed in the Slack integration card once the integration is dissolved.

The Slack integration is disconnected and no longer available to any projects within that organization. Any project-level modifications you made to the Slack integration will be lost. 

