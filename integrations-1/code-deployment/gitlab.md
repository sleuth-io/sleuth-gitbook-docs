# GitLab

## About the integration <img src="../../.gitbook/assets/gitlab-logo.svg" alt="" data-size="line">

Integrating GitLab with Sleuth is simple. If you're connecting to a personal GitLab repo, you just need your credentials. If you're part of an organization and aren't the owner, you will need permission to allow Sleuth to connect to the repo—after you connect you'll be able to select individual private or public repositories.

{% hint style="info" %}
Be sure your account has at least [maintainer privileges](https://docs.gitlab.com/ee/development/permissions.html#members). We query for `min_access_level=40`
{% endhint %}

#### Check out this video by Sleuth CTO Don Brown on how to get started with Sleuth and GitLab

{% embed url="https://www.youtube.com/embed/jV3RkebZJIA" %}

## Setting up the integration

To set up the GitLab integration:

1. Click **Integrations** in the left sidebar, then select **Code** in the dropdown at the top-right to filter the view.
2. In the _GitLab_ tile, click **Enable**.
3. You must grant Sleuth access to your GitLab account. Don't worry, you'll select the GitLab repo to connect to your Sleuth project later.\
   ![](<../../.gitbook/assets/image (10) (2).png>)
4. On successful integration, _GitLab enabled_ will be displayed in the GitLab tile. You'll next configure the code deployment to connect your repo to a project.

### Custom HTTP headers

If you using GitLab on-premise behind Cloudflare access or similar, Sleuth might need to include some HTTP headers in order to reach your instance. In order to set Sleuth to send any custom HTTP headers when making requests:

1. In the GitLab dialog, click on the **Advanced setting**
2. Enter comma separated list of custom headers you want Sleuth to include

### Read-only mode

GitLab can be configured in read-only mode, making use of a read-only token from GitLab. Several Sleuth features such as deployment locking and some Sleuth Action automations may be disabled, but if your security team requires integrations to be read-only, this may be necessary.

1. In the GitLab dialog, click on **Advanced settings** and check **Read-only** checkbox.
2. Continue to add a new code deployment as usual.
3. Now, you'll need to manually configure the GitLab webhook so that Sleuth is notified about key events. Visit the code deployment page, click on the cog at the top right and select **Get webhook instructions**\
   ![](<../../.gitbook/assets/image (12) (2).png>)\\
4. Copy the webhook URL, secret, and note the events for later
5. Visit your GitLab repository settings and click on **Webhooks**
6. Create a new webhook, using the URL and secret from the earlier dialog, and check the events that match with the requested list\
   ![](<../../.gitbook/assets/image (11) (1).png>)
7. Save the new webhook and now Sleuth should receive the required GitLab events.

Steps 3 through 7 need to be done for each GitLab repository

## Configuring the integration

You now need to add a [code deployment](../../modeling-your-deployments/code-deployments/) for your GitLab repo to a Sleuth [project](../../modeling-your-deployments/projects/). Once configured and you start [registering deploys](../../modeling-your-deployments/code-deployments/how-to-register-a-deploy.md) Sleuth will be tracking deploys for your code changes.To configure the GitLab integration:

1. After step #4 above, you will be taken back to the GitLab integration tile. On the GitLab tile, click the **Add code deployment** dropdown.
2. Select the [Sleuth project](../../modeling-your-deployments/projects/) you wish to add a chance source to from the dropdown list.
3. Follow the instructions for [setting up a new code deployment](../../settings/project/code-deployments.md)

## Removing the integration

#### If you wish to dissolve the **GitLab** integration for the organization:

1. Click on **Integrations** in the left sidebar, then on **Change Sources**.
2. In the GitLab integration card, click **disable**.

The GitLab integration is disconnected and no longer available to any projects within that organization.
