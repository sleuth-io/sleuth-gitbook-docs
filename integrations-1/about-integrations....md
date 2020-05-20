# About Integrations...

Integrations are what enable Sleuth to communicate with the various CD/CI tools in your DevOps arsenal. Sleuth is then able collect the information it needs to provide a comprehensive view of your deployments, ensuring that you always know what is happening with your code—commits, PRs, deploys, issues, errors, metrics, feature flags, authors, and so much more—and communicating successful—or failed—deployments through a [chat ops integration](about-integrations....md#chat-ops). 

You can even have Sleuth track a [manual change](manual-changes.md), which can be anything you can assign a name and description to. 

Integrations are separated by the base utility they provide: 

### Change Sources

#### Code Deployment

* [Bitbucket](change-sources/code-deployment/bitbucket.md)
* [GitHub](change-sources/code-deployment/github.md)
* [GitLab](change-sources/code-deployment/gitlab.md)\*

#### Feature Flags

* [LaunchDarkly](change-sources/feature-flags/launchdarkly.md)

#### Infrastructure

* [AWS](change-sources/infrastructure/aws.md)\*
* [Terraform Cloud](change-sources/infrastructure/terraform-cloud.md)\*

### Chat Ops

* [Slack](chat-ops/slack.md)

### Impact Sources

#### Errors

* [Honeybadger](impact-sources/errors/honeybadger.md)
* [Rollbar](impact-sources/errors/rollbar.md)
* [Sentry](impact-sources/errors/sentry.md)

#### Metrics

* [Datadog](impact-sources/metrics/datadog.md)\*
* [New Relic](impact-sources/metrics/new-relic.md)\*

### Issue Trackers

* [Clubhouse](issue-trackers/clubhouse.md)
* [Jira](issue-trackers/jira.md)

### Manual Changes

Manual changes allow you to enter just about anything into the Sleuth Dashboard as a change source. [Read](manual-changes.md) more about it. 

_**\*** indicates an integration that is coming soon._ 

