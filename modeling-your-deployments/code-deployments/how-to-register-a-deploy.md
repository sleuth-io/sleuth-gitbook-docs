# How to register a deploy

## Notifying Sleuth when you deploy

How does Sleuth know when you have deployed? There are five different ways Sleuth can be notified:

* [Precise (CI/CD) – automatically detect deploys from completed CI/CD builds](how-to-register-a-deploy.md#precise-deploy-detection-from-completed-builds)
* [Precise (webhook) – send Sleuth a webhook so we know exactly when you've deployed](how-to-register-a-deploy.md#precise-deploy-registration-via-a-webhook)
* [Approximate – automatically create deploys for every PR merged](how-to-register-a-deploy.md#approximate-automatic-tracking-for-each-pr-merged)
* [Approximate – automatically create deploys for every commit created](how-to-register-a-deploy.md#approximate-automatic-tracking-for-each-push-to-the-configured-branch)
* [Approximate – automatically create deploys for every tag created](how-to-register-a-deploy.md#approximate-automatic-tracking-for-each-tag-made-against-the-configured-branch)

{% hint style="info" %}
We highly **recommend precise deploy registration**. Knowing exactly when you've made your deploy unlocks the truly powerful features of Sleuth such as Impact tracking, notifications and more.
{% endhint %}

### Precise deploy detection from completed CI/CD builds

When this option is selected Sleuth will guide you through a CI/CD mapping step where you'll map a build / job / pipeline name to each Sleuth environment. Sleuth will then automatically register a deploy on a successfully completed build / job / pipeline that matches the mapped name.&#x20;

When using CI/CD build deploy detection there is no need to modify your build scripts or change the way you deploy, Sleuth does all the work and will track your deploys precisely and automatically.&#x20;

For example, we use CircleCI where we have many jobs, but only two are relevant for deploy registration. These are `deploy-prod` and `deploy-stage`, so our mapping between CI/CD and Sleuth environments looks like so:

![](<../../.gitbook/assets/build detection mapping.png>)

{% hint style="info" %}
Sleuth is only able to do auto deploy detection from CI/CD builds for our supported [CI/CD integrations](../../integrations-1/builds/).  If you don't see your CI/CD provider please reach out and let us know. We're always adding new Integrations and are prioritizing as demand dictates.

Keep in mind that even without a supported provider you can still achieve precise tracking using our webhook registration.
{% endhint %}

### Precise deploy registration via a webhook

Ping Sleuth with a Git commit SHA or a tag to tell Sleuth you've deployed by making a `POST` request. You'll need to provide theses values when making the call:

* `YOUR_API_KEY`
* `YOUR_SHA`
* `ORG_NAME`
* `PROJECT_NAME`

You can find your _API Key_ in **Organization Settings** > **Details** > **Api key**:

![Locating your Sleuth API key](../../.gitbook/assets/screen-shot-2020-05-06-at-9.29.52-pm.png)

You can find `YOUR_SHA` using the commands:

```http
git checkout YOUR_BRANCH
git rev-parse HEAD
```

{% hint style="info" %}
[Get more detailed information](https://help.sleuth.io/sleuth-api#deploy-registration) on precisely registering a deploy via the Sleuth API.
{% endhint %}

### Approximate – automatic tracking for each PR merged

When this option is selected Sleuth will treat every merged PR on your branch as a deploy.

{% hint style="info" %}
Sleuth allows you to specify a delay in minutes. When this is set Sleuth will only create the deploy after the delay has passed. A delay of 0 will create the deploy immediately.
{% endhint %}

### Approximate – automatic tracking for each push to the configured branch

When this option is selected Sleuth will treat every commit made to your branch as a deploy.

{% hint style="info" %}
Sleuth allows you to specify a delay in minutes. When this is set Sleuth will only create the deploy after the delay has passed. A delay of 0 will create the deploy immediately.
{% endhint %}

{% hint style="warning" %}
It's rarely the case that every commit is a deploy. Only true continuous deployment setups deploy every commit.
{% endhint %}

### Approximate – automatic tracking for each tag made against the configured branch

When this option is selected Sleuth will treat every tag made on your branch as a deploy.

{% hint style="info" %}
Sleuth allows you to specify a delay, in minutes. When this is set Sleuth will only create the deploy after the delay has elapsed. A delay of 0 will create the deploy immediately.
{% endhint %}

{% hint style="warning" %}
If you've chosen this option make sure that your CD system is tagging your code only once it's actually been deployed.
{% endhint %}
