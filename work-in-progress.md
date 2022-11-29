# Work in Progress

In addition to tracking deploy metrics, Sleuth also provides **Work in Progress** dashboards for Teams and Projects that provide real-time visibility into in-flight work (i.e. work that has not yet deployed) and highlights risks that you can address right now.&#x20;

<figure><img src=".gitbook/assets/image (53).png" alt=""><figcaption><p>Work in Progress dashboard</p></figcaption></figure>

### What is "Work in Progress"?

Work in Progress, or WIP, includes any PRs or Future Deploys that have not yet deployed to their target environment (where "Future Deploy" is a Sleuth construct that is essentially a container for PRs that have merge but have not yet deployed).&#x20;

### Understanding "at-risk" items

While the **Work in Progress** dashboards present in-flight work in part to provide general visibility into the changes that are likely deploy next, the real value of these dashboard is that they highlight "at risk" items that are likely to have a negative impact on your DORA metrics. This early risk identification allows you to take immediate corrective actions on at-risk items before they ship, driving tactical improvements to your DORA metrics.&#x20;

Sleuth currently highlights the following risk types:

* Batch Size
* Total CLT
* Coding time
* Review lag time
* Review time
* Waiting to deploy

For Batch Size, an item is considered "at risk" if it is either Large or Gigantic.

For CLT and each of its composite breakdowns, an item is considered "at risk" if it's current value exceeds your rolling average by more than 20% (i.e. your rolling average for the prior period of the same length as your current work-in-progress data range selection).

### Understanding Work in Progress filters

Just like the Metrics Dashboards for Projects and teams, the Work in Progress dashboard can be filtered using global filters for Date Range, Projects, Teams, Environments, and Deployments. These filters impact the specific PRs and Future deploy that display in the listing as well as the data that is displayed in the dashboard charts.

### Understanding Work in Progress charts

* **Work in progress lead time** displays a side-by-side comparison of your current CLT values against your "baseline" CLT values from the prior period of the same length.&#x20;
* **Summary of work in progress** displays a the total count work in progress items (PRs and Future Deploys) included in your current global filter selections versus the subset of those that Sleuth has determined to be "at risk".
* **Batch size breakdown** breaks down your current work in progress by each of Sleuth's four batch size categories.
* **Current work in progress lead time** and **Baseline lead time** show similar information as **Work in progress lead time** but with a broken-out view that is better suited to comparing the baseline CLT values against the item-by-item WIP CLT values that appear in the listing.

