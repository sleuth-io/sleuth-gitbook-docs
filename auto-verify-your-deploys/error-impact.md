# Error impact

Error monitoring services help DevOps teams discover, triage, and prioritize the errors their applications produce in real-time. Error impacts are specific to a Sleuth [project](../modeling-your-deployments/projects/) and [environment](../modeling-your-deployments/environment-support.md) and will be used to determine the health of that project/environment combination.

Sleuth uses anomaly detection to determine your teams healthy range for the number of errors your application generates and will alert you and mark deploys as unhealthy when they are outside of your normal range. With each deploy, the error rate is sampled and correlated to the change that may have caused it. 

Sleuth supports the existing tools you already use such as [Sentry](../integrations-1/impact-sources/errors/sentry.md), [Rollbar](../integrations-1/impact-sources/errors/rollbar.md), [Bugsnag](../integrations-1/impact-sources/errors/bugsnag.md) and [Honeybadger](../integrations-1/impact-sources/errors/honeybadger.md).

Error rates are displayed on the health graphs throughout the application. 



