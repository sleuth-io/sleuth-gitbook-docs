# Teamspaces

Reviews and Surveys are organized into **Teamspaces**.&#x20;

![](<../.gitbook/assets/CleanShot 2024-12-09 at 11.13.22@2x.png>)&#x20;

Sleuth presents Teamspaces alphabetically in the left-hand navigation pane. All Sleuth users can create Teamspaces, and all Teamspaces are accessible by all Sleuth users

### Defining Teamspaces

Users can define Teamspaces in whatever way best suits their use case. A Teamspace might represent:

* A software engineering team (developers and a Team Lead)
* A "product team" or "scrum team" (including scrum masters, design, PM, QA...)
* A team of teams ("tribes" or "guilds" )
* Supporting teams (SRE, DevEx, Technical Project Management, etc.)
* A single user's "personal" teamspace&#x20;

As these examples illustrate, a Teamspace can represent any level in your organization structure. We recommend creating a separate Teamspaces for any group of users that will be performing the same Reviews and Surveys together over time.

### Reviews and Surveys

Each Teamspace has tabs for managing the Reviews and Surveys within the Teamspace:

![](<../.gitbook/assets/CleanShot 2024-12-09 at 11.14.29@2x.png>)&#x20;

#### Reviews

Reviews are displayed as tiles that each represent a linear "chain" of Reviews created over time:

<figure><img src="../.gitbook/assets/CleanShot 2024-12-09 at 11.41.57@2x.png" alt=""><figcaption></figcaption></figure>

Review chains are sorted based on the most recent Review in the chain as follows:

* **Primary sort:** [Review state](reviews/review-workflow.md#review-states) (Draft, In Progress, Published)
* **Secondary sort:** End date (from newest to oldest)
* **Tertiary sort:** Last updated (from newest to oldest)

To add a new Review to an existing Review chain, click **Repeat** on any Review chain:![](<../.gitbook/assets/CleanShot 2024-12-09 at 11.48.20@2x.png>)

{% hint style="info" %}
The most recent Review in a chain must be Published before a new Review can be added to the chain.&#x20;
{% endhint %}

To view earlier Reviews in a Review chain, click **History:**

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

To "fork" a new Review chain from an existing Review, click **Copy review** next to any Review in the History screen. A new Review chain will be created with the same configuration as the copied Review.

To create a brand new Review chain, click **New Review** and select from the available [Review templates](reviews/review-templates.md).&#x20;

#### Surveys

The Surveys tab behaves similar to the Review tab. Surveys are displayed using similar sorting criteria, and the **Repeat**, **History**, and **Copy** actions behave as described above.&#x20;

<figure><img src="../.gitbook/assets/CleanShot 2024-12-09 at 12.03.56@2x.png" alt=""><figcaption></figcaption></figure>

## Teamspace settings

To access Teamspace settings, click the ellipsis to the right of the Teamspace name in the left-hand navigation:\
![](<../.gitbook/assets/CleanShot 2024-11-12 at 18.18.40@2x.png>)

### General settings

Change the Teamspace name in General settings.&#x20;

<figure><img src="../.gitbook/assets/CleanShot 2024-11-12 at 18.21.05@2x.png" alt=""><figcaption><p>Emojis highly recommended 😆</p></figcaption></figure>

### Teamspace members

You'll be prompted to add Teamspace members when you create a new Teamspace, and you can view and modify Teamspace members at any time by navigating to the **Members** tab in **Teamspace settings**.

<figure><img src="../.gitbook/assets/CleanShot 2024-11-12 at 18.30.47@2x.png" alt=""><figcaption></figcaption></figure>

To add Teamspace members, click **Add members**

<figure><img src="../.gitbook/assets/CleanShot 2024-11-12 at 18.37.19@2x.png" alt=""><figcaption></figcaption></figure>

Sleuth presents all of contributing user and teams that it detects in your integrated tools (PR authors and reviews from GitHub, issue assignees from Jira, etc.). Members that you select here are used to _filter_ Review data, not to determine which Sleuth users have _access_ to the Teamspace (all Sleuth users have access to all Teamspaces). &#x20;

{% hint style="danger" %}
The people and teams you add as Teamspace members will act as **default filters** for all Reviews created in the Teamspace. You can [override this filter for any Widget](broken-reference) within a Review, but Teamspace members are a common reason for not seeing the data you might expect in a Review.
{% endhint %}

### Integration scoping rules

Integration rules allow you to limit which Jira projects that are considered "in scope" for the Reviews in a Teamspace.

Setting integration rules improves user experience by automatically filtering out irrelevant issue data and also reduces the loading time for Review data.

To set integration rules, navigate to the **Integrations** tab in Teamspace settings and click **Set rules**.

<figure><img src="../.gitbook/assets/CleanShot 2024-11-20 at 09.48.13@2x.png" alt=""><figcaption></figcaption></figure>

Use the **Projects** drop-down to select which Jira projects to include in the Teamspace, then click **Save rules**.

<figure><img src="../.gitbook/assets/CleanShot 2024-11-20 at 09.53.39@2x.png" alt=""><figcaption></figcaption></figure>

### Investment mix

**Investment mix** settings allow you to define rules that "map" your Jira issues into meaningful categories for understanding where developer time and salary are being spent.&#x20;

These settings are required for any of the **"**&#x49;nvestment mix..." widgets included in the **Investment Mix** Review template:

<figure><img src="../.gitbook/assets/CleanShot 2024-11-20 at 10.09.21@2x.png" alt=""><figcaption></figcaption></figure>

Sleuth lets you define category mapping rules based on common Jira fields. To add or modify a mapping rule for any Investment mix category, perform the following steps:

1.  Click **Edit** for the category you wish to define:

    <figure><img src="../.gitbook/assets/CleanShot 2024-11-20 at 11.26.01@2x.png" alt=""><figcaption></figcaption></figure>
2.  Specify conditions for the mapping rule using any combination of the available filters, then click **Save settings**:

    <figure><img src="../.gitbook/assets/CleanShot 2024-11-20 at 11.27.49@2x.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
If Investment mix settings have not been specified for a Teamspace, then Reviews created in that Teamspace will default to the org-level Teamspace's Investment mix settings.
{% endhint %}

{% hint style="warning" %}
For planned vs unplanned work, both the “Planned” and “Unplanned” categories must be defined
{% endhint %}

{% hint style="warning" %}
You'll need to specify an average developer salary in [Organization Settings](broken-reference) in order to see monetary costs reflected in Investment mix widgets.
{% endhint %}

#### Using Jira Automations for complex Investment Mix mappings

If your logic for mapping Jira issues into investment mix can't be captured using Sleuth's [Investment mix settings](general-settings/investment-mix.md) alone, then we recommend using [Jira Automations](https://www.atlassian.com/software/jira/guides/automation/overview#what-is-automation) to pre-label your issues before they come into Sleuth.&#x20;

Jira Automations allow you define complex conditions using any combination of Jira metadata fields and even supports custom JQL expressions:&#x20;

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

By using Jira Automations to pre-label your issues, you can automate complex issue categorization logic in Jira and then simply capture the 1-to-1 mappings between your Jira labels and Sleuth's investment mix categories in Sleuth's [Investment mix settings](general-settings/investment-mix.md).
