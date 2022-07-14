# Teams

While [projects](../projects/), [environments](../environment-support.md), and [deploys](../deploy-cards.md) represent the core "targets" of changes in Sleuth (and the DORA metrics associated with those changes), we also understand that Teams represent a critical dimension for interpreting DORA metrics and driving Team-level improvements over time.&#x20;

Teams often span multiple projects, and vice-versa (e.g. a platform team contributing to multiple projects, multiple micro-services teams contributing to the same project). In order to provide even more value to your Accelerate journey, Sleuth provides the optional ability to define team-centric lenses in addition to your project-level and org-wide views.

One benefit to team-centric views is that they can provide greater insight into the root causes (and recommended remediations) of changes to project-level DORA metrics (e.g. being able to trace a project-level increase in Change Failure Rate down to a particular contributing team).

But team-based views are about more than just understanding each team’s relative contributions to the projects they’re working on. Different teams often have their own unique processes, tools, and relevant targets for “what’s good” when it comes to measuring their performance against the DORA metrics, and so team-centric views provide an invaluable tool for enabling “apples-to-apples” measurements, comparisons, and improvements to each team’s DORA metrics over time.

With Teams, Sleuth user can:

* [Define teams and sub-teams](../../settings/organization/team-settings.md) in Sleuth
* Automatically maintain Sleuth teams using [GitHub Team Sync](../../settings/organization/team-settings.md#manage-teams-using-github-team-sync) (Enterprise-only)
* Track teams across projects with Team-centric DORA metrics dashboards
* Subscribe to [Team-centric email digests](../../notifications.md#to-set-up-at-the-team-level)
* Filter [Filter project-level DORA metrics dashboards](../projects/) by contributing teams
* View [team-level trends](../organization/trends.md) over time
* [Compare teams](../organization/compare.md) with other teams, projects, or labels (Enterprise-only)
* [Search by team](../organization/search.md)

![The Team Metrics dashboard displays Team-level DORA metrics along with breakdowns by "Projects contributed to" and "Sub teams"](<../../.gitbook/assets/image (10).png>)

Teams are managed and maintained from within Organization Settings. For information on how to set up and maintain your teams, sub-teams, and team members in Sleuth, refer to [Managing Teams](../../settings/organization/team-settings.md).&#x20;

Sleuth also allows users to subscribe to Team-centric digest emails. For more information on notifications, refer to [Slack and Email Notifications](../../notifications.md).&#x20;
