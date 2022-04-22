---
description: How to represent your existing deployments in Sleuth
---

# Deployment tracking

Sleuth is designed to allow you to get up and running quickly with all of your existing dev, observability and CI/CD tools. Our light-weight [integrations](../integrations-1/about-integrations.md) allow you to model your existing deployments in Sleuth without having to change your flow or install any invasive libraries.

## How Sleuth models your deployments

![](<../.gitbook/assets/sleuth\_ia\_graphic (1) (1).png>)

### Projects

Within your Sleuth [Organization](../settings/organization/) you can create any number of [Projects](projects/). Examples of how you might use projects are:

* To represent a product line your organization offers
* To represent a collection of services that many of your products rely on
* To represent a collection of micro-services that, together, offer a specific set of functionality
* To represent business units of your organization

{% hint style="info" %}
Sleuth creates a project for you out-of-the-box. Just name your project in the setup wizard and you're on your way.
{% endhint %}

### Environments

Sleuth allows you to model your existing deployment Environments. Environments are defined and shared under a Project. Examples of how you might use an Environment are:

* To represent your staging and production deploys
* To represent each percentage of a Canary rollout (10%, 25%, etc)
* To represent QA deployments or production deployments across different regions

{% hint style="info" %}
Sleuth creates a Staging and Production environment for every Project by default. You may delete these if they don't correctly represent your deployments.
{% endhint %}

### Code deployments

The heart of most software change in an organization is driven via code. A Code deployment in Sleuth directly maps to a Git repository in your source control system (e.g. GitHub, Bitbucket, GitLab). You may define any number of Code deployments under a Project so Sleuth can track your code deploys. Examples of code deployments include:

* The code used to deploy your main monolith application
* The code used to store and deploy your Terraform infrastructure
* The mono-repo code used to deploy many micro-services (you can create a deployment per service in your mono-repo)

### Feature flags

Many teams use Feature flags to activate new code paths or features for their customers. This is just another source of change and Sleuth will treat them as such. You can connect your LaunchDarkly feature flags to a project.

### Manual changes

Manual changes let you enter anything that you want tracked in Sleuth that isn't covered by code, feature flags, or another type of change that Sleuth [currently supports](../integrations-1/about-integrations.md). They are a free-form entry that can have any name or description you'd like. Examples include:

* A manual resource scaling event
* The restart of a service
* An increase in your infrastructure capacity

### Deploys

Deploys are how Sleuth represents the changes that are made from your code deployments, feature flag and manual changes. Deploys are specific to a project, environment and deployment but are visible and searchable at the project level. Deploys can progress through your different environments and Sleuth will show you which a deploy has passed through. Deploys collect all the relevant data that went into making your change and, when deploy verification is enabled via Impact tracking, shows the impact your change has made on the health of your service.
