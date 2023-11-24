# Installing Automations

We've made it incredibly easy to install automations from right from the Marketplace.&#x20;

We see Sleuth Automations as part of continuous improvement _experimentation platform_, so we understand how important is to enable teams to quickly try out an automation, see if it's working for them, and then quickly move on to trying out additional automations.

The install process varies slightly depending on the [automation type](./#automation-types), but all automations share the the following easy-install features:

* All automations can be installed (and also [edited or uninstall](editing-and-uninstalling-automations.md)ed) from completely from within Sleuth's UI.
* The install process will never require issuing a PR or otherwise modifying your code repositories
* The install process allows you determine a specific Team or Project to which an automation will apply

{% hint style="info" %}
Most automations can be applied to either a Project or a Team, but some are limited to one or the other.&#x20;

When installing an automation to a Project, the automation will apply by default to all Code Deployments within that Project, but some automations provide a configuration option for limiting their scope to specific Code Deployments within the selected Project&#x20;
{% endhint %}

{% hint style="warning" %}
In order to use automations that update PRs in your Git provider, you'll need to make sure you've enabled "write" permissions for that Git provider within Sleuth.&#x20;
{% endhint %}

To install an automation in your sleuth environment, follow these steps:

* [Browse the Marketplace](./) to find an automation you'd like to install
* Click on the automation card to view additional details about the automation
*   Click **Install in Sleuth** \


    <figure><img src="../../.gitbook/assets/image (106).png" alt=""><figcaption></figcaption></figure>
*   The next page allows you pick a Project or Team for the automation and might prompt for further configuration parameters depending on the specific automation.  In this PR check example, Sleuth is asking for the maximum number of files allowed on a single PR. Other common parameters might include a Slack channel for sending notifications, an Environment selector for determining which environments an automation applies to, etc. \


    <figure><img src="../../.gitbook/assets/image (108).png" alt=""><figcaption><p>Installing and configuring a PR check automation</p></figcaption></figure>
* Once all required fields have been specified, click **Install and continue**
*   Sleuth will display a toast indicating that the installation was successful, and the installed automation now appears under the **Automations** item in the left-hand-navigation pane for the selected Project/Team.\


    <figure><img src="../../.gitbook/assets/image (109).png" alt=""><figcaption><p>Viewing installed automations for a specific Project</p></figcaption></figure>
