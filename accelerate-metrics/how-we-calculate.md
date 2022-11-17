# Interpreting Metrics in Sleuth

In order to trust and effectively improve your DORA metrics, it's helpful to understand exactly how Sleuth calculates and presents each of the four DORA metrics throughout its various dashboards and views.

This article expands on the descriptions of the four core DORA metric calculations already described on the preceding pages, and we highly recommend familiarizing yourself with these before reading on:

* [Deploy Frequency](deploy-frequency.md) (and included discussion of [Batch size breakdown](deploy-frequency.md#batch-size-breakdowns))
* [Change lead time](how-we-calculate.md#change-lead-time)
* [Change failure rate](how-we-calculate.md#change-failure-rate)
* [MTTR](mttr.md)

Parts of this article also assume a basic familiarity with Sleuth's [Project Metrics](../modeling-your-deployments/projects/), [Team Metrics](../modeling-your-deployments/teams.md), and [Trends](../modeling-your-deployments/organization/trends.md) dashboards.

## Interpreting "Percent Change" in Sleuth

### Percent Change for Project Metrics and Team Metrics&#x20;

In both the [**Project Metrics**](../modeling-your-deployments/projects/) and [**Team Metrics**](../modeling-your-deployments/teams.md) dashboards, Sleuth provides the ability to filter by a specific target date range. Sleuth then displays 2 lines within each of the four DORA charts, one for the currently selected period and a second for the prior period of the same length. This overlay is great for comparing and zooming-in on specific points in time, however, what's often more important is understanding how the current period compares _overall_ against the prior period.&#x20;

In addition to plotting the currently selected period and the prior period as two distinct timelines on each graph, Sleuth also displays an overall "percent change" at the top of each graph to help you see at-a-glance how the _average_ for the selected period compares to the _average_ of the prior period.

![Percent change is displayed from prior period to current period](<../.gitbook/assets/image (8).png>)

On both the [**Project Metrics**](../modeling-your-deployments/projects/) and [**Team Metrics**](../modeling-your-deployments/teams.md) dashboards, percent change is calculated as follows:

* First, Sleuth calculates the net difference between the two periods by subtracting the average for the prior period from the average for the currently selected period.
* Then, Sleuth calculates the percent change by dividing this net difference by the average for the prior period and multiplying that result by 100

### Percent Change for the Trends dashboard

The [**Trends**](../modeling-your-deployments/organization/trends.md) **** dashboard also displays percent change for each of the four DORA metrics, but the calculation for percent change here differs slightly from the Project Metrics and Team Metrics dashboards in that the Trends dashboard display only one period of time (i.e. has no concept of a "prior period" in tis comparison.&#x20;

![Percent change is displayed on the Trends dashboard](<../.gitbook/assets/image (6) (2).png>)

For the Trends dashboard, Sleuth calculates percent change by splitting the selected period into two equal halves and calculating the average for each half. From there, the calculation of percent change is similar to the one described for the Project Metrics and Team Metrics dashboards above.&#x20;

## Interpreting Team-level Metrics

Sleuth does not require users to explicitly associate Teams with Projects. Rather, when calculating Team-level metrics, Sleuth automatically infers which Teams are contributing to which Projects by searching for Team Members within Deploys (and in the case of Code Change Deploys, by searching within the underlying PRs, Branches, Builds, and Issues included in those Deploys). If any Team Member is included as an author on a PR, Branch, or Build within a Deploy, as an owner of an linked Issues listed in the Deploy, or as the initiator of the Deploy itself, then Sleuth will include the entirety of that Deploy in its calculation of Team level-metrics for all Teams to which that Team Member belongs.

![Sleuth detects team members directly within change sources ](<../.gitbook/assets/Sleuth Data Model for Teams 2.jpg>)

As such, Sleuth can present powerful DORA metric "intersections" that show each Team's relative contribution to the DORA metrics for the Projects they're working on. This is evident in views such [Team Metrics](../modeling-your-deployments/teams.md) dashboard's **Projects contributed to** panel below, which shows the DORA metrics at the specific intersection of _this Team_ and _those Projects_.  &#x20;

![The Team Metrics dashboard shows DORA metrics for the specific intersections between the selected team and the specific projects to which they're contributing](<../.gitbook/assets/image (15).png>)

Similarly, from within the [Project Metrics](../modeling-your-deployments/projects/) dashboard, Sleuth presents a view into **Contributing teams** and their relative impacts on that Project's metrics.&#x20;

![The Project Metrics dashboard shows DORA metrics for each team's specific contributions to the project ](<../.gitbook/assets/image (26).png>)

## Interpreting Averages across Multiple Projects

When viewing metric averages across multiple Projects in Sleuth, it's important to note that Sleuth calculates cross-Project averages based on the underlying Deploys within each Project.&#x20;

So, for example, if _Project A_ has 2 deploys and _Project B_ has 7 deploys, Sleuth will calculate the average CLT across both Projects by adding the CLT for all 9 Deploys and then dividing that sum by 9 (the total number of Deploys across both Projects).&#x20;

This produces an average CLT result that in most cases will not be equal to the result of adding up the Project-level CLTs and dividing that sum by 2 (the total number of Projects). Sleuth has been intentionally designed around a Deploy-centric point of view, and we believe this Deploy-level handling of cross-project averages provides the most accurate representation of customers' DORA metrics across Projects. &#x20;

Some specific use cases where this applies include:

* Viewing multiple Projects on the **Trends** dashboard
* Using **Labels** to view cross-project metrics
* Viewing **Team-level metrics** for Teams working on multiple Projects
* Passing multiple Project slugs into the **Sleuth API**
