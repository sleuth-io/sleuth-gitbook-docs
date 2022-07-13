# How Sleuth Calculates Team-level Metrics

Sleuth does not require users to explicitly associate Teams with Projects. Rather, when calculating Team-level metrics, Sleuth automatically infers which Teams are contributing to which Projects by searching for Team Members within Deploys (and in the case of Code Change Deploys, by searching within the underlying PRs, Branches, Builds, and Issues included in those Deploys). If any Team Member is included as an author on a PR, Branch, or Build within a Deploy, as an owner of an linked Issues listed in the Deploy, or as the initiator of the Deploy itself, then Sleuth will include the entirety of that Deploy in its calculation of Team level-metrics for all Teams to which that Team Member belongs.

![](<../../.gitbook/assets/Sleuth Data Model for Teams (1).jpg>)

As such, Sleuth can present powerful DORA metric "intersections" that show each Team's relative contribution to the DORA metrics for the Projects they're working on. This is evident in views such as the **Projects contributed to** panel below, which shows the DORA metrics at the specific intersection of this Team and those Projects.   &#x20;

![](<../../.gitbook/assets/image (12).png>)

Similarly, from within the Project-level Metrics dashboard, Sleuth presents a view into **Contributing teams** and their relative impacts on that Project's metrics.&#x20;

![](<../../.gitbook/assets/image (21).png>)
