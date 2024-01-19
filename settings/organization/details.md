# Details

{% hint style="warning" %}
Only **Owners** and **Administrators** have access to the _Organization Settings_ and _Invite People_ selections in the Organization dropdown. Developers and Observers must request access from an Owner or Administrator. Read [Access Control](../access-control.md) for more information about RBAC (role-based access control) in Sleuth.
{% endhint %}

The **Details** tab contains general information about the selected **organization**. The name of selected organization is displayed at the top of the sidebar. Select the dropdown to select a different organization, if you belong to more than one.

![](../../.gitbook/assets/org-details.png)



{% hint style="warning" %}
The **API Key** described below is a legacy feature. It's still supported so as not to break existing customers' API tokens that have been deployed in their integrated tools, but we recommend generating any new API tokens from the [Access Tokens](access-tokens.md) tab
{% endhint %}

* You can change the name of your organization in the **Details** tab, along with an optional **Description** for the organization.
* Enter an optional well-formed URL in the **URL** field.
* **Working Hours** allow you to specify default working hours for Change lead time calculations. The working hours specified here will be used for any users that haven't set their own working hours (including Contributor users who don't have access direct to Sleuth). For more information on working hours, refer to [Working hours and Change lead time](../../accelerate-metrics/change-lead-time.md#working-hours-and-change-lead-time).
* The **API Key** field contains an API key for external application access to your organization's data. Keep this key private, and **do not share it** with anyone or any system without knowing what you're doing! If you feel your API key has been compromised, click Regenerate Key to obtain a new one. Any external applications that access your Sleuth organization programmatically might stop working, so be sure you know what you're doing!
* Press **Save** after making any changes in the _Details_ tab.
