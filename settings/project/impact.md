# Impact settings

The **Impact** tab in [Project Settings](./) is where configuration changes are made to the impact  sources in your project. Impact sources track changes made by the **error** and **metric** impact integrations made in Sleuth. 

**Metrics** track the impact from service level metrics, application and infrastructure specific metrics you are collecting on your project. With each deploy, the metric is sampled and correlated to the change that may have caused it. Examples of a metric impact includes:

* The average response time of your API;
* The percentage of notifications sent within a 5 minute SLA. 

**Errors** track the impact from application errors on your project. With each deploy, the error rate is sampled and correlated to the change that may have caused it. 

* View error rates on the deployment frequency graph; 
* Generate a ChatOps notification of impacted deploys. 

![](../../.gitbook/assets/impact.png)

## Edit Error Impact Source

To edit error impact sources, click the _edit_ dropdown in the Actions column then select **Edit** to view the _Edit Error Impact_ _Source_ screen.

{% hint style="info" %}
Error Impact's only apply to the specified Environment. If you have an Error impact that applies to more than one Environment you must create a second one that maps to that Environment.
{% endhint %}

![](../../.gitbook/assets/edit-error-impact-source.png)

## Edit Metric Source

To edit metric sources, click the _edit_ dropdown in the Actions column then select **Edit** to view the _Edit Metric_ _Source_ screen.

{% hint style="info" %}
Metric Impact's only apply to the specified Environment. If you have an Metric impact that applies to more than one Environment you must create a second one that maps to that Environment.
{% endhint %}

![](../../.gitbook/assets/edit-metric-impact-source.png)

