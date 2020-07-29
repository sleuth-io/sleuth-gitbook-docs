# Environments

Organize project settings and configuration states by packaging them into **environments**. Sleuth provides support for environments in ways that are already familliar to developers. Environment modifications are made at the Sleuth [project](../../projects.md) level, and contain all the settings and configuration states for each environment, such as _staging, testing,_ and _production_. You can easily integrate with your existing DevOps tools to intelligently organize environmental attributes.

Changes made to settings and states apply only to the selected environment. Create as many environments as your project needs. You can easily switch between environments using the environment selector underneath the project title in the [Dashboard](../../dashboard/). 

Using environments means that every code deployment you create is represented in all of your environments. When you register a deploy against the [Sleuth API](../../resources/api-reference.md) you can specify an environment parameter that tells Sleuth which environment is being deployed to. If separate branches are used for your environment deploys, you can map those branches in the code deployment edit screen. \[screenshot here\]

If using [manual deployments](../../resources/api-reference.md#manual-deploy-registration), you can specify the environment on the HTTP POST as the 'environment' field or let it default to the project's default environment. Selecting a default environment ensures it’s displayed first when you visit the Dashboard. The selected default environment settings are also applied to any additional environments that are created.

#### To create a new environment: 

#### To edit environment parameters: 

