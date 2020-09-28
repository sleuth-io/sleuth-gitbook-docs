# About...

Integrations are what enable Sleuth to communicate with the CD/CI tools in your DevOps arsenal. Sleuth is then able to collect the information it needs to provide a comprehensive view of your deployments, ensuring that you always know what is happening with your code—commits, PRs, deploys, issues, errors, metrics, feature flags, authors, and so much more—and communicating successful—or failed—deployments through any [chat ops integrations ](about-integrations.md#chat-ops)you have set up. 

Sleuth acts as a control panel so that you can have a single place to monitor your deployed applications, and know instantly when something goes wrong and where you need to go to fix it. 

Sleuth communicates with your tools via the APIs they provide. You will need access to your tools' API keys so that Sleuth can connect to your integrations and obtain the information it needs to build a comprehensive overview of your applications' health. Sleuth surfaces this data via its [Dashboard](../dashboard-1/dashboard.md).  

You can even have Sleuth track a [manual change](manual-changes.md), which can be anything you can give a name and description to. 

### Sleuth Integrations

| Integration | Type | Additional info... |
| :--- | :--- | :--- |
| [AWS](change-sources/infrastructure/aws.md) | Infrastructure | Can be used a change source. _Coming soon_ |
| [Bitbucket](change-sources/code-deployment/bitbucket.md) | Code Deployment | Code deployments as a change source |
| [CircleCI](builds/circleci.md) | Builds | Track your builds |
| [Clubhouse](issue-trackers/clubhouse.md) | Issue Tracker | Automatically associate issues with deploys |
| [Datadog](impact-sources/metrics/datadog.md) | Metric Tracker | Metrics tracker |
| [GitHub](change-sources/code-deployment/github.md) | Change Source | Code deployments as a change source |
| [GitLab](change-sources/code-deployment/gitlab.md) | Change Source | Code deployments as a change source |
| [Honeybadger](impact-sources/errors/honeybadger.md) | Error Tracker | Error tracker |
| [Jira](issue-trackers/jira.md) | Issue Tracker | Automatically associate issues with deploys |
| [LaunchDarkly](change-sources/feature-flags/launchdarkly.md) | Change Source | Feature flags as a change source |
| [Linear](issue-trackers/linear.md) | Issue Tracker | Automatically associate issues with deploys |
| [Rollbar](impact-sources/errors/rollbar.md) | Error Tracker | Error tracker |
| [Sentry](impact-sources/errors/sentry.md) | Error Tracker | Error tracker |
| [SignalFx](impact-sources/metrics/signalfx.md) | Metric Tracker | Metrics tracker |
| [Slack](chat-ops/slack.md) | Chat Ops | Notify your entire team or specific individuals |
| [Terraform Cloud](change-sources/infrastructure/terraform-cloud.md) | Infrastructure | Can be used as a change source. _Coming soon_ |

### Manual Changes

Manual changes allow you to enter just about anything into the Sleuth Dashboard as a change source. [Read](manual-changes.md) more about it.  __

