# Jenkins

## About the integration

The Jenkins integration provides Sleuth with the ability to track your Jenkins builds and associate them with your corresponding Sleuth deploys. Once configured, the Sleuth Jenkins integration silently monitors your deployment activity, and ties your Jenkins builds with associated deployments you make to your integrated change sources by matching the git SHAs from your code repos. Sleuth then shows you a snapshot of your build state at the time of deploy.

## Setting up the integration

To add the Sleuth Jenkins integration:

1. Click **Integrations** in the profile drop-down (top right).
2.  Select "CI/CD" in the drop-down, then click **enable** in the Jenkins card.\


    <figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>
3. Enter your Jenkins instance publicly accessible URL, your username and API token, then press **Save**. You can generate the API token through Jenkins UI at `<YOUR_JENKINS_URL>/user/<YOUR_USERNAME>/configure`
4.  On successful integration, you'll see new **Jenkins connection** displayed in the Jenkins tile. You'll configure the default build server later.\


    <figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

### Custom HTTP headers

If you using Jenkins on-premise behind Cloudflare access or similar, Sleuth might need to include some HTTP headers in order to reach your instance. In order to set Sleuth to send any custom HTTP headers when making requests:

1. In the Jenkins dialog, click on the **Advanced setting**
2. Enter comma separated list of custom headers you want Sleuth to include

## Configuring the integration

To configure the Jenkins integration, you will need to set a default build server:

1. Click **Integrations** in the profile drop-down (top right).
2. Click the **Set default build server** drop-down.

![](<../../.gitbook/assets/image (76).png>)

1. Select a project to set as the default build server. You'll need to add a code deployment to the selected project if you haven't already done so.

Now that the Jenkins integration is configured, you will begin seeing information displayed in the Builds tab of a [deploy](../../modeling-your-deployments/deploy-cards.md).
