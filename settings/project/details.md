# Details

The **Details** tab contains general information about the selected **project**. The name of selected project is displayed at the top of the sidebar. Select the "Switch to" dropdown to select a different project, if you have more than one.

<figure><img src="../../.gitbook/assets/image (70).png" alt=""><figcaption></figcaption></figure>

You can change the name of your project in the Details tab, along with an optional **Description** for the project. This is helpful if you are on a large team with multiple projects within the organization.

![](<../../.gitbook/assets/Project Settings - sleuth - Sleuth 2022-06-24 16-33-41.png>)

You can also change the default issue tracker for the selected project and, if a [Build](../../integrations-1/builds/) integration has been established, a default build server. Selecting a build server is optional, but at least one default [issue tracker](../../integrations-1/issue-trackers/) or [code deployment](../../integrations-1/code-deployment/) must be selected for your project. A link to enable an issue tracker is provided if the integration has not yet been made in the organization.

### Advanced settings

![](<../../.gitbook/assets/Project Settings - sleuth - Sleuth 2022-06-24 16-29-57.png>)

#### Change failure rate boundary

This setting lets you define the lowest health state that should be considered a failure by Sleuth. It is used to calculate Failure rate and MTTR.

Raising this value (e.g. from _Unhealthy_ to _Incident_) will mean that fewer events will be classified as failures.

The correct setting very much depends on how you configured your impact sources and what your organization generally considers to be production failures.

#### Change failure sensitivity

This setting represents the amount of time (in minutes) a deploy must spend in a failure status (see Change failure rate boundary above for details) before it is determined a failure.

Setting this value to a longer time means that fewer events will be classified as failures.

#### Health autodetect sensitivity

This setting controls how many minutes Sleuth takes into account when auto-determining the health of a deploy. Measurements are usually collected every two minutes.

If you set this to _Fine_, we will use less time to calculate the overall health of the environment and vice-versa if you set it to _Coarse_.

The best setting here will be a trade off between response time and detection reliability. If you're being alerted too often on account of minor anomalies, choose _Coarse_. If you want to be alerted sooner and with higher sensitivity, choose _Fine_.&#x20;

#### Locking

This setting lets you disable [deployment locking](../../modeling-your-deployments/code-deployments/deployment-locking.md) for all deployments in the project.

{% hint style="info" %}
Only certain members can create an integration for the organization. See [Access Control](../access-control.md) for more information.
{% endhint %}

Press **Save** after making any changes in the _Details_ tab.

#### Rollback detection

This setting allows you to disable [rollback detection](../../modeling-your-deployments/code-deployments/rollbacks.md). There are some scenarios where you don't want Sleuth to detect rollbacks or include them as change failures.&#x20;
