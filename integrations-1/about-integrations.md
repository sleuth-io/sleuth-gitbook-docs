# About Integrations...

Sleuth works with the tools you already have in place. Every integration has been designed to setup in Sleuth in under 5 minutes. Our **webhook** approach to [deploy registration](../modeling-your-deployments/code-deployments/how-to-register-a-deploy.md) means we support **every** possible way you deploy your code.

Integrations are what enable Sleuth to communicate with the tools in your DevOps arsenal. Sleuth is able to collect the information it needs to provide a comprehensive view of your deployments, ensuring that you always know what is happening with your code—commits, PRs, deploys, issues, errors, metrics, feature flags, authors, and so much more—and communicating successful—or failed—deployments through any [chat ops integrations ](about-integrations.md#chat-ops)you have set up. 

Sleuth communicates with your tools via the APIs they provide. You will need access to your tools' API keys so that Sleuth can connect to your integrations and obtain the information it needs to build a comprehensive overview of your applications' health. 

### Sleuth Integrations

| Integration | Type | Additional info... |
| :--- | :--- | :--- |
| [AWS CloudWatch](impact-sources/metrics/aws-cloudwatch.md) | Impact metric tracking | Metrics tracker |
| [Bitbucket](code-deployment/bitbucket.md) | Code deploys | Code deployments as a change source |
| [Bugsnag](impact-sources/errors/bugsnag.md) | Impact error tracking | Error tracker |
| [Custom impact](impact-sources/metrics/custom.md) | Impact metric tracking | Submit custom metrics |
| [CircleCI](builds/circleci.md) | Deployment CI/CD | Track your builds |
| [Clubhouse](issue-trackers/clubhouse.md) | Deploy issue tracker | Automatically associate issues with deploys |
| [Datadog](impact-sources/metrics/datadog.md) | Impact metric tracking | Metrics tracker |
| [GitHub](code-deployment/github.md) | Code deploys | Code deployments as a change source |
| [GitLab](code-deployment/gitlab.md) | Code deploys | Code deployments as a change source |
| [Honeybadger](impact-sources/errors/honeybadger.md) | Impact error tracking | Error tracker |
| [Jira](issue-trackers/jira.md) | Deploy issue tracker | Automatically associate issues with deploys |
| [LaunchDarkly](feature-flags/launchdarkly.md) | Feature flag changes | Feature flags as a change source |
| [Linear](issue-trackers/linear.md) | Deploy issue tracker | Automatically associate issues with deploys |
| [NewRelic](impact-sources/metrics/newrelic.md) | Impact metric tracking | Metrics tracker |
| [Rollbar](impact-sources/errors/rollbar.md) | Impact error tracking | Error tracker |
| [Sentry](impact-sources/errors/sentry.md) | Impact error tracking | Error tracker |
| [SignalFx](impact-sources/metrics/signalfx.md) | Impact metric tracking | Metrics tracker |
| [Slack](slack.md) | Notifications and control | Notify your entire team or specific individuals |
| [Terraform Cloud](https://www.terraform.io/cloud) | Code deploys | Automatically register a deploy via a Webhook |

