# AWS CloudWatch

## About the integration

AWS CloudWatch is a metric monitoring service that helps DevOps teams discover, triage, and prioritize their observability data in real-time. Before you start, you should already have a AWS account and your environment setup and running. If not, head over to AWS to get things started. Once you're done, return to Sleuth so you can complete setup of the integration.

## Setting up the integration

To add the Sleuth CloudWatch integration:

* Click **Integrations** in the sidebar.
* Click the _Metric Trackers_ tab, then **enable** in the CloudWatch card.
* Enter your Secret Key, Access Key and your AWS region in the corresponding fields.
* Press **Save**.

{% hint style="info" %}
The AWS Secret and Access key can be added to an AWS user. The user only requires the permissions: CloudWatch: List, Read.

[https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_users\_create.html](https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_users\_create.html)
{% endhint %}

![](../../../.gitbook/assets/integrations-sleuth-2021-02-23-17-27-02.png)

* Once the AWS CloudWatch integration is enabled, you will see **CloudWatch enabled** displayed in the integration card (as shown below).

![](../../../.gitbook/assets/integrations-sleuth-2021-02-23-17-28-14.png)

## Configuring the integration

* Click **Add metric** and select a Sleuth project that will collect the metrics CloudWatch generates. All projects within your organization will be displayed in the dropdown.

![](../../../.gitbook/assets/integrations-sleuth-2021-02-23-17-29-35.png)

{% hint style="info" %}
Integrations are made at the Sleuth organization level, and are available for all projects within that organization. Individual settings for an integration are made at the project level.
{% endhint %}

That's it! Sleuth will now start verifying your deploys health by tracking the values from your CloudWatch metric. Head over to the Dashboard to start seeing your data in action in the project and deploy health graphs.

## Removing the integration

#### To dissolve the AWS **CloudWatch** integration for the organization:

1. Click on **Integrations** in the left sidebar, then on **Metric Trackers**.
2. In the AWS CloudWatch integration card, click **disable**.

The AWS CloudWatch integration is disconnected and no longer available to any projects within that organization. Any project-level modifications you made to the AWS CloudWatch integration will be lost.

### Adding Impact

1. Click +Add under IMPACT SOURCES in the left sidebar
2. Select CloudWatch from the dropdown and click "Enable and add"

Query defines which metric the impact will track. There are 2 ways to specify your metric query:

#### **If you are familiar with AWS**

you can write the query parameters in the prefilled format

![](../../../.gitbook/assets/screenshot-2021-08-10-at-16.51.33.png)

#### **Find query through CloudWatch UI**

1. Log in to AWS CloudWatch management console
2. Click on **Metrics** in left sidebar
3. Click through metric groups cards and select the metric you want your impact to track

![](<../../../.gitbook/assets/image (5) (1) (1).png>)

4\. Make sure **only 1 metric** is graphed, click **Source** and **copy-paste** the JSON to Sleuth

![](<../../../.gitbook/assets/image (3) (2) (1).png>)

***
