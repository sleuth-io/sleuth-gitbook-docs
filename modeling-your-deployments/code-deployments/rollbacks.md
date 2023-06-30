# Rollbacks

Sleuth supports the deployment of a previously deployed code revision, otherwise know as a rollback.

![](../../.gitbook/assets/sleuth-sleuth-973f846-2021-06-24-15-03-47.png)

It's not too uncommon for a team to deploy a code change and then realize, after some time, that the change isn't behaving how they intended. The most common strategy to deal with this is to roll-forward, making a quick fix for the new error. However, sometimes it's too difficult to make a quick fix and you decide to revert to the last known good code revision.

Sleuth automatically detects rollbacks by checking the SHA of the deploy currently being deployed against the SHAs of all existing deploys in the target environment. If a matching SHA is found on an existing deploy, Sleuth will do the following:

* Register the new deploy as a rollback and tag it with the tag <mark style="color:red;">`rollback`</mark>
* Identify all deploys registered between the rollback deploy and the initial deploy with the same SHA, and mark them as rolled back, changing their health to `Rolled back` and adding the tag <mark style="color:red;">`rolled_back`</mark>

![](../../.gitbook/assets/sleuth-sleuth-f976d31-2021-06-24-15-13-10.png)

Rollbacks, by default, are counted as a failure when determining your [Change failure rate](../../accelerate-metrics/change-failure-rate.md).
