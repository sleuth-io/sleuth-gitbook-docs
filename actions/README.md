---
description: How to use automate deployment with Sleuth Actions
---

# Overview

Sleuth Actions is an automation engine to help you streamline tasks you do manually around
deployments today. Execute actions by defining a set of rules for your repository, containing
conditions and actions to take when those conditions are met.

Rules are defined by a YAML file in your code repository, located at `.sleuth/rules.yml`, and include zero or more conditions, as well as one or more actions
to take when those conditions are met. Rules are triggered by events such as a code deployment or a deploy being determined
to be healthy.

Here's an example `.sleuth/rules.yml`:

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


A rule can be named whatever you want, `stage-to-prod` in this example, and can
have a description to display in the Sleuth interface.

For more information, including what condition variables and actions are available, within Sleuth, click on "Help" 
and then "Actions".

### Cookbook

For more ideas on what tasks can be automated, see [our cookbook](cookbook.md)

