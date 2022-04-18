# Custom

## About the integration

Some teams track incidents outside of traditional Observability tools. Custom impact sources allow you to submit these values to Sleuth and get your Failure Rate and MTTR values.

## Setting up the integration

Custom Incident Impact is always available with your Sleuth project. No additional configuration is needed. See '[Configuring the integration](../impact-sources/metrics/custom.md)' below for how to use a Custom Incident Impact.

## Configuring the integration

* From your Project Settings --> Impact - click \*\*Add impact source \*\*and select a Sleuth project that will collect the metrics Datadog generates. All projects within your organization will be displayed in the dropdown.
* From the "Add a new impact source" screen choose - "Custom Incident - user provided"
* From the create screen, name your custom impact, choose a name that's descriptive, such as "Production incidents"

![](<../../.gitbook/assets/Screenshot 2021-10-29 at 13.43.22.png>)

* Once you've created the Impact Source you will be presented list of your impact sources. Click the actions dropdown on your created custom incident source and click "Show register details"

![](<../../.gitbook/assets/Screenshot 2021-10-29 at 13.43.50 (2).png>)

* A modal with instructions on how to report an Impact value to Sleuth will open. You will need to POST your data to a Sleuth REST endpoint that is specific to your metric. The dialog includes the exact URLs and information you will need to submit your data.

![](<../../.gitbook/assets/incident instructions.png>)

That's it! Sleuth will now start monitoring incidents from your custom source. Head over to the Dashboard to start seeing your data in action in the project and deploy health graphs.

## Removing the integration

#### To remove the custom incident source

1. Click on your **Project Settings --> Impact**
2. Choose the metric you'd like to remove and choose delete from the cog.
