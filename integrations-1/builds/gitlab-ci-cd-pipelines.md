# GitLab CI/CD Pipelines

## About the integration

The GitLab CI/CD Pipelines integration provides Sleuth with the ability to track your GitLab CI/CD Pipelines builds and associate them with your corresponding Sleuth deploys. Once configured, the integration silently monitors your deployment activity, and ties your GitLab CI/CD Pipelines builds with associated deployments you make to your integrated code deploys by matching the git SHAs from your code repos. Sleuth then shows you a snapshot of your build state at the time of deploy.

## Setting up the integration

GitLab CI/CD Pipelines integration reuses the same credentials used to connect [GitLab](../code-deployment/gitlab.md).

## Configuring the integration

To configure the Gitlab CI/CD Pipelines integration, you will need to set a default build server:

1. Click **Integrations** in the sidebar, then click the **CI/CD** tab.
2. Click the **Set default build server** dropdown.\
   ![](<../../.gitbook/assets/Integrations - Sleuth 2021-10-12 11-25-56.png>)
3. Select a project to set as the default build server. You'll need to add a code deployment to the selected project if you haven't already done so.

Now that the GitLab CI/CD Pipelines integration is configured, you will begin seeing information displayed in the Builds tab of a [deploy](../../modeling-your-deployments/deploy-cards.md).
