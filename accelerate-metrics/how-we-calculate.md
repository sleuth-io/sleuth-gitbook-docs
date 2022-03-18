# How we calculate

To trust and improve your DORA metrics you must understand exactly how each of the four DORA metrics are calculated.

## Frequency

Sleuth shows you the **deploy frequency** for all [code deployments](../modeling-your-deployments/code-deployments/) and [feature flags](../modeling-your-deployments/feature-flags.md) you've setup within a [project](../modeling-your-deployments/projects/) and [environment](../modeling-your-deployments/environment-support.md). Sleuth allows you to see your deploy frequency for each [environment](../modeling-your-deployments/environment-support.md) you maintain.‌

Once you've [configured your deployment to let Sleuth know when you deploy](../modeling-your-deployments/code-deployments/how-to-register-a-deploy.md) Sleuth will use those events to determine your frequency. We will show you your Flag change frequency but don't bake that into the overall frequency DORA metric.

The deploys per day statistic is calculated by taking the total number of deploys divided by the total number of days in the period, weekends included.

You can read about how we calculate the Frequency sub-metric of batch size [here](https://help.sleuth.io/accelerate-metrics/deploy-frequency#batch-size-breakdowns).

## Change lead time

Change lead time is defined as the time from first commit to deploy. Sleuth allows you to see your change lead time for each [environment](../modeling-your-deployments/environment-support.md) you maintain.‌&#x20;

Sleuth further breaks down change lead time into four categories:

1. Coding - the amount of time between first commit and a pull request being opened
2. Review lag - the amount of time between a pull request being opened and the first approval
3. Review - the amount of time between first approval and the pull request being merged
4. Deploying - the amount of time between the pull request being merged and [Sleuth discovering you've deployed](../modeling-your-deployments/code-deployments/how-to-register-a-deploy.md)

{% hint style="info" %}
On Sleuth dashboards the change lead time and breakdowns are the averages for each deploy across the period.&#x20;

On the deploy view the change lead time and breakdowns are the averages for each pull request that was deployed.

You can view the individual change lead time and breakdowns for an individual pull request view the `PRs` tab on the deploy view.
{% endhint %}

## Change failure rate

Change failure rate is defined for each project and environment. The failure conditions are determined by the [Impact integrations](../integrations-1/impact-sources/) you've setup. We recommend that you read our docs on [how to define failure](change-failure-rate.md) first.

The way failure rate is calculated is Sleuth takes the number of deploys that were within [your change failure sensitivity](https://help.sleuth.io/settings/project/details#advanced-settings) divided by the total number of deploys in the period.

For example, if you've setup the [PagerDuty integration](../integrations-1/incident-tracker-integrations/pagerduty.md#about-the-integration) as an impact source and your team has one incident during the report period that spanned two deploys and you made a total of 20 deploys in that period you change failure rate will be: 2 / 20 = 10%.

## MTTR (mean time to recovery)

Sleuth calculates MTTR for a specific project and environment pairing based on the Impact that has been configured for the Project. We recommend that you read our docs on [how to define failure](change-failure-rate.md) first.

When Sleuth detects that an Impact source is failing, e.g. an incident in PagerDuty or an elevated metric in Datadog, we create a failure period that tracks its details and the start and end period. When calculating the MTTR for a date range we take all the failure periods that happened in that range and produce the average.&#x20;

For example, if you have three incidents that happened in the date period you're inspecting, one lasting 1 hour, one lasting 2 hours and one lasting 3 hours. Your MTTR will be: (1 + 2 + 3) / 3 = 2 hours.



