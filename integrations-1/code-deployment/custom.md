# Custom Git

## About the integration

If your Git hosting application isn't supported or if your repository is not internet-accessible, you can still connect it to Sleuth through the 'Custom Git' option.

{% hint style="info" %}
Because Sleuth won't have access to your repository, Sleuth won't know about associated pull requests. This means features such as the deploy timeline and metrics will only take into account commits, but not also pull requests.
{% endhint %}

## Configuring the integration

You can add a [code deployment](../../modeling-your-deployments/code-deployments/) for your git repository to a Sleuth [project](../../modeling-your-deployments/projects/). Once configured and you start [registering deploys](../../modeling-your-deployments/code-deployments/how-to-register-a-deploy.md), Sleuth will be tracking deploys for your code changes.

To configure the custom Git integration:

1. Start the process for creating a new code deployment \(see [instructions](../../settings/project/code-deployments.md)\)
2. If this is your first repository, select **Custom** in the repository type dropdown list. If instead you were taken to the repository selector page, click on the **connect** link in the right sidebar, and then select **Custom** in the repository type dropdown list.
3. Enter the code deployment name and click **create** to create the code deployment source.
4. Finally, click on the link in the "Waiting for new deploy" instructions to see how to use the [Sleuth CLI client](https://github.com/sleuth-io/sleuth-client) or API directly to register deploys.

