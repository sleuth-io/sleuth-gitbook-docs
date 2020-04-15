# Impact

Impact is an important part of the Sleuth experience, and is one of the main metrics Sleuth computes to provide you with the overall health status of your deploys. 

![Example of Impact on a deploy](.gitbook/assets/impact-banner.png)

Impact lives at the Organization level; it is similar to creating a GitHub or LaunchDarkly integration. A specific instance of Impact lives at the Project level and applies to all changes made via a change source within that project. This is configured similarly to a change source.

A user wants to know if a deploy has had a positive/negative/neutral impact on the project. A user wants to quickly, visually see how impact is trending in relation to the deploys that are occurring. A user wants to understand if a deploy has changed the “normal” behavior of their system so they can react appropriately.

Since we’ll be monitoring Impact we can establish a baseline of “normal” for the project. We want to be able to detect when the impact value has deviated from “normal” and call this out in Sleuth.

We can start with Standard Deviation and get more nuanced from there. A user wants to know, in [Slack](dashboard/integrations/slack.md) if a deploy has had a positive/negative/neutral impact on the project.

This information should also be used in the personalized Slack notifications we send to change authors. 

