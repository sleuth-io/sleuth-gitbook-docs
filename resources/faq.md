# FAQ

## How are environments represented in Sleuth?

Currently, the way to represent your environments in Sleuth is to model them as [projects](../projects.md). Create a new project for each environment, such as staging, production, development, etc., and then map change sources, deployments, feature flags, etc., to each environment individually. 

More information about how environments are represented in the Sleuth Information Architecture is available on the [Terminology page](terminology.md#information-architecture-ia). 

## How do I connect to my organization? 

Someone on your team might have already created a Sleuth project, and connected integrations already. Instead of creating a new account and project from scratch, you can join their organization, which can be your team or your company. If your email address domains match, you can automatically connect to their environment, which will give you access to all their projects and integrations. 

## How does Sleuth perform anomaly detection? 

Sleuth uses an open source anomaly detection tool to perform its impact source reporting. When you deploy, Sleuth immediately starts analyzing the information received from your integrated tools. Of course, the more tools you have means that Sleuth has more information to process, which will give you a much clearer picture of how healthy \(or not\) your deploys are. For example, with a [Datadog](../integrations-1/impact-sources/metrics/datadog.md) integration you can set the baseline of the reported metrics and then configure Sleuth how to process any deviations; for example, less 500 errors are better than more. 

## Can I get chat support? 

Yes! Sleuth uses Tawk.to for chat support. Look in the lower-right hand corner of your [Dashboard](../dashboard/) and click on the Tawk.to icon to get instant chat support \(available Monday thru Friday, 8 am to 5 pm PST\).   

![Tawk.to chat widget on the Dashboard](../.gitbook/assets/tawk-to-icon.png)

## How much does Sleuth cost? 

You can get detailed pricing and purchasing information here on the [Purchasing](purchasing.md) page. 



