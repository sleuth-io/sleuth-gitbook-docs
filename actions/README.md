# Sleuth Actions (legacy)

{% hint style="warning" %}
**Sleuth Actions is evolving into Automations Marketplace 🛹 🛵 🚀**

Sleuth is laser-focused on delivering a first-class developer automation capability, and we're doing it with our new [**Automations Marketplace**](../automations-marketplace/) **⚡️**

\
Automtaions Marketplace is where it's at because:\
\
&#x20; 1\.   Marketplace automations can be installed, edited, and removed right in Sleuth!

2. Sleuth can suggest Marketplace automations based on your current bottlenecks!&#x20;
3. Sleuth shows you how Marketplace automations are impacting your metrics!



All that said, we're continuing to support Sleuth Actions for now because, in certain cases, it can still be more expressive than our already highly-configurable Marketplace automations.&#x20;

But let's also be frank: Sleuth Actions is clunky. You'll have to drop Sleuth Action YAML files into all of the code repos you want them in, and depending on your PR process, you might have to issue PRs to add, modify, or remove them. Sounds a little like our competition, right? 🔥

We're hard at work right now on providing you the ability to define your own Marketplace automations with YAML, giving you all the flexibility of legacy Sleuth Actions plus all of the added benefits of Marketplace automations. And since "a rising tide lifts all boats," we're also planning to let you share your custom automations with other Sleuth customers!&#x20;

Stay tuned, and in the meantime, please [send us your feedback](mailto:support@sleuth.io)!
{% endhint %}

Sleuth Actions is an automation engine to help you to define and automate the workflow and actions you’re likely already doing by convention today. Some examples are:

* seeking approvals before promoting from your staging to production environment
* using PR labels to fast-track a change through to prod
* sending custom Slack notifications when a specific set of conditions are true of a deploy

Execute actions by defining a set of rules for your repository, containing conditions and actions to take when those conditions are met. Rules are defined by a YAML file in your code repository, located at `.sleuth/rules.yml`, and include zero or more conditions, as well as one or more actions to take when those conditions are met. Rules are triggered by events such as a code deployment or a deploy being determined to be healthy.

Here's an example `.sleuth/rules.yml`:

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

A rule can be named whatever you want, `stage-to-prod` in this example, and can have a description to display in the Sleuth interface. The actions used here automatically approve a pending build and then send a notification to the Slack deployment message thread. Another common action is [webhook](webhook.md), used to notify external systems.

For more information, including what condition variables and actions are available, within Sleuth, click on "Help" and then "Actions".

For more ideas on what tasks can be automated, see [our cookbook](cookbook.md).

{% hint style="info" %}
Sleuth actions is in beta and is undergoing rapid development. If you'd like to participate just drop us a line via email at support@sleuth.io.
{% endhint %}
