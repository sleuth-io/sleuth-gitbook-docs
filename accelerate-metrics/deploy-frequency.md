# Deploy frequency

![](<../.gitbook/assets/image (17) (1) (1).png>)

**Deploy frequency** measures how often you deploy changes to a given target environment. Along with [Change lead time](change-lead-time.md), **Deploy frequency** is a measure of _speed_ (whereas [Change failure rate](change-failure-rate.md) and [MTTR](mttr.md) are measures of _quality_, or _stability_) &#x20;

Once you've [configured your deployment to let Sleuth know when you deploy](../modeling-your-deployments/code-deployments/how-to-register-a-deploy.md), Sleuth will use those events to determine your deploy frequency for all [code deployments](../modeling-your-deployments/code-deployments/) and [feature flags](../modeling-your-deployments/feature-flags.md) you've setup within a [project](../modeling-your-deployments/projects/) and [environment](../modeling-your-deployments/environment-support.md).&#x20;

Sleuth's [**Project Metrics**](../modeling-your-deployments/projects/) and [**Team Metrics**](../modeling-your-deployments/teams.md) dashboards show the total number of deploys and the frequency, deploys per day, in the selected period. The deploys per day statistic is calculated by taking the total number of deploys divided by the total number of days in the period, weekends included.&#x20;

For more on how Sleuth measures Deploy frequency, check out Sleuth CTO, Don Brown, explaining it in detail in this SleuthTV episode!

{% embed url="https://www.youtube.com/watch?v=ewWqbLL-3LE" %}
Sleuth CTO Don Brown explains how Sleuth measures Deploy frequency
{% endembed %}

### Batch Size Breakdowns

In order to help you better contextualize your deploy frequency, Sleuth also provides a detailed breakdown of the batch size of each deploy as a percentage of the total and broken down per day. Batch size is defined as a blend of the number of pull requests, the number of commits, and the amount of code changed, weighted in that order. Batch sizes are defined as:

* Small - usually 1 pull request, 1 - 10 commits and a few hundred lines of code changed
* Medium - usually 1 - 2 pull requests, 10 - 30 commits and many hundreds of lines of code changed
* Large - usually 2 - 4 pull requests, 20 - 40 commits and many hundreds of lines of code changed
* Gigantic - usually 4 or more pull requests or 30 or more commits or many thousands of lines of code changed

{% hint style="info" %}
Because batch size is a weighted blend of pull requests, commits and code changes, you may find that an especially large amount of change in any of those elements can cause a deploy to be classified as Large or Gigantic.
{% endhint %}

## Feature flags and Deploy frequency

Sleuth [supports feature flags](../modeling-your-deployments/feature-flags.md) as a first class form of change. That said, we find that teams want to understand the distinction between their code deploy frequency and their flag change frequency. Sleuth's Project Metrics and Team Metrics dashboards show the two frequencies as separate graph lines and allows you to toggle one or the other on and off. To see totals for flag frequency you can hover over a data point.

## Setting up Deploy frequency

Sleuth uses our [code integrations](https://help.sleuth.io/integrations-1/code-deployment) (Github, Bitbucket, Gitlab, etc) coupled with our [deployment tracking](../modeling-your-deployments/) to understand when you've deployed. Once you've connected your code to Sleuth, setup your first [code deployment](../modeling-your-deployments/code-deployments/) and started [registering deploys](../modeling-your-deployments/code-deployments/how-to-register-a-deploy.md) Sleuth will automatically track your deploy frequency and batch size breakdown for each deploy to each of your defined [Environments](../modeling-your-deployments/environment-support.md).

Sleuth uses our [LaunchDarkly integration](../integrations-1/feature-flags/launchdarkly.md) to track feature flag changes. Once setup, we'll automatically start tracking your flag frequency across each of your defined [Environments](../modeling-your-deployments/environment-support.md).

{% hint style="info" %}
For the most accurate metrics we recommend using one of our native [CI/CD integrations](../integrations-1/builds/) or a [webhook to register](https://help.sleuth.io/modeling-your-deployments/code-deployments/how-to-register-a-deploy#precise-deploy-registration-via-a-webhook) your deploys. Initially, Sleuth is configured to count a pull request merge as a deploy until we've received your first integrated deployment notification.
{% endhint %}

## Further Reading

For additional information on how Sleuth calculates and presents Deploy frequency and other DORA metrics throughout its various dashboards and views, see [Interpreting metrics in Sleuth](how-we-calculate.md).
