# Move code deployments

We get it, things change. Sometimes it's a change to your development process or your product architecture, or sometimes you just realize after configuring your initial hierarchy of Projects, Environments, and Code Deployments in Sleuth that there was a better way you could have done things.

Fortunately, Sleuth provides the ability to easily move existing Code Deployments from one Project to another while maintaining each Deployments's full history of deploys, health impacts, etc.   &#x20;

To move a Code Deployment (and all of its Deploys) from one Project to another, perform these steps:

*   Open the "source" Project, navigate to the Code Deployment you'd like to move, expand the cog, and select **Move code deployment**.&#x20;

    <figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
*   In the next screen, select the "target" Project (i.e. the Project you'd like to move this Deployment to), and specify Environment mappings between the two Projects:

    <figure><img src="../../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>
*   For any of source environments that do not have a corresponding environment in the target Project, select "Do not map." Note, however, that _**this action will irrevocably delete all historical deploy data**_ for that source environment_**.**_ Sleuth will ask you to confirm:

    <figure><img src="../../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>
* It is not currently possible to map a single source environment to multiple target environments
* Click **Save** to initiate the move. Note that a code deployment might be in motion for as long as 30 minutes. You can freely move additional code deployments during this time, but it is recommended that you wait until all code deployments have finished moving before evaluating metrics data for any source or target projects.

