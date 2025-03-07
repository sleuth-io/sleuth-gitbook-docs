# FAQ

## How does Sleuth handle security and protect my data?

Sleuth is SOC2 Type 2 certified. You can read about how Sleuth secures and manages your data in the [Sleuth Trust Center](https://www.sleuth.io/trust).

Additionally, when you disconnect an integration, Sleuth purges all data, including any API keys/tokens, username/passwords, and any other information it needed to access your integration data.

## How can I allow Sleuth to connect to resources behind my firewall?

Sleuth connects to many different systems to provide your full deployment picture. Some of these systems such as Github Enterprise, Jira and others may live behind a corporate firewall. Sleuth maintains three (for AZ redundancy) NAT gateways which all outbound traffic will originate from. To allow Sleuth to connect to your protected resources you will want to allow these IP addresses through your firewall:

* 52.42.95.252
* 44.225.94.110
* 54.148.48.201
* 35.162.250.51
* 52.32.199.5
* 35.81.173.156

## Can I initialize a code deployment with more than 30 days worth of past deploys?

Yes, Sleuth allows you to manually import past data into a code deployment. Most teams don't need more than the 30 day baseline Sleuth provides out-of-the-box. However, if your team does you can follow these instructions for how to [include as much past data as you'd like](../modeling-your-deployments/code-deployments/creating-a-deployment.md#manually-initializing-a-deployment-with-as-much-past-data-as-you-want).

## How do I register deploys if my deployment tool like ArgoCD or Harness only deploys artifacts and not Git SHAs?

Because Sleuth tracks Git SHAs (revisions or tags) as deploys, when your deployment system of choice is deploying an artifact instead of checking out a SHA and running the deploy there, it can be hard to know what to send to Sleuth as part of the deploy registration webhook.

The first solution to try is to find a way to pass the Git SHA along through to the deployment pipeline. That could be done by embedding the SHA into the version number or tag name, or as part of the artifact metadata. Then, in your deployment pipeline, extract that SHA and report it to Sleuth. If multiple repositories are involved, embed multiple SHAs and call multiple webhooks.

If that isn't an option, you may need to settle for an approximate deploy registration method. For example, have Sleuth track when a Git tag is created and treat that as a deploy. You could also have Sleuth track pushes to a specific branch, then add a fixed delay to approximate when the deploy would have likely been completed.

## Which browsers are officially supported?

Sleuth officially supports up-to-date versions of all evergreen browsers (Chrome, Firefox, Edge and Opera). We also do our best to make sure everything works in latest Safari.

Browsers outside of the ones listed above represent less than 1% of all users and aren't officially supported. While we try to maintain a best-effort policy, we cannot guarantee everything will work.

## How are environments represented in Sleuth?

Sleuth has full-featured support for **environments**, which are are created and managed at the [project](../modeling-your-deployments/projects/) level. You can have as many environments as needed to represent your project and its development states, with _staging_, _testing_, and _production_ being common ones (you can name them anything you want).

Check out the [Sleuth Information Architecture](../modeling-your-deployments/) to visualize Sleuth organization hierarchy.

## How do I connect to my organization?

Someone on your team might have already created a Sleuth project and made some integrations. Instead of creating a new account and project from scratch, you can join their organization, which can be your team or your company.

If your email address domains match, you will automatically connect to the organization, which will give you access to all their projects and connected integrations.

## Can I get chat support?

Yes! Sleuth has chat support. Look in the lower-right hand corner of your Dashboard and click on the chat icon to get instant chat support (available Monday thru Friday, 8 am to 5 pm PST).

![Chat widget on the Dashboard](../.gitbook/assets/tawk-to-icon.png)

## How much does Sleuth cost?

Get detailed pricing and purchasing information on the [Purchasing](purchasing.md) page.

## Where can I find your Terms & Conditions?

You can find Sleuth software Terms & Conditions [here](https://www.sleuth.io/terms).

## What is your privacy policy?

Read the Sleuth Privacy Policy [here](https://www.sleuth.io/privacy).
