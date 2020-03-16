# Manual deploy notification

Ping the Sleuth API with a Git commit **sha** or **tag** to mark your deploy, like so:

```text
curl -X POST -d api_key=YOUR_API_KEY -d sha=YOUR_SHA https://sleuth.io/api/1/ORG_NAME/PROJECT_NAME/register_deploy
```

Make sure to replace `YOUR_API_KEY`, `YOUR_SHA`, `ORG_NAME` and `PROJECT_NAME` with your actual information.

{% hint style="info" %}
You can find `YOUR_SHA` with the commands:

```text
git checkout YOUR_BRANCH
git rev-parse HEAD
```
{% endhint %}



