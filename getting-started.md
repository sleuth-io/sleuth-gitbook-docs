# Getting started

Getting started with **Sleuth** takes about 5 minutes. The only thing you need is a code repository. Sleuth will instantly provide a health assessment of your code based on its commit history. 

The following actions will get you on the path to fast deployment and less errors with Sleuth: 

* [ ] **Create a Sleuth account.** You'll need one to get started. You can create an account via OAuth using your Google, GitHub, or Bitbucket account. 
* [ ] **Create an** **organization**. A Sleuth organization is how you'll manage your team as well as any integrations you decide to connect \(i.e. Sentry, Rollbar, LaunchDarkly, Honeybadger, etc.\). 
* [ ] **Create a** **project**. You can make as many projects as needed to model your deployments. Each project contains two default environments: _Production_ and _Staging_. Add as many environments as you'd like, or use only one \(i.e., monorepo\). 
* [ ] **Set up a** **change source**, such as a code deployment in GitHub or Bitbucket, or feature flags in LaunchDarkly. Sleuth will instantly analyze your commit history and show you meaningful, actionable data instantly.
* [ ] **Invite others on your team to join your** **organization**. Setup a domain so that invitees with a matching email domain automatically join your organization. 

#### Increase impact fidelity and team communication by adding the following features: 

* **Add a ChatOps integration.** Send and receive team and personal Slack notifications. If you don't use Slack, you can use Sleuth's built-in email notifications. 

{% page-ref page="integrations-1/chat-ops/" %}

* **Add an impact integration.** Sleuth supports popular tools for tracking errors and metrics. **Bugsnag**, **Datadog**, **Honeybadger**, **Rollbar**, **Sentry**, and **SignalFx** are some of the integrations you can make with Sleuth. 

{% page-ref page="integrations-1/impact-sources/" %}

* **Add an issue tracker.** You probably use **Clubhouse**, **Jira**, or **Linear** to keep your development tasks on track. Let Sleuth automatically connect your issues with your deploys to track down the root of a code change or to conduct valuable post-mortems. 

{% page-ref page="integrations-1/issue-trackers/" %}

For a step-by-step walkthrough of the setup process, click through the tabs below: 

{% tabs %}
{% tab title="Step 1" %}
#### Go to the Sleuth [Dashboard](dashboard-1/dashboard.md)

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

Integrations are what enables Sleuth to gather data from your development tools and present them to you in a single, easy-to-use interface—the [Dashboard](dashboard-1/dashboard.md). 

Integrations are made at the Sleuth organization level. You can then add as many projects as you need within the organization. Once integrations are made to the organization, all projects created under the organization have access to the integrations' connections. You can also add environments to each project; by default, Sleuth provides a production and staging environment to every new project. You can use as little or as many environments as needed to model your projects. 

Furthermore, any custom settings to an integration can be made for each project. For example, your staging environment might send [Slack](integrations-1/chat-ops/slack.md) notifications to one team, your production environment to another. 

[Learn more](integrations-1/about-integrations.md) about integrations. 
{% endtab %}

{% tab title="Step 5" %}
#### Invite team members

![](.gitbook/assets/invite-team-members.png)

If you're part of an organization that has already set up a Sleuth environment and your email address uses the same domain, integrations might already be connected to your organization. In this case, you won't need to add the integration yourself. 

You can add existing members to your organization or add the email address of someone you'd like to have invited to join your organization. If the invitation's accepted, the user will automatically be added to your organization. Go to Organization settings for more information on inviting team members. 

You should also configure Sleuth's RBAC \(Role-Based Access Control\) system to control what team members can do with their Sleuth account. For more information, see [Access Control](settings/access-control.md), then head to the [Organization's Members settings](settings/organization/) to set it all up. 
{% endtab %}

{% tab title="Step 6" %}
#### Add change sources

* See commits, issues, pull requests, changed files and authors for every deploy.
* Get notified when you or others on your team deploy, and know exactly what's changed and how it impacts your code.
* Get release notes sent to specified Slack channels.
* See an aggregate of what's been deployed today, this week or the entire month.
* Allow everyone in your organization to understand what code changes you're shipping.
{% endtab %}

{% tab title="Step 7" %}
Configure settings for your: 

* [Organization](settings/organization/) 
* [Project](settings/project/)
* [Account](settings/account/)

####  💥 You're ready! 

Start seeing the impact of your changes in [the Sleuth Dashboard](dashboard-1/dashboard.md). Happy deploying! 
{% endtab %}
{% endtabs %}



