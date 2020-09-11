# Manual changes

Manual changes let you enter anything that you want tracked in Sleuth. Such changes are those not tracked by source code, feature flags, or another type of change that Sleuth [currently supports](about-integrations.md). They are a free-form entry that can have any name or description you'd like. 

Examples include: 

* Manual scaling event
* Restart of a service
* Increase in capacity

To add a manual change: 

1. Click **Create** then **Add Manual Change** in the sidebar. 
2. Give the manual change a **Name** and **Description**. 
3. Press **Create**. 

{% hint style="info" %}
A well-formed curl request with your project data pre-populated is displayed \(see similar image below\). You can use this curl request on CLI or by using Postman.  
{% endhint %}

{% hint style="danger" %}
**Do not share the curl link with anyone outside of your organization.** The dynamically-generated curl command contains your private Sleuth API key and other private information. 
{% endhint %}

![curl information in Add Manual Change page](../.gitbook/assets/curl_url_dialog.png)

The manual change will be visible on your [Dashboard](../dashboard/) and displayed just like any other source of change. Manual changes are not updated nor managed by Sleuth; you'll need to maintain them on your own. 

{% hint style="info" %}
Manual changes can be also be [submitted via the Sleuth API](../resources/sleuth-api.md#manual-change). 
{% endhint %}

