# Creating a deployment

A code deployment in Sleuth is mapped to a Git code repository and a branch. The repository/branch combination represents the changes your team is deploying to your [environments](../environment-support.md).

Creating a code deployment is an easy 3 step process. Sleuth guides you through each step and it only takes about 1 - 2 minutes to configure. Creating a code deployment results in pulling in your last 30 days of deploys (DORA metrics) and leaves you fully setup to track your DORA metrics moving forward.

The 3 steps to create a code deployment are:

1. Enable Integrations
2. Add Code Deployment
3. Choose Tracking Type

### Step 1: Enabling Integrations

Sleuth supports most [code repository providers](../../integrations-1/code-deployment/). Choose, your code provider and Sleuth will walk you through connecting to your system either via App, OAuth or API key, depending on the provider.

![](<../../.gitbook/assets/Project Setup Step 1.png>)

### Step 2: Add Code Deployment

Configuring a code deployment in Sleuth is simple. You just map the repository and branch that your team deploys from and away you go.

![](<../../.gitbook/assets/Code deployment setup - Step 1 - Sleuth 2022-08-05 13-23-49.png>)

#### Mapping the branch you deploy from

Sleuth is very flexible and will support the way that your team works. For teams that deploy the same branch to all pre-production and production environments you will just choose that branch on this screen.

However, some teams maintain a branch for each environment they deploy to. If this is how your team works you will click the checkbox that says `Map separate branches to environments`

![](<../../.gitbook/assets/Map branches.png>)

This allows you to tell Sleuth which branch it should inspect for which environment.

#### Mapping a set of branches

Some teams will cut a release branch with a predictable name for each deployment they make. If your team works this way you can type in the prefix of the branch name you create and Sleuth will provide you with an option to track `branches matching prefix`.

![](<../../.gitbook/assets/Code deployment setup - Step 1 - Sleuth 2022-08-05 13-17-07.png>)

In this example Sleuth would look for changes on any branch that matches the prefix `released`.

#### Supporting Monorepo's

It's not uncommon for teams to maintain multiple deployable units of code in one large repository , this style of repository structure is called a [Monorepo](https://en.wikipedia.org/wiki/Monorepo). Sleuth supports Monorepo's for code deployments.&#x20;

The way to setup a Monorepo in Sleuth is to add one code deployment for each deployable unit of code within your Monorepo. When configuring the code deployment you will open the `Advanced` settings and use the `Source path prefix (include)` and the `Source path prefix (exclude)`fields to tell Sleuth which parts of the repository to include or exclude. Once configured Sleuth will only register deploys that had changes made within the patterns defined.

![](<../../.gitbook/assets/Code deployment setup - Step 1 - Sleuth 2022-08-05 13-24-06.png>)

### Step 3: Choosing Tracking Type

Sleuth supports a number of ways to track your code deploys. The easiest, zero conf, way to start tracking is connecting Sleuth to your CI/CD system and letting Sleuth detect when you've made a deploy.

![](<../../.gitbook/assets/Code deployment setup - Step 2 - Sleuth 2022-08-05 13-28-09.png>)

You can read more about all of the options for [how-to-register-a-deploy.md](how-to-register-a-deploy.md "mention").

#### Initializing a deployment

By default Sleuth will initialize a code deployment with the last 30 days of deploys we can detect. This will allow you to quickly get a baseline of your DORA metrics for the last 30 days. Sleuth uses past events, based on the tracking type you've chosen to seed the initial deploys.

For instance, if you have connected up CircleCI and mapped your deploy jobs to Sleuth we will find all of the successful jobs run in the last 30 days and create deploys for those. Similarly, if you have chosen to manually tell Sleuth about deploys with a webhook we will use the last 30 days worth of pull requests to initialize your deploys.

#### Manually initializing a deployment with as much past data as you want

{% hint style="warning" %}
Initializing more than 30 days worth of data is not a common thing teams require. It's a manual process and will take more effort on your part. If you do need to do so please make sure to follow the directions throughly.
{% endhint %}

For some teams 30 days of past data won't be enough to meet their needs. If you want to manually  import past data into Sleuth it is possible but you must follow these steps, in the right order:

1. Create your code deployment
2. When selecting the tracking type choose `Webhook`
3. On the `Using the webhook` confirmation screen open the `Advanced` configuration and deselect the option that says `Populate deploys from the last 4 weeks`\
   ![](<../../.gitbook/assets/Code deployment setup - Step 3 - Sleuth 2022-08-05 13-49-34.png>)
4. Once the deployment has been created you will then need to manually register the past deploy SHA's with Sleuth's [#deploy-registration](../../sleuth-api/#deploy-registration "mention") REST endpoint
   1. You **MUST** register old deploys in Sleuth from oldest to newest. If you don't Sleuth's rollback detection may get confused, skewing your Change Failure rate
   2. You will need to provide the Sleuth REST call with the git commit SHA, the Environment the deploy occurred in and the date the deploy occurred
   3. You will need to wait about 1 minute between each call to the Sleuth so Sleuth has enough time to sequentially process the new data
5. Once you're satisfied with how the older data looks inside of your code deployment you can edit the code deployment to have the Tracking type that you'd like moving forward.

{% hint style="info" %}
If you run into trouble initializing the data you can always delete the deployment, re-create it and try populating again.
{% endhint %}
