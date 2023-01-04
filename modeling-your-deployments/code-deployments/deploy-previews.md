---
description: Previewing upcoming deploys
---

# Future deploys

Sleuth automatically generates Future deploys, or previews of your upcoming deploys, in your project and environment. The information displayed in a Future deploy is similar to the information displayed in the detailed display of a Deploy.

![](<../../.gitbook/assets/6012408558f32c0030bb2e1e\_deploy-preview (1).png>)

{% hint style="info" %}
As an example, let's say you make commits, A, B, C, and D, but only manually notified Sleuth that A was deployed. In this case, your master branch's current version is A, while B, C, and D have yet to deployed. Sleuth will then preview commits B, C, and D, then notify you that a preview exists for the corresponding code deployment in your project.
{% endhint %}
