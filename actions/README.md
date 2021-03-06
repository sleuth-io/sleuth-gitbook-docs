---
description: How to use automate deploy workflows with Sleuth Actions
---

# Deploy workflows \(beta\)

Sleuth Actions is an automation engine to help you to define and automate the workflow and actions you’re likely already doing by convention today. Some examples are:

* seeking approvals before promoting from your staging to production environment
* using PR labels to fast-track a change through to prod
* sending custom Slack notifications when a specific set of conditions are true of a deploy

Execute actions by defining a set of rules for your repository, containing conditions and actions to take when those conditions are met. Rules are defined by a YAML file in your code repository, located at `.sleuth/rules.yml`, and include zero or more conditions, as well as one or more actions to take when those conditions are met. Rules are triggered by events such as a code deployment or a deploy being determined to be healthy.

Here's an example `.sleuth/rules.yml`:

```text
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

