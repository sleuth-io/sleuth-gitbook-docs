# Azure Pipelines

## About the integration

Azure Pipelines is the continuous integration tool provided by Azure. It allows you to build, test, deploy your application using automated jobs that are triggered manually or as a consequence of various interactions with your Azure DevOps repository.

It is assumed you already have an active Azure DevOps account and a repository with a working Azure Pipelines configuration.

## Setting up the integration

Refer to the [general instructions on adding Azure DevOps as a code integration](../../code-deployment/azure-devops.md).

You should also add at least one [Code deployment](../../../modeling-your-deployments/code-deployments/) based on a Azure repository so that we may use it as a source of Azure Pipelines builds.

## Configuring the integration

Once the integration is successful, find the **Impact sources** section in the sidebar and click the **+ Add **link nested under that section.

![](../../../.gitbook/assets/impact-sidebar.png)

Select **Azure DevOps** from the dropdown and continue by clicking **Enable and add**.

![](../../../.gitbook/assets/azure-devops-impact-build-provider.png)

Give this build tracking instance a **name** and select which **build** should be used to base the impact measurements on.

![](../../../.gitbook/assets/azure-impact-form.png)

That's it! Sleuth will now start verifying your deploys health by tracking whether the selected build is passing or failing. Head over to the Dashboard to start seeing your data in action in the project and deploy health graphs.

## Removing the integration

Refer to the [general instructions on adding Azure DevOps as a code integration](../../code-deployment/azure-devops.md).
