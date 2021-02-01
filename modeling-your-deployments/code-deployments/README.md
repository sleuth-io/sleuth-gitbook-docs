# Code deployments

Sleuth uses your code repositories as its main sources of change. Setting up a code deployment in Sleuth allows us to track and alert on what goes into every code deploy. A code deploy surfaces all the **pull requests, linked issues, commits and authors** included in every deploy. This information allows Sleuth to:

* Track your deployment's Accelerate DevOps metrics
  * Deploy frequency, change lead time, change failure rate, MTTR and deploy size
* [Lock deployments](deployment-locking.md) so you can pump the brakes on deploying when needed
* Slice and dice past deploys with [powerful search](search.md)
* Highlight [drift between your different deployment environments](environment-drift.md)
* Sleuth [automatically tag deploys](tags.md) based on the code that's changed
* and much more...

![](../../.gitbook/assets/601240d8b9789fe380455e94_code-deployment-view.png)

{% page-ref page="how-to-register-a-deploy.md" %}

{% page-ref page="../../integrations-1/code-deployment/" %}

{% page-ref page="../../settings/project/code-deployments.md" %}

