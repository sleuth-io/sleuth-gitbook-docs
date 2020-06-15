# Bitbucket

## About the integration ![](../../../.gitbook/assets/bitbucket-2x-blue.png) 

Code deployments are one of the key sources of change Sleuth needs to do its job. Once a code deployment is integrated as a change of source, Sleuth immediately begins its analysis, looking at your commit history, number of authors, deploy frequency, size of commits, and other data to give you a full picture of how you and your team are managing your project's codebase. You'll instantly see the [Trend Graph](../../../resources/terminology.md#dashboard) come to life with a complete snapshot that gives you the information you need to start deploying faster.

Integrating Bitbucket with Sleuth is simple. If you're connecting to a personal Bitbucket repo, you just need your credentials. If you're part of a Bitbucket organization and aren't the owner, you will need permission to allow Sleuth to connect to the repo \(after you connect you'll be able to select individual private or public repositories\).

You can connect as many code deployments to a project as you'd like; be sure to give them recognizable names in Sleuth. You will also be able to tell Sleuth whether it should [manually register](../../manual-changes.md) each deploy or automatically create deploys [for every push to or tag on branch](../../../resources/terminology.md#deploy-tracking-type), it's completely up to you. This setting can be changed at any time. Additionally, you can configure your target branch to [lock](../../../resources/terminology.md#locking) if it contains unreleased code.

Check out the [GitHub](github.md), [GitLab](gitlab.md), [Jira](../../issue-trackers/jira.md), or [Clubhouse](../../issue-trackers/clubhouse.md) integration pages if you'd like to track your issues using those tools instead of or in addition to Bitbucket.

## Setting up the integration

To set up the Sleuth Bitbucket integration: 

1. Click **Integrations** in the left sidebar, then click **Change Sources**. 
2. In the _Bitbucket_ tile, click **connect**. 
3. You must grant Sleuth access to your Bitbucket account by clicking **Grant access** in the confirmation dialog. Don't worry, you'll select the Bitbucket repo to connect to your Sleuth project later.   ![](../../../.gitbook/assets/bitbucket-confirmation-dialog.png) 
4. On successful integration, you'll see _Bitbucket is connected as {Bitbucket user account}_ displayed in the Bitbucket tile, and the Bitbucket logo will turn green. You'll next configure the code deployment to connect your repo to a project. 

## Configuring the integration

You now need to add a Bitbucket repo to a Sleuth project. This source of change is the repo the configured Sleuth project will monitor and report in the [Dashboard](../../../dashboard.md) on each and every deploy you make to that repo, along with any other change sources you have connected to your project. 

To configure the Bitbucket integration: 

1. After step \#4 above, you will be taken back to the Bitbucket integration tile. On the Bitbucket tile, click the **Add code deployment** dropdown.   ![](../../../.gitbook/assets/bitbucket-add-code-deployment.png) 
2. Select the [Sleuth project](../../../projects.md) you wish to add a chance source to from the dropdown list.   ![](../../../.gitbook/assets/bitbucket-add-code-deployment-withdropdown.png) 
3. In the _Add a new Code Deployment change source_ screen, you must configure which code repo and branch to monitor; give the code deployment a name; select the [deploy tracking type](../../../resources/terminology.md#deploy-tracking-type); and tell Sleuth whether to [lock the target branch](../../../resources/terminology.md#deployment-locking) if it has unreleased code.  __![](../../../.gitbook/assets/bitbucket-add-code-deployment-change-source.png) 

## Removing the integration

#### If you wish to dissolve the Bitbucket integration for the organization: 

1. Click on **Integrations** in the left sidebar, then on **Change Sources**. 
2. In the Bitbucket integration card, click **disconnect**.

The Bitbucket integration is disconnected and no longer available to any projects within that organization. 

