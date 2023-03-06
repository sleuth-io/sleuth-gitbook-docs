# Environment drift

**Environment drift** is the difference between two unique environments in a [project](../projects/), measured in the number of commits and deploys between them as well as the amount of time between the current date and the last commit date for the environment that's lagging.

For example, if you just deployed your staging environment to production, drift will be zero since both environments have the same code. As soon as you make a deploy to your staging environment, Sleuth detects a drift between staging and production as _1 commit and 1 deploy_. An example drift value between _Production_ and _Staging_ environments could be:_\*\* 1 commit and 3 days\*\*_.

Sleuth displays environment drift for individual code deployments within the Code Deployment dashboard, and for Projects with multiple code deployments, it also displays environment drift for each of those code deployments from within the Project Status dashboard.

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

What's more, when drift is detected, Sleuth also provides visibility into drift details, showing exactly which deploys, PRs, commits, and issues need to be resolved across the two environments.

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
