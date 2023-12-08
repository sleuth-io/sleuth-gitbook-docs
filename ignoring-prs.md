# Ignoring PRs

Whether it's because of Dependabot PRs or those one-off, unusually long deploy times, rest assured you can always ignore specific PRs from Sleuth's DORA metrics, Work in Progress, Goals, and notifications.&#x20;

You can ignore one-off PRs from within Sleuth, and you can also use [Sleuth Automations](https://marketplace.sleuth.io/?filter=action\&search=ignore) to quickly set up rules that will automatically ignore PRs that meet certain conditions (e.g. those pesky Dependabot PRs).



### Automatically ignoring PRs

Check out the canned ignore rules available in Sleuth's [Automations Marketplace](https://marketplace.sleuth.io/?filter=action\&search=ignore) for ignoring PRs based on PR author, label, title, description, and more, or create your own ignore rules using Sleuth's [Custom Automations framework.](sleuth-automations/actions/)&#x20;

### Manually ignoring PRs in Sleuth

#### Igoring PRs from the Work in Progress dashboard

To manually ignore a PR from Sleuth's [Work in Progress](work-in-progress.md) dashboard, click **Ignore** from the actions ellipsis menu on any pull request. Click **Unignore** to re-include the PR in your work in progress metrics. Note that any PRs ignored from Work in Progress dashboard will continue to be ignored from the DORA Metrics dashboard once those PRs ship. They will also be excluded from any [Goals charts](goals.md) or ["nudge" notifications](goals.md#setting-up-nudge-notifications-for-goals).

<figure><img src=".gitbook/assets/image (123).png" alt=""><figcaption></figcaption></figure>

#### Ignoring PRs from the DORA Metrics dashboard

To manually ignore a PR that has already deployed, open the deploy's details page from the Metrics dashboard, and click the **Ignore** icon for any PRs within the deploy that you want ignore from your DORA metrics. Click the icon again to re-include the PR in those metrics. Lead time metrics are recalculated on-the-fly as you ignore/unignore PRs.

<figure><img src=".gitbook/assets/image (124).png" alt=""><figcaption></figcaption></figure>



