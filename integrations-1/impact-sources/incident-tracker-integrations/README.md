# Incident tracker integrations

**Incident trackers** are used by Sleuth to automatically track change failure and its associated MTTR when your systems are having an incident.

| Integration                                          |
| ---------------------------------------------------- |
| [Blameless](blameless.md)                            |
| [PagerDuty](pagerduty.md)                            |
| [Datadog Monitors](datadog.md)                       |
| [Statuspage](statuspage.md)                          |
| [Opsgenie](opsgenie.md)                              |
| [Jira (Coud/Data Center)](jira-cloud-data-center.md) |
| [FireHydrant](firehydrant.md)                        |
| [Rootly](rootly.md)                                  |
| [ServiceNow](servicenow.md)                          |
| [Custom](custom/)                                    |

### Updating incidents over time

Sleuth will pick up on changes you make to incidents after they've come into Sleuth. Each day, Sleuth will re-evaluate 30 days of incident history looking for incident deletion, the merging of 2 incidents into 1, or updates to incident metadata (start/end dates, severity, incident types, etc.) and will recalculate Failure and MTTR metrics accordingly.&#x20;
