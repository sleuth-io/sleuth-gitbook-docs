---
description: >-
  Sleuth uses terms that you are probably already familiar with as a developer.
  Just to be sure we're all on the same page, we've compiled a list of some
  common terms here.
---

# Terminology

## Information Architecture \(IA\)

Sleuth can help you track the health and status of your deploys by providing a single of pane of glass through which you can view all of your change and impact sources. The Sleuth information architecture terms should already be familiar to you, since we use industry-standard CI/CD nomenclature. 



![The Sleuth Information Architecture](../.gitbook/assets/sleuth_ia_graphic.png)

In Sleuth you create a **Project** container, which houses all the necessary **Environments** your team might need to create, develop and test your applications. These Enviroments might include production, staging, development, and could even account for different deployment strategies such as canary, blue/green, etc. 

Once you've created and configured the various Environments within your Project, you can start adding connections to your **Change Sources** and **Impact Sources** \(see [Integrations](about-integrations.md) for more information on connecting Change Sources and Impact Sources\). 

Sleuth tracks Change Sources, such as **Code Deployments**, **Feature Flags**, and **Infrastructure**, and constantly analyzes the information they contain to capture the state of your code before, during, and after deploys. Additionally, Sleuth intakes information provided by various Impact Sources, such as **Error Rates**, **Uptime**, and **Other SLIs**. 

## Dashboard

Combining Impact Source information with Change Source data is what drives the information you see on the Sleuth Dashboard. 

You can instantly see the impact of your deploys on your entire project environment over a period of time by viewing the Trend Graph; for detailed information on individual deploys you can view a deploy card \(see below\). 

{% hint style="info" %}
You can view a live version of the Sleuth Dashboard at [https://app.sleuth.io/sleuth/sleuth](https://app.sleuth.io/sleuth/sleuth).   
It's what the Sleuth team uses everyday to make **awesome**! ✨ 
{% endhint %}

## Deploy cards

By viewing a deploy card, you can: 

* see who authored the deploy and how many PRs/commits/issues/files were in the deploy; 
* instantly view the pull request in whichever repository it resides in \([GitHub](change-sources/code-deployment/github.md) or [Bitbucket](change-sources/code-deployment/bitbucket.md), for example\);
* know when the deploy occurred; 
* get an objective, historical assessment of your project's health __\(_Unhealthy_, _Ailing_, _Healthy_, _Improved_\); and
* know how large or small of an impact the deploy had on your project overall. 

![A Sleuth deploy card showing detailed information about a single deploy](../.gitbook/assets/deploy-tracking.png)

To get more information about a deploy, you can:

* Click on the card title to view all the PRs, commits, issues, files, impact and authors of the deploy; or
* Click on any of the PRs that comprised the deploy to view the deployed code in its corresponding repo.

## Size

Another significant metric assessment Sleuth provides is **Size**. The Size chart shows you how many large versus small deploys you have committed to your repos \(changes can be _Small_, _Medium_, _Large_, or _Gigantic_\). Since the overall goal of solid CI/CD practice is to deploy small and deploy often, the Size chart gives you instant insight into whether you're _continuously deploying_ small, effective changes to your repositories instead of occasional _gigantic_, unstable changes, which could prove problematic if a rollback is necessary when a change proves fatal to your application. 

![](../.gitbook/assets/screen-shot-2020-04-29-at-2.19.19-pm.png)

**Projects** are the main entities in Sleuth. They house your code deployments, feature flags, impact sources, and any manual changes you configure. Think of them as the application you're deploying.  

## Code deployment

**Code deployments** track changes made via source code and the software development surrounding the change. Each deploy collects the **code reviews, issues, code changes and authors** of the change being deployed to your systems. Code can live on either [GitHub](change-sources/code-deployment/github.md) or [Bitbucket](change-sources/code-deployment/bitbucket.md) repos. 

## Feature flags

Sleuth tracks **feature flags** changes in [LaunchDarkly](change-sources/feature-flags/launchdarkly.md) by changing the values of feature flags. Each flag change collects the changes made, who made them, and the state of your other flags and the linked code version deployed at the time of the change. Feature flags are an integral part of software development, and Sleuth tracks them along with other metrics to provide you with a snapshot of your deployments' health. 

## Impact

The effect of your deploys over a predetermined period of time. As you perform your commits and PRs to your code repos, Sleuth is constantly ingesting the information generated by your change sources and impact sources. The collective effect of the errors generated by all of your change sources and impact sources is what defines the **impac** \([observability](https://en.wikipedia.org/wiki/Observability) and [SLI](https://en.wikipedia.org/wiki/Service_level_indicator) are similar terms used in software development\). Sleuth detects when the impact value has deviated from “normal” and keeps you posted on this deviation by constantly generating an impact metric. 

![](../.gitbook/assets/impact-banner.png)

A user might want to know if a deploy has had a positive/negative/neutral impact on their project, or wants to know how impact is trending in relation to the deploys that are occurring. They want to understand if a deploy has changed the “normal” behavior of their system so they can react appropriately.

Once a commit is performed, Sleuth samples the commit at the moment of deploy, started by defining a standard deviation, and then afterwards for up to 60 minutes. The average of the errors in that time period is used to compute the impact, which is visible on the deploy card for every commit. This feature is exclusive to Sleuth, and provides you with higher-resolution feedback other than a simple👍or 👎. 

Impact is integral to the Sleuth experience, and is one of the main metrics Sleuth computes to provide you with the overall health status of your deploys. 

## Locking

 The Lock feature in Sleuth prevents pull requests from merging into main branches, and generates automatic notifications via your Chat Ops [integrations]() \(e.g., [Slack](chat-ops/slack.md)\). 

![Locking a project/deployment is as easy as pressing one button](../.gitbook/assets/sleuth-lock-blog-button.png)

Read team member Don Brown's blog post on how Sleuth's locking feature can make your DevOps life happier! 

## Leaderboard

The Leaderboard provides a social component to Sleuth by endeavoring developers to deploy faster and smaller. 

**Scoring**

The score of an author is the simple sum of several metrics:

* **Deploy** - 5 points for each deploy;
* **Author** - 3 points for each deploy in which the author was involved but didn't perform the deploy;
* **Impact** - 2 points for each deploy rated 'Healthy', and 10 for each deploy rated 'Improved'.

## Size

The Size graph displays the overall size of the deploys being committed to the repo in your project. This is a quantitative way to gauge how your team is performing. Although size on its own is not a pure indication of the quality of the code your team is committing, it can help you and your team realize the goal of deploying smaller and faster. Quality still matters, of course, but maintaining smaller pieces of code and deploying more often makes it easier to scale things back if your application crashes. 

![Size graph on the Dashboard](../.gitbook/assets/screen-shot-2020-04-29-at-2.19.19-pm.png)

## View Compare

The View Compare function provides a link to the right of the commit hash that opens up the corresponding code repo in Bitbucker, GitHub or GitLab where you can view the changes between differente branches. 

Since the interfaces vary on the various code repository services, consult the documentation for the corresponding service for help on using the compare function. 

![](../.gitbook/assets/view-compare-arrow.png)

