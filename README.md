# Getting started

Sleuth is a deployment tracker that helps you move fast without breaking things. It only takes a few minutes to connect Sleuth to a change source and start analyzing the health of your code. 

A change source can be a code deployment on GitHub, feature flags on LaunchDarkly, or issues on Jira, with many other integrations available. 

To get started with Sleuth: 

1. **Create an account.** You can use an email address or connect via SSO thru Google, GitHub or Bitbucket. 
2. **Name your project.** You can also add a description if you wish. 
3. **Add a change source.** This can be a code deployment on GitHub, feature flags on LaunchDarkly, issues on Jira, or many other integrations that are available. 
4. **Connect your integrations.** These are change sources, chat ops, issue trackers, or error trackers. Make sure you have access credentials for these services; Sleuth will need to connect and make the integration. If you're part of an organization that has already setup a Sleuth environment and your email address uses the same domain, your integrations might already be connected. 
5. **Add a change source.** These code deployments can be a code repo on GitHub, feature flags on LaunchDarkly, or infrastructure on AWS. As in step 4, make sure you have access credentials for these services handy. 

If you haven't already signed up for a Sleuth account, [you'll need to do that first](./). Otherwise, let's continue by connecting Sleuth to a code repo. 

{% tabs %}
{% tab title="Step 1" %}
#### Go to the Sleuth [Dashboard](dashboard.md)

![](.gitbook/assets/sleuth-dashboard-april172020.png)
{% endtab %}

{% tab title="Step 2" %}
#### Select _**Create**_, then _**Create project**_

![](.gitbook/assets/create-project.png)
{% endtab %}

{% tab title="Step 3" %}
#### Add a name and description for your project

![](.gitbook/assets/create-new-project%20%281%29.png)
{% endtab %}

{% tab title="Step 4" %}
#### Connect integrations

* Connect [GitHub](integrations-1/change-sources/code-deployment/github.md), [Bitbucket](integrations-1/change-sources/code-deployment/bitbucket.md) and [LaunchDarkly](integrations-1/change-sources/feature-flags/launchdarkly.md) change source integrations; [Slack](integrations-1/chat-ops/slack.md) ChatOps integrations; and [Jira](integrations-1/issue-trackers/jira.md) and [Clubhouse](integrations-1/issue-trackers/clubhouse.md) issue tracking integrations. 
* Enable GitHub or Bitbucket to track deploys made via your code repositories. See pull requests, commits, authors and issues associated with every deploy.
* Enable LaunchDarkly to track changes made via your feature flags. Associate your flag changes with your code deployments.
* Enable Slack to stay on top of your changes and alert your DevOps team members when changes have been deployed.
* Enable Jira or Clubhouse to track the issues and epics you are deploying to your users
{% endtab %}

{% tab title="Step 5" %}
#### Invite team members

![](.gitbook/assets/invite-team-members.png)

You can add existing members to your organization or add the email address of someone you'd like to have invited to join your organization. If the invitation's accepted, the user will automatically be added to your organization. 

You can also configure your organization so that anyone signing up with an email from your company's domain will automatically join your organization without any additional action needed.
{% endtab %}

{% tab title="Step 6" %}
#### Add change source

* See commits, issues, pull requests, changed files and authors for every deploy.
* Quickly see when you've rolled out code and exactly what's changed to help squash bugs.
* Release notes sent to your Slack team channels.
* See an aggregate of what's been deployed today, this week or this month.
* Allow everyone in your organization to understand what code changes you're shipping.

#### 💥 You're ready! 

You can now start seeing your code in [the Sleuth Dashboard](dashboard.md). Happy deploying! 
{% endtab %}
{% endtabs %}



 



