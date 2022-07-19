# Change failure rate

![What you define as a change failure can vary from project to project. It can be as broad as a change causing a hard-down incident or as fine as a business metric deviating from its norm. Sleuth allows users to flexibly define what failure means to their projects via deploy verification and impact tracking.](<../.gitbook/assets/image (22) (1).png>)

## Change failure breakdowns

Sleuth's project and team metrics dashboards show the total number of deploys that were deemed a failure in the period. We also provide a detailed breakdown of deploys by the type of failure. Failure types currently supported in Sleuth are:

* Incidents - any deploy with a status of `Incident` - _Sleuth provides integrations with PagerDuty, Statuspage, and many more, and we're continuously adding new integrations per customer demand. See_ [_Integrations_](broken-reference) _for an up-to-date list of those we currently support._&#x20;
* Rolled back - any code deploys that were [detected to be rolled back](../modeling-your-deployments/code-deployments/rollbacks.md)
* Unhealthy - any configured [impact sources](../integrations-1/impact-sources/) and [deploy verification](../auto-verify-your-deploys/) that has determined a deploy is `Unhealthy`
* Ailing - any configured [impact sources](../integrations-1/impact-sources/) and [deploy verification](../auto-verify-your-deploys/) that has determined a deploy is `Ailing`

## Feature flags and change failure rate

Sleuth [supports feature flags](../modeling-your-deployments/feature-flags.md) as a first class form of change. Because feature flag changes have just as much power to affect failure as code changes, feature flag changes are included in your change failure rate calculations. Sleuth's [deploy verification](../auto-verify-your-deploys/) applies to flag changes in the same way it applies to code deploys.

{% hint style="info" %}
Every deployment, feature flags included, has an advanced setting that allows you to exclude it from impact collection. If this is enabled, then feature flags will not affect your change failure rate.
{% endhint %}

## Setting up change failure

Sleuth's change failure rate is configured and calculated at the [Project](../modeling-your-deployments/projects/) level. By default Sleuth considers any deploys marked as `Unhealthy` as a failure. You can change the failure level in your project settings. If you would like to count only Incidents as failure, then set the failure level to `Incident`.

Sleuth's [deploy verification](../auto-verify-your-deploys/) allows you to integrate error trackers, such as Sentry and Rollbar, metrics trackers, like AWS CloudWatch and Datadog, and incident trackers, like Statuspage and Pagerduty _(see_ [_Integrations_](broken-reference) _for a full list of currently supported integrations)_. When Sleuth auto-verifies a deploy as `Unhealthy` that deploy is considered a failure. Setting a deploy to `Unhealthy` manually will also be considered a failure. Sleuth also supports code deploy [rollbacks](../modeling-your-deployments/code-deployments/rollbacks.md). `Rolled back` deploys also count as change failure.

{% hint style="info" %}
When configuring change failure rate you'll want to determine what failure means to your project. Sleuth is flexible and allows you to define whatever failure criteria works for your projects. Once configured at the project level, change failure rate is also viewable by contributing [teams](../modeling-your-deployments/teams/). Just keep in mind that the failure data Sleuth provides is only as good as the data coming in.
{% endhint %}
