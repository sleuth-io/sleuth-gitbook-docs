# Getting started

Sleuth is a deployment tracker that helps you move fast without breaking things. It only takes a few minutes to connect Sleuth to a change source and start analyzing the health of your code. 

A change source can be a code deployment on Bitbucket, GitHub or GitLab; feature flags on LaunchDarkly; or issues on Clubhouse or Jira, with [many other integrations](integrations-1/about-integrations.md) available. 

To get started with Sleuth: 

1. **Create an account.** You can use an email address or connect via SSO thru Google, GitHub or Bitbucket. Read [Signing up](./) for more information. 
2. **Name your project.** You can also add a description, which is optional. 
3. **Add a change source.** This can be a code deployment on [GitHub](integrations-1/change-sources/code-deployment/github.md), feature flags on [LaunchDarkly](integrations-1/change-sources/feature-flags/launchdarkly.md), issues from [Jira](integrations-1/issue-trackers/jira.md), or the many [other available integrations](integrations-1/about-integrations.md). 
4. **Add an integration.** An integration can be change sources, chat ops, issue trackers, and error and metric trackers. Make sure you have access credentials for any integration you want to connect.  
5. **Create an account.** You can use an email address or connect via SSO thru Google, GitHub or Bitbucket. Read [Signing up](getting-started.md) for more information. 
6. **Name your project.** You can also add a description, which is optional. 
7. **Add a change source.** This can be a code deployment on [GitHub](integrations-1/change-sources/code-deployment/github.md), feature flags on [LaunchDarkly](integrations-1/change-sources/feature-flags/launchdarkly.md), issues from [Jira](integrations-1/issue-trackers/jira.md), or the many [other available integrations](integrations-1/about-integrations.md). 
8. **Add an integration.** An integration can be change sources, chat ops, issue trackers, and error and metric trackers. Make sure you have access credentials for any integration you want to connect.  

For a more detailed walkthrough of the setup process, click through the tabs below: 

{% tabs %}
{% tab title="Step 1" %}
#### Go to the Sleuth [Dashboard](dashboard.md)

![](.gitbook/assets/screen-shot-2020-04-29-at-2.17.48-pm.png)
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

Integrations are what enables Sleuth to gather data from disparate systems and present them to you in a single, easy-to-parse interface—the [Dashboard](dashboard.md). 

Integrations are made at the Sleuth organization level. You can then add as many projects as you like within the organization. Once integrations are made to the organization, all projects created under the organization have access to the integrations' connections. Furthermore, any custom settings to an integration can be made for each project. For example, your staging project might send [Slack](integrations-1/chat-ops/slack.md) notifications to one team, your production project to another. 

[Learn more](integrations-1/about-integrations.md) about integrations. 
{% endtab %}

{% tab title="Step 5" %}
#### Invite team members

![](.gitbook/assets/invite-team-members.png)

If you're part of an organization that has already set up a Sleuth environment and your email address uses the same domain, integrations might already be connected to your organization. In these cases, you won't need to add the integration yourself. 

You can add existing members to your organization or add the email address of someone you'd like to have invited to join your organization. If the invitation's accepted, the user will automatically be added to your organization. 
{% endtab %}

{% tab title="Step 6" %}
#### Add change sources

* See commits, issues, pull requests, changed files and authors for every deploy.
* Quickly see when you've rolled out code and exactly what's changed to help squash bugs.
* Release notes sent to your Slack team channels.
* See an aggregate of what's been deployed today, this week or this month.
* Allow everyone in your organization to understand what code changes you're shipping.

#### 💥 You're ready! 

You can now start seeing the impact of your changes in [the Sleuth Dashboard](dashboard.md). Happy deploying! 
{% endtab %}
{% endtabs %}



