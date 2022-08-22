# Change lead time

![](<../.gitbook/assets/image (8) (2) (1).png>)

**Change lead time** measures the time it takes for a change to go from first code commit to being deployed in its target environment. Like [Deploy frequency](deploy-frequency.md), **Change lead time** is a measure of _speed_ (whereas [Change failure rate](change-failure-rate.md) and [MTTR](mttr.md) are measures of _quality_, or _stability_). &#x20;

Sleuth calculates **Change lead time** for all your [code deployments](../modeling-your-deployments/code-deployments/) and for each configured [environment](../modeling-your-deployments/environment-support.md). Because Sleuth tracks not just your pull requests or branches, but your actual _deploys_, we're able provide a highly accurate **Change lead time** that includes all the commits and pull requests that went into a deploy.‌

For instance, let's say that you deploy every merged pull request to your staging environment. However, let's also say that you bulk up all changes made in a day in staging and deploy them together to your production environment. With this style of work you'll see smaller **Change lead times** for each staging deploy. However, the **Change lead time** for your production deploy will include all the pull requests and the extended deploy time it took for them to make it to production.

For more on how Sleuth measures **Change lead time**, check out Sleuth CTO, Don Brown, explaining it in detail in this SleuthTV episode!

{% embed url="https://www.youtube.com/watch?v=h-Q70_p0PMo" %}
Sleuth CTO Don Brown explains how Sleuth calculates Change lead time
{% endembed %}

## Lead time breakdowns

In addition to showing the average Change lead time for all deploys in a selected period, Sleuth also provides a detailed breakdown of how much time your teams, on average, are spending:

* **Coding** - the time spent from first commit to when a pull request is opened
* **Review lag time** - the time spent between a pull request being opened and the first review
* **Review time** - the time spent from first review to the pull request being merged
* **Deploying** - the time spent from pull request merge to deployment

In addition to the averages found on the metrics dashboards you can always see exactly where time was spent for each deploy via its detailed view.

![Change lead time for a specific deploy](../.gitbook/assets/sleuth-sleuth-d742c80-2021-07-13-15-28-10.png)

For a more detailed timeline, including events from issue creation to deploy verification, you can always consult the [timeline](https://help.sleuth.io/modeling-your-deployments/deploy-cards#deploy-card-timeline-icons) for each deploy.

{% hint style="info" %}
On Sleuth dashboards the change lead time and breakdowns are the averages for each deploy across the period.&#x20;

On the deploy view the change lead time and breakdowns are the averages for each pull request that was deployed.

You can view the individual change lead time and breakdowns for an individual pull request by viewing the_`PRs`_tab on the deploy view.
{% endhint %}

## Feature flags and Change lead time

Sleuth [supports feature flags](../modeling-your-deployments/feature-flags.md) as a first class form of change. That said, feature flags are an instantaneous change to your running deployments. Therefore feature flags don't have a lead time or breakdown. Sleuth excludes feature flag changes from the lead time graph and associated deploy list.

## Setting up Change lead time

Sleuth uses our [code integrations](https://help.sleuth.io/integrations-1/code-deployment) (Github, Bitbucket, Gitlab, etc) coupled with our [deployment tracking](../modeling-your-deployments/) to build a complete picture of your team's lead time, the time from first commit to deploy. Once you've connected your code to Sleuth and setup your first [Code Deployment](../modeling-your-deployments/code-deployments/) Sleuth automatically tracks your change lead time for each deploy.

See [Interpreting metrics in Sleuth](how-we-calculate.md) for additional information on how to interpret Sleuth's presentation of Change lead time and the other DORA metrics

## Further Reading

For additional information on how Sleuth calculates and presents Change lead time and other DORA metrics throughout its various dashboards and views, see [Interpreting metrics in Sleuth](how-we-calculate.md).
