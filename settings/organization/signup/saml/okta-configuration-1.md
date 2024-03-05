# PingIdentity Configuration

## Steps to follow

* [Create a new Application](okta-configuration-1.md#create-a-new-application)
* [Set up Single Sign-On](okta-configuration-1.md#set-up-single-sign-on)
  * [Configure Attributes](okta-configuration-1.md#configure-attributes)
* [Enter PingIdentity's metadata into Sleuth](okta-configuration-1.md#enter-pingidentitys-metadata-into-sleuth)
  * Option 1: Link to metadata file
  * Option 2: Enter metadata manually
* [Assign People/Groups to the Application](okta-configuration-1.md#assign-people-groups-to-the-application)

## Create a new Application

Sign in to **PingIdentity** as an administrator. In the left-hand menu, expand the " **Applications**" section and click "**Applications**:

<figure><img src="../../../../.gitbook/assets/image (132).png" alt=""><figcaption></figcaption></figure>

On the "**Applications** "page click the :heavy\_plus\_sign:  icon to add a new Application. In the "**Add Application**" pane provide an "**Application Name**" (_e.g., Sleuth_), a "**Description**" and an "**Icon**" for the Application, select "**SAML Application**" as the "**Application Type**", and click "**Configure**":

<figure><img src="../../../../.gitbook/assets/image (150).png" alt=""><figcaption></figcaption></figure>

## Set up Single Sign-On

You have the choice between **Importing Metadata** (_from a file you downloaded from Sleuth_), **Importing from URL**, or **Manually Entering** the metadata into PingIdentity.



{% tabs %}
{% tab title="Import Metadata" %}
On the "**SAML Configuration**" page, select "**Import Metadata**", and click "**Select a file**" to find and select the metadata file on your computer (_click_ [_here_](https://help.sleuth.io/settings/organization/signup/saml#gather-sleuth-service-provider-metadata) _to find out how to download the file_):

<figure><img src="../../../../.gitbook/assets/image (151).png" alt=""><figcaption></figcaption></figure>

The "**ACS URLs**" and "**Entity ID**" fields will populate automatically. Click "**Save**".
{% endtab %}

{% tab title="Import From URL" %}
On the "**SAML Configuration**" page, select "**Import From URL**", **paste the following URL** into the "**Import URL**" field, and click "**Import**":

```url
https://app.sleuth.io/saml/metadata/
```

<figure><img src="../../../../.gitbook/assets/image (152).png" alt=""><figcaption></figcaption></figure>

The "**ACS URLs**" and "**Entity ID**" fields will populate automatically. Click "**Save**".
{% endtab %}

{% tab title="Manually Enter" %}
On the "**SAML Configuration**" page, select "**Manually Enter**", and **fill in the necessary metadata** (_found in Sleuth_), using the following reference:

| PINGIDENTITY  | SLEUTH                     | EXAMPLE                                |
| ------------- | -------------------------- | -------------------------------------- |
| **ACS URLs**  | Assertion Consumer Service | `https://app.sleuth.io/complete/saml/` |
| **Entity ID** | SAML Entity ID             | `https://app.sleuth.io/saml/metadata/` |

Click "**Save**".
{% endtab %}
{% endtabs %}

On the Application, switch to the "**Configuration**" tab, and click the **pencil icon** to enter edit mode:

<figure><img src="../../../../.gitbook/assets/image (137).png" alt=""><figcaption></figcaption></figure>

**Fill in any missing metadata** (_found in Sleuth_), using the following reference:

| PINGIDENTITY                 | SLEUTH                     | EXAMPLE                                                                                |
| ---------------------------- | -------------------------- | -------------------------------------------------------------------------------------- |
| **ACS URLS**                 | Assertion Consumer Service | `https://app.sleuth.io/complete/saml/`                                                 |
| **ENTITY ID**                | SAML Entity ID             | `https://app.sleuth.io/saml/metadata/`                                                 |
| **SLO ENDPOINT**             | Single Logout Service      | `https://app.sleuth.io/saml/sls/`                                                      |
| **SUBJECT NAMEID FORMAT**    | n/a                        | `urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress`                               |
| **TARGET APPLICATION URL**   | Default Relay State        | (unique to each Sleuth org, usually your `orgSlug`)                                    |
| **VERIFICATION CERTIFICATE** | Sleuth x509 Certificate    | if not already filled in, can be found in Sleuth (_needs to be saved as a `crt` file_) |

Leave other settings as they are and click "**Save**".

### Configure Attributes

Once again on the Application, switch to the "**Attribute Mappings**" tab, and click the **pencil icon** to enter edit mode:

<figure><img src="../../../../.gitbook/assets/image (139).png" alt=""><figcaption></figcaption></figure>

Edit the default Attribute `saml_subject` from `User ID` to `Email Address`, click the `...` to reveal the contextual menu, and click `Update NameFormat`:

<figure><img src="../../../../.gitbook/assets/image (140).png" alt=""><figcaption></figcaption></figure>

Select `urn:oasis:names:tc:SAML:2.0:attrname-format:unspecified` from the list of options and click "**Update**":

<figure><img src="../../../../.gitbook/assets/image (141).png" alt=""><figcaption></figcaption></figure>

Add the remaining required Attributes using the following reference and click "**Save**" when done:

| Attributes   | PingOne Mappings | NameFormat                                          |
| ------------ | ---------------- | --------------------------------------------------- |
| `first_name` | Given Name       | `urn:oasis:names:tc:SAML:2.0:attrname-format:basic` |
| `last_name`  | Family Name      | `urn:oasis:names:tc:SAML:2.0:attrname-format:basic` |
| `email`      | Email Address    | `urn:oasis:names:tc:SAML:2.0:attrname-format:basic` |

{% hint style="info" %}
Don't forget to **enable your Application** by flipping the toggle!
{% endhint %}

<figure><img src="../../../../.gitbook/assets/image (142).png" alt=""><figcaption></figcaption></figure>

## Enter PingIdentity's metadata into Sleuth

You can choose between **pointing Sleuth to a URL** where the IdP's metadata is now available, or **entering the metadata into Sleuth manually**.

{% tabs %}
{% tab title="Option 1: Link to metadata file" %}
In PingIdentity on the "**Configuration**" tab on your Application, click the **clipboard icon** next to the "**IDP Metadata URL**" to copy the URL:

<figure><img src="../../../../.gitbook/assets/image (144).png" alt=""><figcaption></figcaption></figure>

In Sleuth, click the "**point Sleuth to metadata file URL**" link to trigger the input modal and **paste the copied URL** into the field, then click "**Save**":

<figure><img src="../../../../.gitbook/assets/image (145).png" alt=""><figcaption></figcaption></figure>

The remaining fields in Sleuth will get **populated automatically**, just click "**Test Metadata and Save**":

<figure><img src="../../../../.gitbook/assets/image (146).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Sleuth defaults all of the Advanced configuration to the most commonly used values, but depending on your IdP configuration you might need to adjust "**Advanced settings**".
{% endhint %}
{% endtab %}

{% tab title="Option 2: Input metadata manually" %}
You'll find the data needed for this in PingIdentity on the "**Configuration**" tab on your Application under "**Connection Details**":

<figure><img src="../../../../.gitbook/assets/image (147).png" alt=""><figcaption></figcaption></figure>

**Fill in the necessary metadata**, using the following reference, and click "**Test Metadata and Save**":

| SLEUTH          | PINGIDENTITY                 | EXAMPLE                                                                                                              |
| --------------- | ---------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| **Entity ID**   | Issuer ID                    | `https://auth.pingone.eu/<...>`                                                                                      |
| **SSO URL**     | Single Signon Service        | `https://auth.pingone.eu/<...>/saml20/idp/sso`                                                                       |
| **SLO URL**     | Single Logout Service        | `https://auth.pingone.eu/<...>/saml20/idp/slo`                                                                       |
| **Certificate** | Download Signing Certificate | <p><code>-----BEGIN CERTIFICATE-----</code><br><code>&#x3C;...></code><br><code>-----END CERTIFICATE-----</code></p> |

<figure><img src="../../../../.gitbook/assets/image (148).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Sleuth defaults all of the Advanced configuration to the most commonly used values, but depending on your IdP configuration you might need to adjust "**Advanced settings**".
{% endhint %}
{% endtab %}
{% endtabs %}

## Assign Groups to the Application

On the Application, switch to the "**Access**" tab, and click the **pencil icon** to enter edit mode, and select Group which should have access to this Application, and click "**Save**":

<figure><img src="../../../../.gitbook/assets/image (149).png" alt=""><figcaption></figcaption></figure>
