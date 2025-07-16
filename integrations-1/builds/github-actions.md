# Github Actions

## About the integration

The Github Actions integration provides Sleuth with the ability to track your Github Actions and associate them with your corresponding Sleuth deploys. Once configured, the integration silently monitors your deployment activity, and ties your Github workflows with associated deployments you make to your integrated change sources by matching the git SHAs from your code repos. Sleuth then shows you a snapshot of your build state at the time of deploy.

## Setting up the integration

Github Actions integration reuses the same credentials used to connect [Github Code integration](../code-deployment/github.md#setting-up-the-integration).

## Using the integration

After the initial setup is complete, the GitHub Actions integration can be used in your code deployment's configuration.

To use GitHub Actions as your CI/CD provider either create a new code deployment, or edit an existing one to get to this screen:

<figure><img src="../../.gitbook/assets/image (156).png" alt=""><figcaption></figcaption></figure>

Select the GitHub Actions as your provider by clicking on the `GitHub` tile and then click `Continue` . On the next screen, select the workflow(s) / job(s) to track for each environment in your Project:

<figure><img src="../../.gitbook/assets/image (157).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
You can either select a whole workflow, meaning that each time the entire workflow finished successfully, Sleuth will consider that to be a new deploy, or a particular step/job within a workflow, meaning that when the particular chosen step/job finishes successfully, Sleuth will register that as a new deploy.
{% endhint %}

### Advanced settings

Each build mapping has an `Advanced` section, which is collapsed by default. Expanding it reveals the following options:

<figure><img src="../../.gitbook/assets/image (158).png" alt=""><figcaption></figcaption></figure>

* `Workflow`: If your desired workflow is not selectable from the dropdown, you can enter its name in this field, and if any workflow runs match this value, Sleuth will register a deploy.
* `Job`: There are several scenarios where this field can be useful:
  * If your desired job is not selectable from the dropdown, you can enter its name in this field,
  * If you have nested jobs with fixed names, you can enter the concatenated string, using the following syntax: Top-Level Job / Sub-Level Job
  * If you have nested jobs with dynamically generated names for the Sub-Level Jobs, you can enter the Top-Level Job's name as a prefix followed by `/*` , e.g. `Top-Level Job /*` , this will catch all builds where the job's name start with `Top-Level Job`&#x20;
* `Build and environment branches must match`: You can toggle whether or not you want only builds runing against the branch, mapped to your environment to count as new deploys, or if you want **all builds** for this workflow to count as a deploy, regardless of the branch they run on/against
