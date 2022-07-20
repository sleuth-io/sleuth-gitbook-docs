# MTTR

![](<../.gitbook/assets/image (20) (1) (1).png>)

**Mean time to recovery or MTTR** is defined in Sleuth as the time a project spends in a failure state.

For instance, let's say you make a deploy that adds 25% to your database CPU. Assume that Sleuth is tracking this impact and determines that the deploy is Unhealthy. You team has setup [slack notifications](../notifications.md) in Sleuth, and as a result your mean time to discovery or MTTD is basically zero. Your team jumps into action and initiates a rollback which takes 25 minutes to complete. Once your rollback is deployed, Sleuth sees that your database CPU has gone back down to normal and auto-verifies the deploy as Healthy. Your **MTTR** in this scenario would be **25 minutes**, the amount of time it took for your team to return your project to a healthy state.

## MTTR breakdowns

The Sleuth project and team metrics dashboards show the total time spent in a failure state in the period. We also provide a detailed breakdown of the time spent in each type of failure. Failure types currently supported in Sleuth are:

* Incidents - any deploy with a status of `Incident` - _Sleuth provides integrations with PagerDuty, Statuspage, and many more, and we're continuously adding new integrations per customer demand. See_ [_Integrations_](broken-reference) _for an up-to-date list of those we currently support._&#x20;
* Rolled back - any code deploys that were [detected to be rolled back](../modeling-your-deployments/code-deployments/rollbacks.md)
* Unhealthy - any configured [impact sources](../integrations-1/impact-sources/) and [deploy verification](../auto-verify-your-deploys/) that has determined a deploy is `Unhealthy`
* Ailing - any configured [impact sources](../integrations-1/impact-sources/) and [deploy verification](../auto-verify-your-deploys/) that has determined a deploy is `Ailing`

## Feature flags and MTTR

Sleuth [supports feature flags](../modeling-your-deployments/feature-flags.md) as a first class form of change. Because feature flag changes have just as much power to affect failure and recovery as code changes feature flag changes are included in your MTTR calculations. Sleuth's [deploy verification](../auto-verify-your-deploys/) applies to flag changes in the same way it applies to code deploys.

{% hint style="info" %}
Every deployment, feature flags included, has an advanced setting that allows you to exclude it from impact collection. If this is enabled then feature flags will not affect your MTTR.
{% endhint %}

## Setting up MTTR

Because MTTR is closely tied to change failure please see [setting up change failure rate](change-failure-rate.md#setting-up-change-failure) to configure MTTR.
