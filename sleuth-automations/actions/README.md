# Custom Automations

Sleuth's Custom Automations framework allows you to build bespoke automations to suit your organization's specific workflows by putting our powerful and highly expressive YAML-based automation capability into your hands.&#x20;

### How it works

All of the automations in Sleuth's [Automations Marketplace](../automations-marketplace/) are built on an underlying YAML-based rules framework that allows you to define an automation by combining one or more **triggers** (e.g. a PR update, a code deployment, or a user-defined schedule), **conditions** (e.g. a code deployment is "healthy"), and **actions** (e.g. send a Slack message, trigger a build). Here's an example of what an automation rule might look like in YAML:

```
rules:
  - stage-to-prod:
      description: Automatically promotes a healthy staging deployment to production
      conditions:
        - environment='Staging'
        - health='Healthy'
        - deployed_for>'10m'
      actions:
        - auto_approve_build: test-and-deploy
        - add_to_deploy_message_thread: >-
            Build promoted automatically on a healthy staging deploy
```

A rule can be named whatever you want, `stage-to-prod` in this example, and can have a description to display in the Sleuth interface. In this example, the automation's conditions check that a deploy has soaked healthily for a specified amount of time, and then the actions automatically approve a pending build to the next environment and send a notification to the Slack deployment message thread. Another common and powerful action is the [webhook](webhook.md), which can be used to notify external systems.

For more ideas on what tasks can be automated, see [our cookbook](cookbook.md).

### Two methods for installing and maintaining custom automations

There are two ways to install and maintain custom automations.&#x20;

#### Method 1: Add a YAML file to your code repositories&#x20;

The first method is to define your rules in a YAML file and then insert that YAML file into each code repository where you want those rules to be evaluated (located at `.sleuth/rules.yml`). The advantage of this approach is that you can modify your custom automations "as code" (e.g. enforcing your SDLC process around changes to rules and ensuring preservation of historical states). The disadvantage is that it's more effort to deploy rules to multiple repositories (since each requires its own rules.yaml file) and to make changes to rules over time (since rules changes will be treated like any other code changes).

#### Method 1: Add custom automations from Marketplace

The second method is to use the [Custom Automation template](https://marketplace.sleuth.io/?filter=custom) provided in Sleuth's Automations Marketplace.

&#x20;![](<../../.gitbook/assets/image (1) (1) (1) (1).png>)

This option allows you to quickly write a new automation (using YAML) and deploy it to multiple teams or projects, all from within Sleuth's UI. You can also modify or uninstall those automations quickly from within Sleuth's UI.&#x20;

This option is great for quickly experimenting with automations, putting them out to team quickly, tweaking them based on feedback, and if they aren't producing the intended effect, removing them as quickly as you added them. While this option streamlines experimentation by removing the need to manually add a rules.yaml files to multiple repositories or to issue pull requests each time you want to change those rules, it might not conform to some organizations' policies for managing "rules as code".

The quickest way to get started with custom automations is to copy the YAML either from an existing automation or from our automations [cookbook](https://help.sleuth.io/sleuth-automations/actions), then tweak it to meet your organization's unique needs. Access the YAML for any existing automation on the Marketplace by navigating to its YAML tab as shown here:

<figure><img src="../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>



### Ready to automate?

For detailed information on the YAML-based framework, including what specific triggers, condition variables, and actions are available, click on "Help" from within Sleuth, then click "Custom Automations".

