# LaunchDarkly



### About the Integration  

If you came over by clicking _Learn More_ on your LaunchDarkly dashboard, welcome! 

![](../../.gitbook/assets/sleuth-on-ld-integrations%20%281%29.png)

Feature flags have quickly become an important part of software development. Making high-impact changes with minimal risk and maximum control of your applications helps deliver quality software to your customers. The Sleuth-LaunchDarkly integration provides a powerful way to track how your feature flags affect the quality of your deploys over time. The LaunchDarkly integration enables Sleuth to track changes made via your LaunchDarkly features flags.

Before you start, you should already have a LaunchDarkly account, and your environment setup and running. If not, head over to [LaunchDarkly](https://app.launchdarkly.com/) to create an account. 

To add the LaunchDarkly integration:

* Click **Integrations** in the sidebar.
* Click **connect** in the LaunchDarkly Change Sources card.

{% hint style="info" %}
You must add Sleuth as an Authorized Application in the corresponding LaunchDarkly environment that contains the feature flags you want tracked.  
For more information, [read the LaunchDarkly documentation](https://docs.launchdarkly.com/integrations/oauth).
{% endhint %}

* The LaunchDarkly logo in the Change Source card will turn green when the integration is successful. 

{% hint style="info" %}
Click **disconnect** to dissolve the Sleuth-LaunchDarkly integration. You will need to re-authorize Sleuth again if you wish to re-establish the integration.
{% endhint %}

* That’s it—Sleuth will now track your feature flags as a source of change. Read [**Dashboard**]() for more information on how feature flag issues are communicated in your Project’s deploy cards. 

  \*\*\*\*

