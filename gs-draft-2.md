# GS Draft 2

Getting started with **Sleuth** takes about 5 minutes. The only thing you need is a code repository. Sleuth will instantly provide a health assessment of your code based on its commit history. 

Following are some things we'll do to get you going with Sleuth: 

* [ ] **Create a Sleuth account.** You'll need one to get started. You can create an account via OAuth using your Google, GitHub, or Bitbucket account. 
* [ ] **Create an** **organization**. A Sleuth organization is how you'll manage your team as well as any integrations you decide to connect \(i.e. Sentry, Rollbar, LaunchDarkly, Honeybadger, etc.\). 
* [ ] **Create a** **project**. You can make as many projects as needed to model your deployments. Each project contains two default environments: _Production_ and _Staging_. Add as many environments as you'd like, or use only one \(i.e., monorepo\). 
* [ ] **Set up a** **change source**, such as a code deployment in GitHub or Bitbucket, or feature flags in LaunchDarkly. Sleuth will instantly analyze your commit history and show you meaningful, actionable data instantly.
* [ ] **Invite others on your team to join your** **organization**. Setup a domain so that invitees with a matching email domain automatically join your organization. 

#### Take Sleuth to the next level with these additional options: 

* **Add a ChatOps integration.** Send and receive team and personal Slack notifications. If you don't use Slack, you can use Sleuth's built-in email notifications. 

{% page-ref page="integrations-1/chat-ops/" %}

* **Add an impact integration.** Sleuth supports popular tools for tracking errors and metrics. **Bugsnag**, **Datadog**, **Honeybadger**, **Rollbar**, **Sentry**, and **SignalFx** are some of the integrations you can make with Sleuth. 

{% page-ref page="integrations-1/impact-sources/" %}

* **Add an issue tracker.** You probably use **Clubhouse**, **Jira**, or **Linear** to keep your development tasks on track. Let Sleuth automatically connect your issues with your deploys to track down the root of a code change or to conduct valuable post-mortems. 

{% page-ref page="integrations-1/issue-trackers/" %}

