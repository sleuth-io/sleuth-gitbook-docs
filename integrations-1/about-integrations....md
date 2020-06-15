# About Integrations...

Integrations allow Sleuth to communicate with the various CD/CI tools in your DevOps arsenal. They enable Sleuth to collect the information it needs to provide a comprehensive view of your deployments, ensuring that you always know what is happening with your code—commits, PRs, deploys, issues, errors, metrics, feature flags, authors, and so much more—and communicating successful—or failed—deployments through a chat ops integration. 

You can even have Sleuth track a [manual change](manual-changes.md), which can be anything you can assign a name and description to. 

Integrations are made at the organization level. This gives all projects created within that organization access to the integration. If applicable, custom settings for a particular integration are made from within the project. For example, individual Slack notifications are made at the project level; this segregates messages to that particular project so that users only receive messages for projects they contributed to.  

### Sleuth Integrations

| Integration | Type | Additional info... |
| :--- | :--- | :--- |
| [AWS](change-sources/infrastructure/aws.md) | Infrastructure | Can be used a change source. _Coming soon._  |
| [Bitbucket](change-sources/code-deployment/bitbucket.md) | Code Deployment | Can be used a change source.  |
| [CircleCI](builds/circleci.md) | Builds | _Coming soon._ |
| [Clubhouse](issue-trackers/clubhouse.md) | Issue Tracker |  |
| [Datadog](impact-sources/metrics/datadog.md) | Impact Metrics | _Coming soon._ |
| [GitHub](change-sources/code-deployment/github.md) | Code Deployment | Can be used as a change source.  |
| [GitLab](change-sources/code-deployment/gitlab.md) | Code Deployment | _Coming soon._ |
| [Honeybadger](impact-sources/errors/honeybadger.md) | Impact Errors |  |
| [Jira](issue-trackers/jira.md) | Issue Tracker |  |
| [LaunchDarkly](change-sources/feature-flags/launchdarkly.md) | Feature Flags | Can be used a change source.  |
| [New Relic](impact-sources/metrics/new-relic.md) | Impact Metrics | _Coming soon._ |
| [Rollbar](impact-sources/errors/rollbar.md) | Impact Errors |  |
| [Sentry](impact-sources/errors/sentry.md) | Impact Errors |  |
| [Slack](chat-ops/slack.md) | Chat Ops |  |
| [Terraform Cloud](change-sources/infrastructure/terraform-cloud.md) | Infrastructure | _Coming soon._  |

### Manual Changes

Manual changes allow you to enter just about anything into the Sleuth Dashboard as a change source. [Read](manual-changes.md) more about it.  __

