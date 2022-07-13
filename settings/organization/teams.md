# Teams

The **Teams** tab allows you to optionally define Teams, Sub-Teams, and Team membership. From this tab you can [manage teams manually](teams.md#undefined), or if your Teams are already represented in GitHub, then Sleuth can manage your teams automatically using [GitHub Team Sync](teams.md#manage-teams-manually-1).&#x20;

For more information on how Teams fit into Sleuth's Deployment tracking data model and why you might want to utilize them in your DORA journey, refer to [Teams](../../modeling-your-deployments/teams/).&#x20;

A few important things to note about Sleuth Teams:

* All team members in Sleuth must be licensed Contributors (or above). Standard plans include up to 50 Contributors, while Enterprise plans provide unlimited Contributors.
* One Member can belong to multiple Teams
* One Team can contribute to multiple Projects, and multiple Teams can contribute to the same Project (e.g. a platform team contributing to multiple Projects, or multiple micro-services Teams contributing to the same Project)
* Sleuth does not require users to explicitly associate Teams with Projects. Rather, Sleuth attributes Project-level metrics with Teams by looking for Team involvement in your underlying Deploys across Projects. Since Team's DORA metrics are calculated as an aggregation of all teams members' contributions to deploys, if a team member moves teams, then their “contributions” move with them. For more information on how Sleuth calculates Team-level metrics, refer to [How Sleuth Calculates Team-level Metrics](../../modeling-your-deployments/teams/how-sleuth-calculates-team-level-metrics.md).&#x20;

## Manage Teams Manually

To manually add Teams, Sub-Teams, and associated team Members, perform the following steps.

* From the **Teams** tab under **Organization Settings**, click _**Add Team**_
* Enter a **Team name** and leave the **Parent team** field empty.
* Click **Save**
* In the following screen, select **** the Sleuth **Members** you'd like to associate with this Team. This screen presents only existing Sleuth users, so if you can't find the user you're looking for, invite them to Sleuth using the [**Members**](members.md) tab
* To add a Sub-Team to this Team, repeat the prior steps, but select the first team as the **Parent team** for your sub-team. Sleuth will present your Teams and Sub-Teams in a collapsible/expansible tree structure.&#x20;

![](<../../.gitbook/assets/image (24).png>)

## Manage Teams using GitHub team Sync

If you're already managing your teams in GitHub, GitHub Team Sync can automatically keep your Teams, Sub-Teams, and Team Members in sync with changes you make in GitHub. This is particularly useful for customers managing many teams.&#x20;

{% hint style="info" %}
GitHub Team Sync is only available on the Enterprise plan.
{% endhint %}

Note that when using GitHub Team Sync, GitHub is the source of truth for team structures, and when enabled, you will not be able to add, edit, or delete teams, sub-teams, or team members from within Sleuth.  If you have teams already defined in Sleuth, those teams will be deleted from Sleuth and replaced by the team data that Sleuth receives from GitHub.

To enable GitHub Team Sync, perform the following steps:

* First, ensure that you have [enabled GitHub](../../integrations-1/code-deployment/github.md) as a code repository integration in Sleuth.&#x20;
* Once you've verified that the GitHub code repository integration is ednabled, from the **Teams** tab under **Organization Settings**, click the **Manage teams using GitHub** toggle to enable it.
* If you've already created teams manually in Sleuth, you will be presented with a warning that those teams will be deleted. Click **Enable Sync**.
* Sleuth will display a progress icon, and once the sync is complete, Sleuth will display the date and time when the last sync completed. Once complete, you should see all of your GitHub teams, sub-teams, and team memberships reflected in Sleuth.
* Sleuth will automatically refresh your GitHub teams every 24 hours at 2:00am UTC, but you can also force a refresh at any time by clicking **Sync now**. However, please note that the **Sync now** button can be used only once every 30 minutes.&#x20;

\


