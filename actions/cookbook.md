# Cookbook

To more easily start using Sleuth Actions, here are several recipes that you can either try today or if labeled with "\(coming soon\)", may be available in the future. To vote for these proposed use cases or suggest new ones, please [let us know](mailto:support@sleuth.io)

## Deployment promotion

### Auto-promote staging deploys to production

When code is deployed to the Staging environment and has been determined to be healthy by Sleuth, auto approve any manual approval steps in the associated build.

```text
staging-promotion:
  conditions:
    - environment='Staging'
    - health='Healthy'
    - deployed_for>='5m'
  actions:
    - auto_approve_build: 'test-and-deploy'
```

### Auto-promote quickfix staging deploys to production

When you want your code shipped quickly or know you are shipping something can't break production, add a 'quickfix' label to your pull/merge request and it'll automatically be promoted to production.

```text
quick-fixes:
  conditions:
    - environment='Staging'
    - pr_labels='quickfix'
  actions:
    - auto_approve_build: 'test-and-deploy'
```

### Slack approvals-based promotion&lt;/h3&gt;

The first rule responds to the staging deployment message in Slack to let people know how to promote. The second rule fires the number of :+1: reactions is 3 or more and there are no :-1: veto votes. If successful, the deploy is promoted to production.

```text
promote-staging-to-prod-notify:
  conditions:
    - environment='Staging'
  actions:
    - slack_deploy_message: |
        Please vote to approve +/-1 to promote this deployment {{slack_mention_authors}}
promote-staging-to-prod-on-approval:
  conditions:
    - environment='Staging'
    - health='Healthy'
    - deployed_for>='5m'
    - deploy_message_reactions_plus_1>=3
    - deploy_message_reactions_minus_1=0
  actions:
    - auto_approve_build: 'test-and-deploy'
```

### Auto-promote after soak time

When code is deployed to staging for at least 4 hours and is still healthy, then promote to production.

```text
staging-to-prod-after-soak:
  conditions:
    - environment='Staging'
    - health='Healthy'
    - deployed_for>'4h'
  actions:
    - auto_approve_build: 'test-and-deploy'
```

### Separate approval workflow for third-party PRs \(coming soon\)

Pull/merge request merges, from non-trusted developers, aren't autopromoted from staging to production, but instead send a Slack message to the `#deploy-requests` channel for someone to promote it for them.

Note that the slack message is markdown and created with the [Jinja](https://jinja.palletsprojects.com/en/2.11.x/) template language.

```text
staging-to-prod-third-party:
  conditions:
    - environment='Staging'
    - pr_authors!='teamlead1' AND pr_authors!='srdev1'
  actions:
    - auto_approve_build: 'test-and-deploy'
    - slack_channel_message:
        channel: '#deploy-requests'
        message: |
          A {{deployment_name}} is awaiting approval:
          {% for pr in prs %}
          * <{{pr.url}}|{{pr.title}}> - by {{ pr.author}}
          {% end %}
```

## Deployment notifications

### Custom message to author when deploy is unhealthy \(coming soon\)

When a deployment to production is determined by Sleuth to be unhealthy, notify any author involved in the deployment, usually commit and pull request authors. Send them a personal slack notification with a custom message containing links to key dashboards, logging systems, runbooks, and whatever other resources they need to resolve the incident.

```text
author-unhealthy:
  conditions:
    - environment='Production'
    - health='Unhealthy'
  actions:
    - notify_deploy_authors: |
        Your code was <{{deploy_url}}|deployed> and is unhealthy. Check these links:
          * &lt;https://datadog.com/dashboard/important-things|Important things graphs>
          * &lt;https://mylogs.com/dashboard/production_logs?sha={{deploy_revision}}|Prod logs for this deploy>
          * &lt;https://statuspage.com/myorg/create_incident|Update status page>
```

### Notify the project lead on certain deploys \(coming soon\)

Sleuth can tag deploys, either based on file paths matched from the contents of the deploy, or via tags passed explicitly when registering the deploy. In this rule, when production deployment is created and the deploy is tagged with `api_change` or `database_migration`, notify the team lead with a personal slack message.

```text
notify-sara:
  conditions:
    - environment='Production'
    - tags='api_change' or tags='database_migration'
  actions:
    - slack_personal_message:
        user: sara@example.com
        message: |
          An important <{{deploy_url}}|deployment> went out tagged with {{deploy_tags}}.
```

### Notify key issues on certain deploys \(coming soon\)

When a blocker issue is resolved with a deployment to production, add a comment on the issue to notify any watchers of that issue that it has been fixed.

```text
notify-important-issues:
  conditions:
    - environment='Production'
    - issue_priority='Blocker'
  actions:
    - notify_mentioned_issues
```

### Notify support team on bugs and new features that impact them \(coming soon\)

When code is deployed to production, find any issues that are either bugs or labeled with `support`, and send them to the Slack `#support` channel to notify the support team so that they can update the customer.

```text
notify-support:
  conditions:
    - environment='Production'
    - issue_labels='support' or issue_type='Bug'
  actions:
    - slack_channel_message:
        channel: '#support'
        message: |
          {{deployment_name}} was deployed with the following relevant issues
          {% for issue in issues %}
          * <{{issue.url}}|{{issue.key}} - {{issue.title}}>
          {% end %}
```

### Notify in Slack when drift is too high

When a deploy hits staging, and staging is more than 10 deploys different than production, send a Slack channel notification to `#dev` warning them that they need to promote to production soon.

```text
drift-too-high:
  conditions:
    - environment='Staging'
    - drift_to_production>10
  actions:
    - slack_channel_message:
        channel: '#dev'
        message: |
          Drift to production too high
```

## Deployment miscellaneous

### Transition issues on deploy \(coming soon\)

When code is deployed to production, find any referenced issues and transition them into the `Deployed` state.

```text
transition-issues-on-deploys:
  conditions:
    - environment='Production'
    - health='Healthy'
    - deployed_for>='5m'
  actions:
    - transition_mentioned_issues:
        state: Deployed
        comment: |
          This issue has been deployed by {{deploy_author_name}} in <{{deploy_url}}|{{deploy_name}}>
```

### Create revert PR when unhealthy \(coming soon\)

When a deployment to production is unhealthy, create a pull/merge request that reverts the deployment. Send a personal Slack message to the authors of the deployment with a link to the revert PR so that they can quickly fix the deployment.

```text
revert-pr-on-unhealthy:
  conditions:
    - environment='Production'
    - health='Unhealthy'
  actions:
    - create_revert_pr
    - notify_deploy_authors: |
        Your code was <{{deploy_url}}|deployed> and is unhealthy, and a PR was created to revert {{pr_url}}
```

### Create backport PR on deploy \(coming soon\)

When a deployment goes to production, create a pull/merge request that backports the changes to staging. Useful if hot fixes were applied directly to the production branch and need to be backported to the staging branch.

```text
backport-pr:
  conditions:
    - environment='Production'
  actions:
    - create_pr:
        target_env: Staging
        source_env: Production
        title: |
          Backport of production to staging for release {{deploy_name}}
    - notify_deployer: |
        Your code was <{{deploy_url}}|deployed> and here is the backport PR: <{{backport_pr_url}}>
```

### Slow rollout of feature flags after delivery \(coming soon\)

When code is shipped to production, and it comes from a pull/merge request that has the `auto-flag-rollout` label, and is healthy, then gradually enable related feature flags over a period of time.

```text
feature-flag-rollout:
  conditions:
    - environment='Production'
    - pr_label='auto-flag-rollout'
    - health='Healthy'
    - deployed_for>='5m'
  actions:
    - gradually_enable_feature_flag:
        increment: 10%
        interval: 20m
        on_unhealthy: revert
```

