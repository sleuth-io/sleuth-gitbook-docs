# GitHub

## About the integration <img src="../../.gitbook/assets/github-mark-120px-plus.png" alt="" data-size="line">

Integrating GitHub with Sleuth is simple. If you're connecting to a personal GitHub repo, you just need your credentials. If you're part of a GitHub organization and aren't the owner, you will need permission to allow Sleuth to connect to the repo (_after you connect you'll be able to select individual private or public repositories_).

If you are using GitHub issues to track issues, Sleuth will automatically discover your referenced issues once the integration is configured. You can still use other [issue tracker integrations](../issue-trackers/) if you don't use GitHub issues.

{% hint style="info" %}
Check out the Sleuth app in the [GitHub marketplace](https://github.com/marketplace/sleuth-deployment-tracking).
{% endhint %}

## Setting up the integration

To set up the Sleuth GitHub integration:

1. Click **Add** in the top navigation bar and select **Integration** from the list.
2. Select **Code** from the drop-down located in the top right.
3. In the **GitHub** tile, click **Enable**.
4. Select the account with which you wish to authenticate your GitHub integration.
5. Select the repositories you wish to grant Sleuth access to by clicking either **All repositories** or **Only select repositories**. Note that if you choose **Only select repositories**, Sleuth will only be able to see and track deploys from the repos you select.\
   ![](<../../.gitbook/assets/image (122).png>)
6. Click **Install & Authorize**.
7.  Upon successful integration, you'll see **GitHub** marked as **Enabled** and a list of connections (_you can have more than one_) specified in the format **Connected via GitHub App (account `<GitHub user account>` for \_\_\_\_\_\_\_\_\_\_\_\_\_\_ repos.**&#x20;

    <figure><img src="../../.gitbook/assets/image (119).png" alt=""><figcaption></figcaption></figure>

## Configuring the integration

After the initial setup is complete, the GitHub integration can be used to set up:

* a **code deployment**: select a Sleuth project from the list and then follow the instructions for [creating a code deployment](https://help.sleuth.io/modeling-your-deployments/code-deployments/creating-a-deployment)
* a **build server**: select a Sleuth project from the list to set GitHub as the `Build integration provider` for the selected project
* an **issue tracker**: select a Sleuth project from the list to set GitHub as the `Issue integration provider` for the selected project

<figure><img src="../../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Adding more repositories

If you've selected **Only select repositories** during your initial setup and now want to give Sleuth access to more repositories, simply navigate to the **Integrations** page (_click the **Add** button in the top nav and then click **Integrations**_), click the arrow to expand the **GitHub** tile, and follow the **Inspect** link next to the connection you wish to update.

<figure><img src="../../.gitbook/assets/image (120).png" alt=""><figcaption></figcaption></figure>

This will take you to GitHub installation's page where you can update your preferences.



## In case of major changes to your GitHub organization

Making significant changes to your GitHub organization, such as **renaming the organization**, shouldn't have any effect on your existing GitHub-based code deployments and deploy data in Sleuth.&#x20;

As per [GitHub's official documentation](https://docs.github.com/en/organizations/managing-organization-settings/renaming-an-organization), any attempt to access links containing the old organization name should get automatically redirected.

That being said, if you want to be extra sure, you can always disconnect your GitHub integration in Sleuth and re-connect it after the renaming, which will ensure Sleuth has the most up-to-date org info. You are also welcome to let our Support Team know of this change, so they can help ensure a smooth transition.

## Removing the integration

#### If you wish to remove the GitHub integration for the organization:

1. Click the **Add** button in the top nav and select **Integrations** from the list.
2. Expand the **GitHub** integration card, and click **Remove** next to the connection you wish to remove. If you want to remove all of your GitHub connections, you'll need to repeat this step for each connection. A confirmation screen will appear warning you of the consequences of this action and prompting you to confirm your decision -> click **Confirm**.

After all connections are removed, the GitHub integration is then disconnected and no longer available for any projects within that organization.
