# Access Tokens

The **Access Tokens** tab allows you to create multiple org-level API tokens for external application access to Sleuth. Sleuth currently supports 2 API token types:&#x20;

* **ALL**: Grants full Administrator access to Sleuth
* **REGISTER\_DEPLOY**: Grants the limited ability to register a deploy to any code deployment in Sleuth

{% hint style="danger" %}
**Keep these API tokens private!** Do not share an API token with any person or any system that should not have the permissions granted by that token. If you suspect that an API token has been compromised, delete it from this screen and generate a new one.  Note that any external applications that were accessing your Sleuth organization using those deleted tokens will stop working.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (116).png" alt=""><figcaption></figcaption></figure>

