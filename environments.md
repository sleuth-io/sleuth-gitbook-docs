# Environments

Sleuth's environment support lets you define change sources once per project but can then register changes to them across all environments within the project. This Sleuth exclusive feature lets you model your deploys across all of your environments, giving you visibility to how your code behaves across different environment variables.  

Environment modifications are made at the Sleuth [project](projects.md) level, and contain all the settings and configuration states for each environment, such as _staging, testing,_ and _production_. You can easily integrate with your existing DevOps tools to intelligently organize environmental attributes. 

Using environments means that every code deployment you create is represented in all of your environments. When you register a deploy against the [Sleuth API](resources/api-reference.md) you can specify an environment parameter that tells Sleuth which environment is being deployed to. If separate branches are used for your deploys, you can map those branches in the code deployment edit screen. 

![](.gitbook/assets/branch_mapping%20%281%29.png)

* If using [manual deployments](resources/api-reference.md#manual-deploy-registration), you can specify the environment on the HTTP POST as the 'environment' field or let it default to the project's default environment.
* A project always has at least one default environment. 
* Environments map to a single branch by default. You can change this behavior, and map multiple environments to multiple branches. 
* If applicable to the integration, Sleuth will try to map environments to Sleuth environments based on their names \(i.e., LaunchDarkly staging to Sleuth staging\). You can manage these mappings in Project Settings. 

