# Environment drift

**Environment drift** is the difference between two unique environments in a [project](../projects/), measured in the number of commits and deploys between them.

For example, if you just deployed your staging environment to production, drift will be zero since both environments have the same code. As soon as you make a deploy to your staging environment, Sleuth detects a drift between staging and production as _1 commit and 1 deploy_. Sleuth will also display the amount of time between current date and the last commit date. An example drift value between _Production_ and _Staging_ environments could be:_\*\* 1 commit and 3 days\*\*_.

![](<../../.gitbook/assets/601240a2c9c85723b9640809\_environments-drift (1).png>)
