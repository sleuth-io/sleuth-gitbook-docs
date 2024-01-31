# Details

{% hint style="warning" %}
Only **Owners** and **Administrators** have access to the _Organization Settings_ and _Invite People_ selections in the Organization dropdown. Developers and Observers must request access from an Owner or Administrator. Read [Access Control](../access-control.md) for more information about RBAC (role-based access control) in Sleuth.
{% endhint %}

The top section of the **Details** tab contains general information about the organization. This is where you can manage the name and other basic information about your organization.



<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

### Default user role

The **Default user role** determines the role that will be granted to users who access Sleuth for the first time via SSO.

<figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

### Working hours (org-level default)

This section allows you to specify default working hours to be used in [Change lead time](../../accelerate-metrics/change-lead-time.md) calculations.&#x20;

The working hours specified here will be used for any members that haven't set their own working hours (including Contributor users who don't have access direct to Sleuth). For more information on working hours, refer to [Working hours and Change lead time](../../accelerate-metrics/change-lead-time.md#working-hours-and-change-lead-time).

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

### API Key

{% hint style="warning" %}
The **API Key** described below is a legacy feature. It's still supported so as not to break existing customers' API tokens that have been deployed in their integrated tools, but we recommend generating any new API tokens from the [Access Tokens](access-tokens.md) tab
{% endhint %}

The **API Key** field contains an API key for external application access to your organization's data. Keep this key private, and **do not share it** with anyone or any system without knowing what you're doing! If you feel your API key has been compromised, click Regenerate Key to obtain a new one. Any external applications that access your Sleuth organization programmatically might stop working, so be sure you know what you're doing!
