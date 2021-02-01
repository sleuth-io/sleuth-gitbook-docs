# Error trackers

**Errors** trackers measure the errors your application produces. Connect your error tracker to Sleuth so Sleuth can automatically verify the health of your deploys. 

Sleuth uses anomaly detection to determine your teams healthy range for the number of errors your application generates and will alert you and mark deploys as unhealthy when they are outside of your normal range. With each deploy, the error rate is sampled and correlated to the change that may have caused it. Error rates are displayed on the health graphs throughout the application. 

* [Bugsnag](bugsnag.md)
* [Honeybadger](honeybadger.md)
* [Rollbar](rollbar.md)
* [Sentry](sentry.md)

