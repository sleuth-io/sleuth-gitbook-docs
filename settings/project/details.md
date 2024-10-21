# Details

The **Details** tab contains general information about the selected **project**. The name of selected project is displayed at the top of the sidebar. Select the "Switch to" dropdown to select a different project, if you have more than one.

<figure><img src="../../.gitbook/assets/image (70).png" alt=""><figcaption></figcaption></figure>

You can change the name of your project in the Details tab, along with an optional **Description** for the project. This is helpful if you are on a large team with multiple projects within the organization.

![](<../../.gitbook/assets/Project Settings - sleuth - Sleuth 2022-06-24 16-33-41.png>)

You can also change the default issue tracker for the selected project and, if a [Build](../../integrations-1/builds/) integration has been established, a default build server. Selecting a build server is optional, but at least one default [issue tracker](../../integrations-1/issue-trackers/) or [code deployment](../../integrations-1/code-deployment/) must be selected for your project. A link to enable an issue tracker is provided if the integration has not yet been made in the organization.

### Advanced settings

![](<../../.gitbook/assets/Screenshot 2023-10-20 at 11.41.28.png>)

#### Change failure rate boundary

This setting lets you define the lowest health state that should be considered a failure by Sleuth. It is used to calculate Failure rate and MTTR.

Raising this value (e.g. from _Unhealthy_ to _Incident_) will mean that fewer events will be classified as failures.

The correct setting very much depends on how you configured your impact sources and what your organization generally considers to be production failures.

#### Change failure sensitivity

This setting represents the amount of time (in minutes) a deploy must spend in a failure status (see Change failure rate boundary above for details) before it is determined a failure and will count towards the failure rate of the project.

The default setting is 7 minutes. Setting this value to a longer time means that fewer events will be classified as failures.

Using the default setting of 7 minutes, if any given deploy has had a failure registered for less than 7 minutes it will not count towards the failure rate of the project. If the failure status (e.g. an incident) has lasted for 7 minutes or longer, the deploy will now count towards the failure rate of the project.

#### Health autodetect sensitivity

This setting controls how many minutes Sleuth takes into account when auto-determining the health of a deploy. As a part of this health-check Sleuth will send notifications about said deploy.

Based on the selected setting (`Fine (6 minutes)`, `Normal (18 minutes)`, or `Coarse (30 minutes)`), Sleuth will take the selected number of minutes and divide that time into the max. number of 3-minute windows (_2, 6, or 10 respectively_). Sleuth will then calculate the **worst environment health in each individual window**, and finally calculate the **average of all the windows** to get to the final result.&#x20;

Important to note, that what is being calculated is the **ENVIRONMENT HEALTH**, not the deploy health. So the set period length doesn't start from the moment the deploy is registered forward, Sleuth actually looks backward, to the past X minutes from the moment the deploy was registered for an environment.

One way to illustrate how this works would be:

<figure><img src="../../.gitbook/assets/image (153).png" alt=""><figcaption></figcaption></figure>

Another important thing to note, this setting only pertains to `Error Impact Sources` and/or `Metric Impact Sources`,  if an `Incident Impact Source` is reporting an incident, that is taken at face value and no averages are calculated.

That is all to say, that the notification will **always be sent out around 6 minutes post deploy registration** in Sleuth, the difference is in **how big of a past time window** prior to the deploy being registered Sleuth should consider when determining whether the deploy is healthy or not.

If you set this to _Fine_, we will use less time to calculate the overall health of the environment and vice-versa if you set it to _Coarse_.

The best setting here will be a trade off between response time and detection reliability. If you're being alerted too often on account of minor anomalies, choose _Coarse_. If you want to be alerted sooner and with higher sensitivity, choose _Fine_.&#x20;

#### Change lead time settings

**Start definition**

See the detailed explanation of the different options

[#starting-clt-based-on-first-issue-transition](../../accelerate-metrics/change-lead-time.md#starting-clt-based-on-first-issue-transition "mention")

**Strict issue matching**

When enabled Sleuth will only look for issue references in PR titles and PR branch names. If strict issue matching is disabled, Sleuth will expand the search for issue references to PR descriptions and commit messages.

#### Locking

This setting lets you disable [deployment locking](../../modeling-your-deployments/code-deployments/deployment-locking.md) for all deployments in the project.

{% hint style="info" %}
Only certain members can create an integration for the organization. See [Access Control](../access-control.md) for more information.
{% endhint %}

Press **Save** after making any changes in the _Details_ tab.

#### Rollback detection

This setting allows you to disable [rollback detection](../../modeling-your-deployments/code-deployments/rollbacks.md). There are some scenarios where you don't want Sleuth to detect rollbacks or include them as change failures.&#x20;
