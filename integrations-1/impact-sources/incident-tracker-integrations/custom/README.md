# Custom

## About the integration

Some teams track incidents using tools Sleuth doesn't have an out-of-the-box integration with yet or even outside of traditional Observability tools. Custom Incident Impact Sources allow you to submit values collected by these tools to Sleuth and get your Failure Rate and MTTR values.

## Setting up the integration

A Custom Incident Impact Source is always available within your Sleuth project(s). No additional configuration is needed. See '[Configuring the integration](../../metrics/custom.md)' below for details on how to use a Custom Incident Impact Source.

## Configuring the integration

* Navigate to the Project you want to add the Impact Source to.
* Click **Add** in the top navigation bar and select **Impact source** from the list.
* Select **Incident management (recommended)** from the `How do you track change failure` drop-down located towards the top of the page.
* Choose **Custom Incident - user provided** from the selection of tiles/providers.
* On the **Configure impact source page**, enter a name for your Impact Source (_we recommend choosing a name that's descriptive, such as "Production incidents"_), select the environment you want the collected incident data to apply for from the dropdown, and click **Save**.

![](<../../../../.gitbook/assets/Screenshot 2021-10-29 at 13.43.22.png>)

*   Once the Impact Source is created, a window will pop up, providing instructions on how to use the Impact Source to register incident events.&#x20;

    <figure><img src="../../../../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption><p><em>You can also always come back to this page by navigating to the Impact Source, clicking the <strong>gearwheel</strong> in the top right, and selecting <strong>Show register details</strong>.</em></p></figcaption></figure>

That's it! Sleuth will now start monitoring incidents from your custom source. Head over to the Dashboard to start seeing your data in action in the project and deploy health graphs.

## Using the integration

The webhook sent to Sleuth must contain the **mandatory** `type` parameter, the value can be:

* `triggered`
* `resolved`
* `reopened`

There are also several **optional** parameters, such as:

* `id`: The unique incident identifier in your system
* `date`: The ISO 8601 date the event occurred, defaults to the current time
* `title`: The human readable title of the incident
* `url`: URL to incident in your external system

{% hint style="info" %}
To access the detailed instruction on how to use the Impact Source at any time, navigate to the Impact Source, click the :gear: icon in the top-right corner, and click `Show register details`.
{% endhint %}

## Removing the integration

#### To remove the custom incident source

1. Click on your **Project Settings** --> **Impact**
2. Find the Impact Source you'd like to remove, click the **pencil i**con to display options, and then click **Delete**.
