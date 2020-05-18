# Slack

## About the Integration ![](../../.gitbook/assets/slack_mark_monochrome_black_sm.png) 

Keep your teams and other principals informed throughout the entire CI/CD lifecycle by using Slack as your main communication channel. No more bloated distribution lists, and bombarding your team with a barrage of emails. Use Slack's powerful communications features to keep development teams informed about your code deploys, and your entire organization up to date on progress.

Agile teams will spend most of their time viewing the Sleuth [Dashboard](../../dashboard.md) to get the granular detail they need to stay informed on the status of deploys, impact, magnitude, and the breadth and scope of information Sleuth provides. Other members of your organization, however, might only want a quick update on your team's progress without getting in the weeds; the Big Picture view🖼. Slack messages provide just that—automated, easily-digestable messages where they can view: 

* when your deploy occurred; 
* what was deployed; 
* who the author was;
* how big the deploy was; 
* the commit hash; 
* how many commits, PRs, issues, and changes were in the deploy; 
* any [Jira]() issues associated with the deploy; and
* a link to the Sleuth deploy card, where even more information is available.  

![Sleuth bot-generated Slack notification](../../.gitbook/assets/slack-channel-deploy-message_2.png)

{% hint style="info" %}
A Jira integration is required to view associated Jira issues within automated Slack messages from Sleuth.  
{% endhint %}

Before you start, you should already have a Slack account. Additionally, you should create channels that you plan to use for messaging in Slack before setting up the integration in Sleuth. Sleuth will ask for the Slack channel where it should send its messages to. You can have as many channels as needed. You might have different audiences, who might have different needs. Your developers might want a channel that communicates every deploy; your CTO, on the other hand, might want a quieter channel that only communicates Unhealthy deploys, which could signal a problem. But no news is good news, right? 📰 

{% hint style="info" %}
Don't forget to set the security on your Slack channels, to either **Public** or **Private**. If you select **Private**, you will need to invite the Sleuth "bot" to the channel first. 
{% endhint %}

To add the Slack integration:

* Click **Integrations** in the sidebar.
* Click **connect** in the Slack Chat Ops card. 

{% hint style="info" %}
You must add Sleuth as an Authorized Application in Slack. For more information, [read the Slack documentation](https://api.slack.com).
{% endhint %}

* The Slack logo in the Change Source card will turn green when the integration is successful. 

![](../../.gitbook/assets/slack-integration-connected.png)

* The Slack integration is done at the Organization level. Since multiple Projects can exist within an Organization, you'll want to go in to each Project and configure notifications individually.  Create your Slack channels first before configuring the notifications in the Sleuth Projects; you can't create a new channel from Sleuth if it doesn't yet exist within Slack. 

{% hint style="info" %}
Click **disconnect** to dissolve the Sleuth-Slack integration. You will need to re-authorize Sleuth again if you wish to re-establish the integration.
{% endhint %}

* Sleuth will now use Slack to relay important deploy information to your team. 

### Setting up Slack notifications

{% hint style="danger" %}
This section is under construction. 
{% endhint %}

Slack integration is setup and configured in a Sleuth organization. All Sleuth projects created within the Sleuth organization have access to the configured Slack space. This enables Slack notifications to be **broadcast to everyone** who has access to the Slack space. When a channel is configured with a Sleuth project, anyone who follows that Slack channel will receive all messages sent to that channel. 

Sleuth can also be setup to send **individual Slack messages**. For example, instead of broadcasting a message to all channel subscribers of a commit, pull request or a locked repo, you might only want to notify the author \(or all authors who made at least one commit\), or only the individual who initiated the deploy. 

Notifications &gt; Configure Slack Notification

Team: Select the Slack channel \(team\); autocomplete \(no need for the hash\);

Individual: Connect Slack ID, then Sleuth can send personal messages 

Manage Account &gt; Account Settings &gt; Identities

Deploy where you are the Author; code deploys only and author of any commits or you're the one who pressed Merge. Notification is list of your code changes. List of their own PRs or own commits \(if you pressed Merge only the commit PR; only 6 maximum even if there's more information\) 

{% hint style="warning" %}
Recipients of individual Slack messages from the Sleuth bot must be registered both in your code repo \(i.e., GitHub, Bitbucket, GitLab, etc.\) and  in Sleuth. 
{% endhint %}

Your Aliases for Github are shown if Sleuth knows who are 

Slack You are connected as USERNAME

Fine Tune Notifications

Receive personal Slack messages \(only Individual\)

Only Deployed Code \(All or Exclude my deployments\) includes Commit or PR

