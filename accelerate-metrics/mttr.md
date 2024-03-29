# MTTR

![](<../.gitbook/assets/image (20) (1) (1).png>)

**Mean time to recovery or MTTR** is defined in Sleuth as the time a project spends in a failure state. Along with [Change failure rate](change-failure-rate.md), **MTTR** is a measure of the _quality_, or _stability_ of your software delivery capability.&#x20;

When Sleuth detects that an Impact Source is failing (e.g. an incident in PagerDuty or an elevated metric in Datadog), it creates a failure period that tracks the details of that failure along with its start and end period. When calculating the **MTTR** for a date range, Sleuth accounts for all of the failure periods that occurred in that range and produces the average.&#x20;

For example, if you have three incidents that happened in the date period you're inspecting, one lasting 1 hour, one lasting 2 hours and one lasting 3 hours. Your MTTR will be: (1 + 2 + 3) / 3 = 2 hours.

For a real-world example of how Sleuth helps you measure and drive down your **MTTR**, let's say you make a deploy that adds 25% to your database CPU. Assume that Sleuth is tracking this impact and determines that the deploy is Unhealthy. Your team has setup [slack notifications](../notifications.md) in Sleuth, and as a result your mean time to discovery (or MTTD) is basically zero. Your team jumps into action and initiates a rollback which takes 25 minutes to complete. Once your rollback is deployed, Sleuth sees that your database CPU has gone back down to normal and auto-verifies the deploy as Healthy. Your **MTTR** in this scenario would be **25 minutes**, the amount of time it took for your team to return your project to a healthy state.

For more on how Sleuth measures **MTTR**, check out Sleuth CTO, Don Brown, explaining it in detail in this SleuthTV episode!

{% embed url="https://www.youtube.com/watch?v=4r3hdFKvA9E" %}
Sleuth CTO Don Brown explains how Sleuth measures MTTR
{% endembed %}

## MTTR breakdowns

Sleuth's [**Project Metrics**](../modeling-your-deployments/projects/) and [**Team Metrics**](../modeling-your-deployments/teams.md) dashboards show the total time spent in a failure state in the period. We also provide a detailed breakdown of the time spent in each type of failure. Failure types currently supported in Sleuth are:

* **Incidents** - any deploy with a status of `Incident` - _Sleuth provides integrations with PagerDuty, Statuspage, and many more, and we're continuously adding new integrations per customer demand. See_ [_Integrations_](broken-reference) _for an up-to-date list of those we currently support._&#x20;
* **Rolled back** - any code deploys that were [detected to be rolled back](../modeling-your-deployments/code-deployments/rollbacks.md)
* **Unhealthy** - any configured [impact sources](../integrations-1/impact-sources/) and [deploy verification](../auto-verify-your-deploys/) that has determined a deploy is `Unhealthy`
* **Ailing** - any configured [impact sources](../integrations-1/impact-sources/) and [deploy verification](../auto-verify-your-deploys/) that has determined a deploy is `Ailing`

## Feature flags and MTTR

Sleuth [supports feature flags](../modeling-your-deployments/feature-flags.md) as a first class form of change. Because feature flag changes have just as much power to affect failure and recovery as code changes feature flag changes are included in your MTTR calculations. Sleuth's [deploy verification](../auto-verify-your-deploys/) applies to flag changes in the same way it applies to code deploys.

{% hint style="info" %}
Every deployment, feature flags included, has an advanced setting that allows you to exclude it from impact collection. If this is enabled then feature flags will not affect your MTTR.
{% endhint %}

## Setting up MTTR

Because MTTR is so closely tied to Change failure rate, please see [setting up change failure rate](change-failure-rate.md#setting-up-change-failure) to configure MTTR.

## Further Reading

For additional information on how Sleuth calculates and presents MTTR and other DORA metrics throughout its various dashboards and views, see [Interpreting metrics in Sleuth](how-we-calculate.md).
