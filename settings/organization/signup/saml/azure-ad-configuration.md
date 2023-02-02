# Azure AD Configuration

## Steps to follow

* [Create a new Enterprise Application](azure-ad-configuration.md#create-a-new-enterprise-application)
* [Set up Single Sign-On](azure-ad-configuration.md#set-up-single-sign-on)
  * Option 1: Upload metadata XML file
  * Option 2: Enter metadata manually
  * [Configure Attributes & Claims](azure-ad-configuration.md#configure-attributes-and-claims)
* [Enter Azure's metadata into Sleuth](azure-ad-configuration.md#enter-azures-metadata-into-sleuth)
  * Option 1: Link to metadata file
  * Option 2: Input metadata manually
* [Assign Users/Groups to the Enterprise Application](azure-ad-configuration.md#assign-users-groups-to-the-enterprise-application)

## Create a new Enterprise Application

Sign into Azure as an administrator and click on the "**Azure Active Directory**" tile.

![](<../../../../.gitbook/assets/image (37).png>)

In the left-hand menu click on "**Enterprise Applications**" and then click "**New application**". On the next page click "**Create your own application**". Name your application (_e.g., Sleuth_), select the "**Integrate any other application you don't find in the gallery (Non-gallery)**" option, and click "**Create**":

<figure><img src="../../../../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>

## Set up Single Sign-On

Once the application is created, you'll be taken to its homepage. Click the "**2. Set up single sign on**" tile (_alternatively, you can click the "**Single sign-on**" link in the left-hand navigation_):

<figure><img src="../../../../.gitbook/assets/image (27) (1).png" alt=""><figcaption></figcaption></figure>

When prompted, select "**SAML**" as the **single sign-on method**, then proceed with one of the 2 options explained below:

{% tabs %}
{% tab title="Option 1: Upload metadata XML file" %}
Click the "**Upload metadata file**" button to trigger the file import modal, **select the file** to upload, and click "**Add**":

<figure><img src="../../../../.gitbook/assets/image (50) (1).png" alt=""><figcaption></figcaption></figure>

Once the file is uploaded, you'll see a preview of the imported metadata. If needed/desired, you can still make changes, although it generally shouldn't be necessary.

One **optional field** that doesn't get populated automatically is "**Relay State**"; you can specify it manually by inputting your **Sleuth org slug** (_find it in your URL -> `https://app.sleuth.io/`**`<org-slug>`**_) and clicking "**Save**" at the top:

<figure><img src="../../../../.gitbook/assets/image (51) (1).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Option 2: Enter metadata manually" %}
On the "**Basic SAML Configuration**" tile click "**Edit**":

<figure><img src="../../../../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>

**Fill in the necessary metadata** (_found in Sleuth_), using the following reference, and click "**Save**":

<table><thead><tr><th>AZURE AD</th><th>SLEUTH</th><th>EXAMPLE</th><th data-hidden></th></tr></thead><tbody><tr><td><strong>Identifier (Entity ID)</strong></td><td>SAML Entity ID</td><td><code>https://app.sleuth.io/saml/metadata/</code></td><td></td></tr><tr><td><strong>Reply URL (Assertion Consumer Service URL)</strong></td><td>Assertion Consumer Service</td><td><code>https://app.sleuth.io/complete/saml/</code></td><td></td></tr><tr><td><strong>Relay State (Optional)</strong></td><td>Default Relay State</td><td><code>sleuth</code><br><code></code><em>(should be your <strong>org slug</strong>)</em></td><td></td></tr><tr><td><strong>Logout Url (Optional)</strong></td><td>Single Logout Service</td><td><code>https://app.sleuth.io/saml/sls/</code></td><td></td></tr></tbody></table>

<figure><img src="../../../../.gitbook/assets/image (43) (1).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

### Configure Attributes & Claims

On the "**Attributes & Claims**" tile click "**Edit**".

Under "**Required claim**" click on the "**Unique User Identifier (Name ID)**" claim and change the "**Source attribute**" from `user.userprincipalname` to `user.mail` and click "**Save**".

<figure><img src="../../../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

Leave the "**Additional claims**" as they are.

## Enter Azure's metadata into Sleuth

Similarly as before, you can again choose between **pointing Sleuth to a URL** where the IdP's metadata is now available, or **entering the metadata into Sleuth manually**.

{% tabs %}
{% tab title="Option 1: Link to metadata file" %}
In Azure on the "**SAML Certificates**" tile under your Enterprise Application, **copy the value** of the "**App Federation Metadata Url**" field:

<figure><img src="../../../../.gitbook/assets/image (7) (2).png" alt=""><figcaption></figcaption></figure>

In Sleuth, click the "**point Sleuth to metadata file URL**" link to trigger the input modal and **paste the copied URL** into the field, then click "**Save**":

<figure><img src="../../../../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

The remaining fields in Sleuth will get **populated automatically**, just click "**Test Metadata and Save**":

<figure><img src="../../../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Sleuth defaults all of the Advanced configuration to the most commonly used values, but depending on your IdP configuration you might need to adjust "**Advanced settings**".
{% endhint %}

## Assign Users/Groups to the Enterprise Application

On the Application's homepage click the "**1. Assign users and groups**" tile (_alternatively, you can click the "**Users and groups**" link in the left-hand navigation_):

<figure><img src="../../../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

Click the "**+Add user/group**" button and **assign Users/Groups** as needed:

<figure><img src="../../../../.gitbook/assets/image (49) (1).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Option 2: Input metadata manually" %}
**Fill in the necessary metadata** (_found in Azure AD_), using the following reference, and click "**Test Metadata and Save**":

<table><thead><tr><th>SLEUTH</th><th>AZURE AD</th><th>EXAMPLE</th><th data-hidden></th></tr></thead><tbody><tr><td><strong>Entity ID</strong></td><td>Azure AD Identifier</td><td><code>https://sts.windows.net/&#x3C;...></code></td><td></td></tr><tr><td><strong>SSO URL</strong></td><td>Login URL</td><td><code>https://login.microsoftonline.com/&#x3C;...></code></td><td></td></tr><tr><td><strong>SLO URL</strong></td><td>Logout URL</td><td><code>https://login.microsoftonline.com/&#x3C;...></code></td><td></td></tr><tr><td><strong>Certificate</strong></td><td>On the "<strong>SAML Certificates</strong>" tile click "<strong>Edit</strong>", then click the <strong>3 ellipses</strong> at the right end of the Active certificate and select "<strong>PEM certificate download</strong>".</td><td><code>-----BEGIN CERTIFICATE-----</code><br><code>&#x3C;...></code><br><code>-----END CERTIFICATE-----</code></td><td></td></tr></tbody></table>

<figure><img src="../../../../.gitbook/assets/image (44).png" alt=""><figcaption><p>Open the downloaded file with a text-/code editor and copy the contents to be pasted into the "Certificate" field in Sleuth.</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/image (4) (2).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

