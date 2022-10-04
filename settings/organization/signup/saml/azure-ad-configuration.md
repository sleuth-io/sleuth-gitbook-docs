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

<figure><img src="../../../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

When prompted, select "**SAML**" as the **single sign-on method**, then proceed with one of the 2 options explained below:

{% tabs %}
{% tab title="Option 1: Upload metadata XML file" %}
Click the "**Upload metadata file**" button to trigger the file import modal, **select the file** to upload, and click "**Add**":

<figure><img src="../../../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

Once the file is uploaded, you'll see a preview of the imported metadata. If needed/desired, you can still make changes, although it generally shouldn't be necessary.

One **optional field** that doesn't get populated automatically is "**Relay State**"; you can specify it manually by inputting your **Sleuth org slug** (_find it in your URL -> `https://app.sleuth.io/`**`<org-slug>`**_) and clicking "**Save**" at the top:

<figure><img src="../../../../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Option 2: Enter metadata manually" %}
On the "**Basic SAML Configuration**" tile click "**Edit**":

<figure><img src="../../../../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>

**Fill in the necessary metadata** (_found in Sleuth_), using the following reference, and click "**Save**":

| AZURE AD                                       | SLEUTH                     | EXAMPLE                                                                                        |   |
| ---------------------------------------------- | -------------------------- | ---------------------------------------------------------------------------------------------- | - |
| **Identifier (Entity ID)**                     | SAML Entity ID             | `https://app.sleuth.io/saml/metadata/`                                                         |   |
| **Reply URL (Assertion Consumer Service URL)** | Assertion Consumer Service | `https://app.sleuth.io/complete/saml/`                                                         |   |
| **Relay State (Optional)**                     | Default Relay State        | <p><code>sleuth</code><br><code></code><em>(should be your <strong>org slug</strong>)</em></p> |   |
| **Logout Url (Optional)**                      | Single Logout Service      | `https://app.sleuth.io/saml/sls/`                                                              |   |

<figure><img src="../../../../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>
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

<figure><img src="../../../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

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

<figure><img src="../../../../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Option 2: Input metadata manually" %}
**Fill in the necessary metadata** (_found in Azure AD_), using the following reference, and click "**Test Metadata and Save**":

| SLEUTH          | AZURE AD                                                                                                                                                                  | EXAMPLE                                                                                                              |   |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | - |
| **Entity ID**   | Azure AD Identifier                                                                                                                                                       | `https://sts.windows.net/<...>`                                                                                      |   |
| **SSO URL**     | Login URL                                                                                                                                                                 | `https://login.microsoftonline.com/<...>`                                                                            |   |
| **SLO URL**     | Logout URL                                                                                                                                                                | `https://login.microsoftonline.com/<...>`                                                                            |   |
| **Certificate** | On the "**SAML Certificates**" tile click "**Edit**", then click the **3 ellipses** at the right end of the Active certificate and select "**PEM certificate download**". | <p><code>-----BEGIN CERTIFICATE-----</code><br><code>&#x3C;...></code><br><code>-----END CERTIFICATE-----</code></p> |   |

<figure><img src="../../../../.gitbook/assets/image (44).png" alt=""><figcaption><p>Open the downloaded file with a text-/code editor and copy the contents to be pasted into the "Certificate" field in Sleuth.</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

