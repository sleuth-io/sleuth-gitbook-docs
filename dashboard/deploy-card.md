# Deploy card

The deploy cards are a running list of your deploys, shown in chronological order. Direct links are provided to the corresponding repos, allowing you to quickly see what changes were made. The size of the deploy is also displayed. Collectively, the size of your deploys over the displayed time range impacts the size graph. Clicking on the commit hash displays more detailed information about all the events leading up to the deploy. [Learn more](../resources/terminology.md#deploy-cards) about deploy cards. 

By viewing a deploy card, you can: 

* see who authored the deploy and how many PRs/commits/issues/files were in the deploy; 
* instantly view the pull request in whichever repository it resides in \([GitHub](../integrations-1/change-sources/code-deployment/github.md) or [Bitbucket](../integrations-1/change-sources/code-deployment/bitbucket.md), for example\);
* know when the deploy occurred; 
* get an objective, historical assessment of your project's health __\(_Unhealthy_, _Ailing_, _Healthy_, _Improved_\); and
* know how large or small of an impact the deploy had on your project overall. 

![A Sleuth deploy card showing detailed information about a single deploy](../.gitbook/assets/deploy-tracking.png)

To get more information about a deploy, you can:

* Click on the card title to view all the PRs, commits, issues, files, impact and authors of the deploy; or
* Click on any of the PRs that comprised the deploy to view the deployed code in its corresponding repo.

### Previewing deploys

Sleuth lets you see what your next deploy is going to look like by 

It's automatic and the way it works is the following - if you have "auto deploy on each commit", you can't have it, because we simply deploy all the commits you push but if you DON'T have auto deploy enabled, you need to manually submit a deploy with us

let's say you made commits A, B, C, D and you told us you deployed A

your current version is A while B, C and D are yet undeployed

we're taking these three and giving you the "next deploy" preview

so whatever the difference is between the last commit you deployed and the last commit in your repo 

