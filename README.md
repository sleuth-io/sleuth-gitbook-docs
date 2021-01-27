---
description: >-
  You can be up and running with Sleuth in less than 5 minutes. Create an
  account, connect to a code repository, and start tracking your deploys.
---

# Getting started

Getting started with **Sleuth** takes about 5 minutes. Link your code and Sleuth will instantly begin to track and verify your deploys.

* [ ] **Create a Sleuth account.** You'll need one to get started. You can create an account via OAuth using your Google, GitHub, or Bitbucket account. [Signup](https://app.sleuth.io/account/signup/) takes less than 5 minutes!  When you're done, [login to your account](https://app.sleuth.io/accounts/login/). 
* [ ] **Configure your** **organization**. A Sleuth organization is how you'll manage your team as well as any integrations you decide to connect \(i.e. Sentry, Rollbar, LaunchDarkly, Honeybadger, etc.\). Setup a domain so that invitees with a matching email domain automatically join your organization.
* [ ] **Configure your** **project**. You can make as many projects as needed to model your deployments. Each project contains two default environments: _Production_ and _Staging_. Add as many environments as you'd like to model your deployment environments. 
* [ ] **Setup a** **change source**, such as a code deployment in GitHub, Bitbucket, GitLab, or feature flags in LaunchDarkly. Sleuth will instantly analyze your commit history and show you meaningful, actionable data.

#### Integrate your Slack, Issue tracker and Observability tools to unlock the full Sleuth experience: 

* **Add the Slack integration.** Send and receive team and personal Slack notifications and use the rich sleuth slash command to take command of your deploys. If you don't use Slack, you can use Sleuth's built-in email notifications. 

{% page-ref page="integrations-1/chat-ops/" %}

* **Verify the health of your deploys by adding an impact integration.** Sleuth supports popular tools for tracking errors and metrics. **Bugsnag**, **Datadog, NewRelic**, **Honeybadger**, **Rollbar**, **Sentry**, and **SignalFx** are some of the sources Sleuth can pull from for deploy verification. 

{% page-ref page="integrations-1/impact-sources/" %}

* **Link your issues.** You probably use **Jira**, **Linear, Github issues or Clubhouse** to keep your development tasks on track. Let Sleuth automatically connect your issues with your deploys to track down the root of a code change or to conduct valuable post-mortems. 

{% page-ref page="integrations-1/issue-trackers/" %}

For a step-by-step walkthrough of the setup process, click through the tabs below:

{% tabs %}
{% tab title="Step 1 - Sign up" %}
#### Sign up to Sleuth

![](.gitbook/assets/signup-sleuth-2021-01-26-15-11-05.png)
{% endtab %}

{% tab title="Step 2 - Setup" %}
**Setup your project and connect your source provider**

![](.gitbook/assets/signup-setup-journeys-figma-2021-01-26-15-18-11.png)
{% endtab %}

{% tab title="Step 3 - Connect code " %}
#### Configure your first code deployment

![](.gitbook/assets/signup-setup-journeys-figma-2021-01-26-15-20-40.png)
{% endtab %}

{% tab title="Step 4 - Integrations" %}
#### Connect more integrations to realize the power of Sleuth

Gain team deploy notifications, personal message when your changes ship and powerful slash commands to _sleuth_ important information about your deploys by **enabling Slack**

![](.gitbook/assets/signup-setup-journeys-figma-2021-01-26-15-26-44.png)

Verify the health of your deploys by integrating your Observability and setting up deploy Impact 

![](.gitbook/assets/signup-setup-journeys-figma-2021-01-26-15-27-06.png)

[Learn more](integrations-1/about-integrations.md) about integrations. 
{% endtab %}

{% tab title="Step 5 - Done!" %}
#### Take control with your Sleuth Command Center!

![](.gitbook/assets/495d70c5-6fce-4aaa-ad85-b78bf7445c5e%20%281%29.png)
{% endtab %}
{% endtabs %}

