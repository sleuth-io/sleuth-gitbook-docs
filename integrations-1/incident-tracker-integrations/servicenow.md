# ServiceNow

## About the integration

ServiceNow is a cloud-based workflow automation platform that provides a wide range of applications centered primarily around IT Service Management and IT Operations. This integration focuses on ServiceNow's [Incident Management application](https://docs.servicenow.com/bundle/sandiego-it-service-management/page/product/incident-management/concept/c\_IncidentManagement.html), allowing Sleuth to source incident data from ServiceNow and evaluate how those incidents impact the overall health of your deploys (i.e. in terms of CFR and MTTR).

Note that the ServiceNow integration currently supports only ServiceNow's _Incident_ object (an extension of ServiceNow's _General Task_ object) and supports only the [default state model](https://docs.servicenow.com/bundle/sandiego-it-service-management/page/product/incident-management/concept/c\_IncidentManagementStateModel.html) for ServiceNow's Incident object, treating all states but _Closed_ as an "open" failure with respect to CFR and MTTR.

&#x20;<img src="../../.gitbook/assets/image (21).png" alt="" data-size="original">

## Enabling the integration (Organization-level)

To set up the the ServiceNow integration, you'll first need to enable it globally (i.e. for your Sleuth Organization).&#x20;

{% hint style="info" %}
Integrations are enabled at the Sleuth Organization level and are then available for all Projects within your Organization. Project-level settings for impact integrations are configured by adding an Impact Source to one or more Sleuth Projects. Project-level configuration for ServiceNow Impact Sources is covered in the next section.
{% endhint %}

To enable the ServiceNow integration for your Organization, perform the following steps:

* Click **Integrations** in Sleuth's left-hand sidebar.
* Select **Incident** from the drop-down to filter the list of available integrations (optional).
* Locate the _ServiceNow_ card and click **Enable**
* Enter a fully qualified URL to your ServiceNow instance
* Enter the **username** and **password** for the service-level account that Sleuth will use to connect to ServiceNow. Note that the account used here must have read permissions for the following tables in ServiceNow:
  * sys\_user\_group
  * incident
  * cmdb\_ci\_service\_businessPress
* Click **Save**.

![](<../../.gitbook/assets/image (23).png>)

## Configuring the integration (Project-level)

In order to leverage the ServiceNow integration within a given Sleuth Project, you'll need to add a ServiceNow Impact Source to that Project, where you can specify the unique filter criteria that will determine which specific ServiceNow incidents Sleuth will associate with that Project.&#x20;

To add ServiceNow as an Impact Source for a specific Project, perform the following steps:

* From the left-hand-navigation panel, select the Project to which you'd like to add a new ServiceNow Impact Source
* Expand the **More** drawer, click **+ Add**, and select **Impact Source**
* In the **How do you track change failure** drop-down, leave the default selection in place:  _Incident management (recommended)_
* Under the **Choose your service** heading, select the _ServiceNow_ tile.&#x20;
* Click **Enable and continue**
* Provide a **Name** for your new Impact Source. Note that you might need to add multiple ServiceNow Impact Sources to cover all of the desired filter criteria combinations that you'd like to include the Project
* Configure the Impact Source by selecting the desired filters for the ServiceNow incident attributes that you would like to include in this Project.&#x20;
  * The **Severity** filter will include all ServiceNow Incidents with a Severity _greater than or equal to_ the selected value.
  * The **Business service** and **Assignment Group** filters are currently single-select, so if you'd like to include additional values for either attribute, you can do so by adding additional ServiceNow Impact Sources to the Project.
  * The **Custom filters** text field allows you to filter incidents using custom attributes you've defined in ServiceNow by specifying any field-value pairings (e.g. _u\_business\_service\_subcat=somevalue_). You can even add multiple custom fields by specifying each on a new line within this text field. You cannot, however, specify multiple values for this same field. Like **Business service** and **Assignment group** above, if you want to include multiple values for the same custom field, you can do so by adding additional ServiceNow Impact Sources to the Project.
* Under **Advanced Settings**, you can control historical data population. If checked, Sleuth will populate all incidents that happened in the last 30 days and recalculate the project's Failure Rate and MTTR metrics.
* Click **Test Connection** to validate that the new Impact Source is returning the expected incidents from ServiceNow.
* Click **Save**

## Viewing ServiceNow Incidents in Sleuth

Once you've configured a ServiceNow Impact Source, you should see that Impact Source and its health status listed on each new Deploy within that Project (as well as for the last 30 days of Deploys if you selected that option in the ServiceNow Impact Source):&#x20;

![](<../../.gitbook/assets/image (20).png>)

You'll also find a chart listing all ServiceNow incidents from the last 14 days (and their health status) within the Impact Source record itself:

![](<../../.gitbook/assets/image (17) (1).png>)
