# Change lead time

![](<../.gitbook/assets/image (8).png>)

Sleuth tracks **change lead time**, defined as the time from your first commit to deploy, for all your [code deployments](../modeling-your-deployments/code-deployments/) and for each configured [environment](../modeling-your-deployments/environment-support.md). Because Sleuth tracks deployments and not just pull requests or branches we can provide an accurate change lead time that includes all the commits and pull requests that went into a deploy.‌

For instance, let's say that you deploy every merged pull request to your staging environment. However, let's also say that you bulk up all changes made in a day in staging and deploy them together to your production environment. With this style of work you'll see small change lead times for each staging deploy. However, the change lead time for your production deploy will include all the pull requests and the extended deploy time it took for them to make it to production.

## Lead time breakdowns

Sleuth project and team metrics dashboards show the average lead time for all deploys in the period. We also provide a detailed breakdown of how much your teams, on average, are spending:

* Coding - the time spent from first commit to when a pull request is opened
* Review lag time - the time spent between a pull request being opened and the first review
* Review time - the time spent from first review to the pull request being merged
* Deploying - the time spent from pull request merge to deployment

In addition to the averages found on the metrics dashboards you can always see exactly where time was spent for each deploy via its detailed view.

![](../.gitbook/assets/sleuth-sleuth-d742c80-2021-07-13-15-28-10.png)

For a more detailed timeline, including events from issue creation to deploy verification, you can always consult the [timeline](https://help.sleuth.io/modeling-your-deployments/deploy-cards#deploy-card-timeline-icons) for each deploy.

## Feature flags and change lead time

Sleuth [supports feature flags](../modeling-your-deployments/feature-flags.md) as a first class form of change. That said, feature flags are an instantaneous change to your running deployments. Therefore feature flags don't have a lead time or breakdown. Sleuth excludes feature flag changes from the lead time graph and associated deploy list.

## Setting up change lead time

Sleuth uses our [code integrations](https://help.sleuth.io/integrations-1/code-deployment) (Github, Bitbucket, Gitlab, etc) coupled with our [deployment tracking](../modeling-your-deployments/) to build a complete picture of your team's lead time, the time from first commit to deploy. Once you've connected your code to Sleuth and setup your first [Code Deployment](../modeling-your-deployments/code-deployments/) Sleuth automatically tracks your change lead time for each deploy.
