---
description: Organize projects and configuration states with environments.
---

# Environment Support

Sleuth's environment support lets you model your change sources, such as code deployments, feature flags, and impact, across multiple environments within a project. This exclusive Sleuth feature provides you with a clear view of how your code behaves across different environments.

![A project can contain multiple environments](.gitbook/assets/project-env_hierarchy.png)

Environments are used to test code at various stages of the feature lifecycle in non-production environments before shipping to customers, and can lead to further confidence in the software when in production. Sleuth's environment support allows you to track changes across environments within a project to understand what state each environment is in, and understand when changes are soon to ship to production.

Model your code as you choose and Sleuth adapts. For example, if you have separate _production_ and _staging_ repos, you can create multiple code deployments that map to a master branch. Or, if you choose, you can have separate master and development branches within the same repo and map those branches to their own environment within your project.

![](.gitbook/assets/branch_mapping%20%281%29.png)

You can register a deploy via the [Sleuth API](resources/api-reference.md) by specifying an environment parameter, which registers the environment you're deploying to. If you maintain separate code branches for production and staging, you can map those branches to individual environments as well.

* If you are using only one branch to deploy to multiple environments, you must provide an environment parameter when registering a deploy. Sleuth will deliver it to the correct environment. 
* If you are using different branches to deploy to different environments, Sleuth allows you to map environments to branches, along with supporting auto-deploy on commit or tag.
* For [manual deployments](resources/api-reference.md#manual-deploy-registration), you can specify the environment on the [HTTP POST](resources/api-reference.md#environment-deploy-registration) as the 'environment' field or default to the project's default environment.
* A project must always have least one default environment. 
* Environments map to a single branch by default. You can change this behavior, and map multiple environments to multiple branches. 
* If applicable to the integration, Sleuth will intelligently map environments to Sleuth environments \(i.e., LaunchDarkly staging to Sleuth staging\). 

{% hint style="success" %}
Edit your project's [environment settings](settings/project-settings/#environments) by going to **Project Settings** &gt; **Environments** in [project settings](settings/project-settings/).
{% endhint %}

