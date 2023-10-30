# Custom Git

## About the integration

If your Git hosting application isn't supported or if your repository is not internet-accessible, you can still connect it to Sleuth through the 'Custom Git' option.

## Configuring the integration

You can add a [code deployment](../../modeling-your-deployments/code-deployments/) for your git repository to a Sleuth [project](../../modeling-your-deployments/projects/). Once configured and you start [registering deploys](../../modeling-your-deployments/code-deployments/how-to-register-a-deploy.md), Sleuth will be tracking deploys for your code changes.

To configure the custom Git integration:

1. Start the process for creating a new code deployment (see [instructions](../../settings/project/code-deployments.md)).
2. When asked to select the repository provider, pick **Custom (any git repository)** and click **Continue**.
3. Enter the code deployment name and click **Save and continue** to create the code deployment source.
4. Finally, click on the link in the "Waiting for new deploy" instructions to see how to use the [Sleuth CLI client](https://github.com/sleuth-io/sleuth-client).&#x20;
