# Slack

### About the Integration ![](../.gitbook/assets/slack_mark_monochrome_black_sm.png) 

Take DevOps clarity to the next level with the Sleuth-Slack integration. Keep your teams and other principals informed throughout the entire CI/CD lifecycle by using Slack as your main communication channel. No more bloated distribution lists, and bombarding your team with a barrage of emails. Use Slack's powerful communications features to keep development teams informed about your code deploys, and your entire organization up to date on progress.

Agile teams will spend most of their time viewing the Sleuth [Dashboard](../dashboard.md) to get the granular detail they need to stay informed on the status of deploys, impact, magnitude, and the breadth and scope of information Sleuth provides. Other members of your organization, however, might only want a quick update on your team's progress without getting in the weeds; the Big Picture view🖼. Slack messages provide just that—automated, easily-digestable messages where they can view: 

* when your deploy occurred; 
* what was deployed; 
* who the author was;
* how big the deploy was; 
* the commit hash; 
* how many commits, PRs, issues, and changes were in the deploy; 
* any [Jira](jira.md) issues associated with the deploy; and
* a link to the Sleuth deploy card, where even more information is available.  

![A Sleuth update message in Slack.](../.gitbook/assets/slack-channel-deploy-message_2.png)

{% hint style="info" %}
A [Jira integration](jira.md) is required to view associated Jira issues within automated Slack messages from Sleuth.  
{% endhint %}

Before you start, you should already have a Slack account. Additionally, you should create channels that you plan to use for messaging in Slack before setting up the integration in Sleuth. Sleuth will ask for the Slack channel where it should send its messages to. You can have as many channels as needed. You might have different audiences, who might have different needs. Your developers might want a channel that communicates every deploy; your CTO, on the other hand, might want a quieter channel that only communicates Unhealthy deploys, which could signal a problem. But no news is good news, right? 📰 

{% hint style="info" %}
Don't forget to set the visibility on your Slack channels to either Public or Private. 
{% endhint %}

To add the Slack integration:

* Click **Integrations** in the sidebar.
* Click **connect** in the Slack Chat Ops card. 

{% hint style="info" %}
You must add Sleuth as an Authorized Application in Slack.  
For more information, [read the Slack documentation](https://api.slack.com).
{% endhint %}

* The Slack logo in the Change Source card will turn green when the integration is successful. 

![](../.gitbook/assets/slack-integration-connected.png)

{% hint style="info" %}
Click **disconnect** to dissolve the Sleuth-Slack integration. You will need to re-authorize Sleuth again if you wish to re-establish the integration.
{% endhint %}

* Sleuth will now use Slack to relay important deploy information to your team. 

{% hint style="info" %}
Slack integration is done at the Sleuth Organization level. You can share your Slack channel with anyone. This is especially useful for targeted communication, as you might not want the entire organization receiving every message about various projects that you are managing. 
{% endhint %}

  
****



