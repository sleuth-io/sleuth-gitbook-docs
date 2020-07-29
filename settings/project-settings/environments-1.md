# Environments

Organize project settings and configuration states by packaging them into **Environments**. Sleuth provides support for environments in ways that are already familliar to developers. Environment modifications are made at the Sleuth [project](../../projects.md) level, and contain all the settings and configuration states for each environment, such as _staging, testing,_ and _production_. 

 Changes made to settings and states apply only to the selected environment. Create as many environments as your project needs. You can easily switch between environments using the environment selector underneath the project title in the [Dashboard](../../dashboard/).

If using [manual deployments](../../resources/api-reference.md#manual-deploy-registration), you can specify the environment on the HTTP POST as the 'environment' field or let it default to the project's default environment. Selecting a default environment ensures it’s displayed first when you visit the Dashboard. Default environment settings are also applied to any additional environments that are created.

