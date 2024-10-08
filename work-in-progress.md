# Work in Progress

In addition to tracking deploy metrics, Sleuth also provides **Work in Progress** dashboards and notifications for Teams and Projects that provide real-time visibility into in-flight work (i.e. work that has not yet deployed) and highlight risks that teams can address right now.&#x20;

<figure><img src=".gitbook/assets/image (64).png" alt=""><figcaption><p>Work in Progress dashboard for a specific Project</p></figcaption></figure>

### What is "Work in Progress"?

Work in Progress, or WIP, includes any PRs that have not yet deployed to their target environment.&#x20;

### Understanding "at-risk" items

While the **Work in Progress** dashboards present in-flight work in part to provide general visibility into the changes that are likely deploy next, the real value of these dashboard is that they highlight "at risk" items that are likely to have a negative impact on your DORA metrics. This early risk identification allows you to take immediate corrective actions on at-risk items before they ship, driving tactical improvements to your DORA metrics.&#x20;

Sleuth currently highlights the following risk types:

* Batch Size
* Total change lead time (CLT)
* Coding time
* Review lag time
* Review time
* Waiting to deploy

For Batch Size, an item is considered "at risk" if it is either Large or Gigantic.

For change lead time and its four composite breakdowns, an item is considered "at risk" if it's current value exceeds your average by more than 30% (where your "average" is calculated based on the items that _deployed_ during the same period as your currently work-in-progress data range selection). Note that an item must accumulate a minimum of 30 minutes in a given CLT bucket before Sleuth will potentially flag it as at-risk relative to your average.&#x20;

### Understanding Work in Progress filters

The Work in Progress dashboards provide three levels of filtering.

#### Left-hand navigation filters

Like all Project-specific and Team-specific dashboards in Sleuth, the highest-level filters for the Work in Progress dashboard are the Project/Team selector and the Environment selector.

When filtering by a specific Environment, note that in order for Sleuth to track PRs for an environment, that environment must be mapped to a branch. See [Environments](modeling-your-deployments/environment-support.md) for more information.

#### Top-level dashboard filters

Just like the Metrics Dashboards for Projects and teams, the Work in Progress dashboard can be filtered using top-level filters for Date Range, Projects, Teams, Environments, and Deployments. These filters impact the specific PRs that display in the listing as well as the data that is displayed in all of the dashboard charts.

<figure><img src=".gitbook/assets/image (49).png" alt=""><figcaption><p>Top-level work-in-progress dashboard filters</p></figcaption></figure>

Special considerations when using the Date Range filter:

* The Date Range filter allows you to select the "from" date, but the "to" date will always be the current date. The main reason for specifying a "from" date is to exclude "zombie PRs" (i.e. PRs that have not been updated for a long time and so should not be included in your universe of "current work in progress"
* For WIP risks that rely on comparison against your "average", that average is calculated based on the items that _deployed_ in the same period as your currently selected work-in-progress date range.
* When you enable [build tracking](modeling-your-deployments/code-deployments/how-to-register-a-deploy.md) for a [code deployment](modeling-your-deployments/code-deployments/), if you opt to include historical deploy data for the past 4 weeks, then Sleuth will also fetch all work-in-progress updated in that time period so that you can immediately begin analyzing your in-flight work.
* Note that Sleuth has been collecting work in progress data only since November 23, 2022, so it is not possible to view work in progress that has not been updated since before that date. &#x20;

Special considerations when using the Date Range filter:

* The Date Range filter allows you to select the "from" date, but the "to" date will always be the current date. The main reason for specifying a "from" date is to exclude "zombie PRs" (i.e. PRs that have not been updated for a long time and so should not be included in your universe of "current work in progress"

#### Work-in-progress listing filter

In addition to the top-level filters, the detailed listing of work-in-progress items provides an additional filter to zero-in on items that exhibit a particular risk type. &#x20;

<figure><img src=".gitbook/assets/image (4) (3) (1).png" alt=""><figcaption><p>Work-in-progress listing filters by specific risk types</p></figcaption></figure>

By default, this filter is set to "No Filters," which displays all work-in-progress items that match the top-level filters (i.e. regardless of what risks they might or might not exhibit).

Selecting "All at risk items" filters the listing to show only those items that exhibit some risk (regardless of which specific risk type or types they might exhibit).&#x20;

The remaining filters selections show items that exhibit a particular risk type. When these specific risk type filters are active, the listing is also sorted by that risk value from riskiest to least risky.

### Understanding work in progress charts

| Chart                                    | Explanation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![](<.gitbook/assets/image (3) (2).png>) | <p><strong>Work in progress lead time</strong> displays a comparison of your current aggregate WIP lead time breakdowns against your average lead time breakdowns for items that deployed in the same period. </p><p></p><p>Grey columns represent the average for deployed items, while red and green columns represent your current work in progress (red indicates that the current WIP value is at risk relative to the average).<br><br>This chart is responsive to selections made in the listing filter.</p> |
| ![](<.gitbook/assets/image (7).png>)     | <p><strong>Batch size breakdown</strong> groups your current work in progress by each of Sleuth's four batch size categories.<br><br>Large and Gigantic counts are outlined in red  when either is greater than 0.<br><br>This chart is responsive to selections made in the listing filter.</p>                                                                                                                                                                                                                    |
| ![](<.gitbook/assets/image (10).png>)    | <p><strong>Summary of work in progress</strong> summarized work in progress by showing the total count of all items, the total at risk, and the number of times that each risk type appears in your work in progress.<br><br>Clicking on the count for any risk type in this chart will set the listing filter to that risk type. It is not, however, responsive to selections made in the list filter.</p>                                                                                                         |

### Subscribe to daily work in progress risk digests

Daily WIP risk digests help ensure that teams are aware of and responding to risks on a daily basis.

#### Slack and Microsoft Teams digests

We recommend using our [Slack or Microsoft Teams digests](https://marketplace.sleuth.io/?search=work+in+progress) over the email digest because they can be delivered to a team's channel, where everyone can see an comment on them, and because they can be scheduled down the minute (e.g. to arrive in a team's channel just before their daily stand-up.).

<figure><img src=".gitbook/assets/image (131).png" alt=""><figcaption></figcaption></figure>

#### Email digests

If Slack or Microsoft Teams digests aren't an option, then email digests are a great alternative. Simply click on the notification bell on the top-right of the dashboard and select "Daily." The email digest will be sent to your email inbox each day if and only if there is at least one risk present in the work in progress dashboard. &#x20;

![](<.gitbook/assets/image (1) (2) (2).png>)

Note that the digest subscription is specific to your currently selected Team or Project context and  currently selected Environment. The date range for the email digest will always be the default look-back period of 28 days.&#x20;

<figure><img src=".gitbook/assets/image (2) (3).png" alt=""><figcaption></figcaption></figure>
