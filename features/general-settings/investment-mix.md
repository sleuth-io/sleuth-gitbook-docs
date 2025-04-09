# Investment mix

The **Investment mix** tab allows you to define rules that "map" your Jira issues into meaningful categories for understanding where developer time and salary are being spent.

<figure><img src="../../.gitbook/assets/image (155).png" alt=""><figcaption></figcaption></figure>

These settings are required for any of the **"**&#x49;nvestment mix..." widgets included in the **Investment Mix** Review template:

<figure><img src="../../.gitbook/assets/CleanShot 2024-11-20 at 10.09.21@2x.png" alt=""><figcaption></figcaption></figure>

Sleuth lets you define category mapping rules based on common Jira fields. To add or modify a mapping rule for any Investment mix category, perform the following steps:

1.  Click **Edit** for the category you wish to define:\


    <figure><img src="../../.gitbook/assets/CleanShot 2025-02-07 at 10.05.01@2x.png" alt=""><figcaption></figcaption></figure>
2.  Specify conditions for the mapping rule using any combination of the available filters, then click **Save settings**:

    <figure><img src="../../.gitbook/assets/CleanShot 2024-11-20 at 11.27.49@2x.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
If Investment mix settings have not been specified for a Teamspace, then Reviews created in that Teamspace will default to the org-level Teamspace's Investment mix settings.
{% endhint %}

{% hint style="warning" %}
For planned vs unplanned work, both the “Planned” and “Unplanned” categories must be defined
{% endhint %}

{% hint style="warning" %}
You'll need to specify an average developer salary in order to see monetary costs reflected in Investment mix widgets.
{% endhint %}

#### Using Jira Automations for complex Investment Mix mappings

If your logic for mapping Jira issues into investment mix can't be captured using Sleuth's [Investment mix settings](broken-reference) alone, then we recommend using [Jira Automations](https://www.atlassian.com/software/jira/guides/automation/overview#what-is-automation) to pre-label your issues before they come into Sleuth.&#x20;

Jira Automations allow you define complex conditions using any combination of Jira metadata fields and even supports custom JQL expressions:&#x20;

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

By using Jira Automations to pre-label your issues, you can automate complex issue categorization logic in Jira and then simply capture the 1-to-1 mappings between your Jira labels and Sleuth's investment mix categories in Sleuth's Investment mix settings.
