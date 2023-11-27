# Azure DevOps

## About the integration <img src="../../.gitbook/assets/devops.png" alt="" data-size="line">

Integrating Azure DevOps with Sleuth is simple. If you're connecting to a personal Azure DevOps repo, you just need your credentials. If you're part of an organization and aren't the owner, you will need permission to allow Sleuth to connect to the repo—after you connect you'll be able to select individual private or public repositories.

The integration is best tested against Azure DevOps Services, however, it should work for Azure DevOps Server as well. Which is which?

* Azure DevOps Services (formerly known as Visual Studio Team Services, or VSTS\_)\_ is a cloud-based solution
* Azure DevOps Server (formerly known as Team Foundation Server, or TFS) is an on-premises offering

## Setting up the integration

To set up the Azure DevOps integration:

1. Click **Add** in the top navigation bar and select **Integration** from the list.
2. Select **Code** from the drop-down located in the top right.
3. In the **Azure DevOps** tile, click **Enable**.
4. Enter the details of the account with which you wish to authenticate your Azure DevOps integration. You will have the chance to select specific repo(s) for your Sleuth project(s) later.\
   ![](<../../.gitbook/assets/image (4).png>)
5. In a separate browser tab or window, visit your Azure DevOps account, and under **User settings**, click on **Personal Access Tokens** and generate a token with the required scopes. The `Work Items` and `Build` scopes are only necessary if you want to configure issue and build integration. Once generated, paste the token into the Sleuth form and click **Save**.
6.  On successful integration, you'll see **Azure DevOps** marked as **Enabled** and there will be a list of connections (_you can have more than one_) displayed on the tile when expanded:\


    <figure><img src="../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Custom HTTP headers

If you using Azure DevOps on-premise behind Cloudflare access or similar, Sleuth might need to include some HTTP headers in order to reach your instance. In order to set Sleuth to send any custom HTTP headers when making requests:

1. In the Azure DevOps dialog, click on the **Advanced setting**.
2. Enter a comma-separated list of custom headers you want Sleuth to include.

## Configuring the integration

After the initial setup is complete, the Azure DevOps integration can be used to set up:

* a **code deployment**: select a Sleuth project from the list and then follow the instructions for [creating a code deployment](https://help.sleuth.io/modeling-your-deployments/code-deployments/creating-a-deployment)
* a **build server**: select a Sleuth project from the list to set AzureDevops as the `Build integration provider` for the selected project
* an **issue tracker**: select a Sleuth project from the list to set AzureDevops as the `Issue integration provider` for the selected project

<figure><img src="../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Removing the integration

#### If you wish to remove the **Azure DevOps** integration for the organization:

1. Click the **Add** button in the top nav and select **Integrations** from the list.
2. Expand the **Azure DevOps** integration card, and click **Remove** next to the connection you wish to remove. If you want to remove all of your Azure DevOps connections, you'll need to repeat this step for each connection. A confirmation screen will appear warning you of the consequences of this action and prompting you to confirm your decision -> click **Confirm**.

After all connections are removed, the Azure DevOps integration is disconnected and no longer available for any projects within that organization.
