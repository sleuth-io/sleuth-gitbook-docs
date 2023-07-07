# Okta Configuration

## Steps to follow

* [Create a new Application](okta-configuration.md#create-a-new-application)
* [Set up Single Sign-On](okta-configuration.md#set-up-single-sign-on)
  * [Configure Attributes](okta-configuration.md#configure-attributes)
* [Enter OKTA's metadata into Sleuth](okta-configuration.md#enter-oktas-metadata-into-sleuth)
  * Option 1: Link to metadata file
  * Option 2: Enter metadata manually
* [Assign People/Groups to the Application](okta-configuration.md#assign-people-groups-to-the-application)

## Create a new Application

Sign in to the **OKTA Dashboard** as an administrator. Open the menu in the top-left corner, expand the " **Applications**" section and click "**Applications**:

<figure><img src="../../../../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>

On the "**Applications** "page click "**Create App Integration**". In the pop-up "**Create a new app integration**" select "**SAML 2.0**" as the Sign-in method and click "**Next**":

<figure><img src="../../../../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

On the "**General Settings**" tab enter a name for your application (_e.g., Sleuth_) and click "**Next**":

<figure><img src="../../../../.gitbook/assets/image (31) (1).png" alt=""><figcaption></figcaption></figure>

## Set up Single Sign-On

On the "**Configure SAML**" page, **fill in the necessary metadata** (_found in Sleuth_), using the following reference:

| OKTA                            | SLEUTH                     | EXAMPLE                                                                               |
| ------------------------------- | -------------------------- | ------------------------------------------------------------------------------------- |
| **Single sign on URL**          | Assertion Consumer Service | `https://app.sleuth.io/complete/saml/`                                                |
| **Audience URI (SP Entity ID)** | SAML Entity ID             | `https://app.sleuth.io/saml/metadata/`                                                |
| **Default RelayState**          | Default Relay State        | <p><code>sleuth</code> </p><p><em>(should be your <strong>org slug</strong>)</em></p> |

Set the "**Name ID format**" to "**Email Address**" and click the "**Show Advanced Settings**" link to expand the settings:

<figure><img src="../../../../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>

Save the "**Sleuth x509 Certificate**" ([found in Sleuth](broken-reference)) in a .**pem** file, then click "**Browse files...**" next to "**Signature Certificate**" and **upload the saved file**. Activate the "**Enable Single Logout**" option and enter the necessary information:

| OKTA                  | SLEUTH                | EXAMPLE                           |
| --------------------- | --------------------- | --------------------------------- |
| **Single Logout URL** | Single Logout Service | `https://app.sleuth.io/saml/sls/` |

<figure><img src="../../../../.gitbook/assets/image (28) (1).png" alt=""><figcaption></figcaption></figure>

### Configure Attributes

In the "**Attribute Statements**" section add the following Attributes (_using the "**Add Another**" button_):

| NAME            | NAME FORMAT | VALUE          |
| --------------- | ----------- | -------------- |
| **email**       | Unspecified | user.email     |
| **first\_name** | Unspecified | user.firstName |
| **last\_name**  | Unspecified | user.lastName  |

<figure><img src="../../../../.gitbook/assets/image (30) (1).png" alt=""><figcaption></figcaption></figure>

Leave the "**Group Attribute Statements**" as they are.

Click "**Preview the SAML Assertion**" if you want to inspect the Assertion before proceeding. Then click "**Next**" at the bottom-right of the page.

On the "**Feedback**" page select "**I'm an Okta customer adding an internal app**" and click "**Finish**" at the bottom-right of the page (_you can leave the rest of the fields blank_).

## Enter OKTA's metadata into Sleuth

You can now choose between **pointing Sleuth to a URL** where the IdP's metadata is now available, or **entering the metadata into Sleuth manually**.

{% tabs %}
{% tab title="Option 1: Link to metadata file" %}
In OKTA in the "**SAML Signing Certificates**" section under your Application, find the certificate with status "**Active**", click on the "**Actions**" link at the right end of its row and click "**View IdP metadata**":

<figure><img src="../../../../.gitbook/assets/image (47) (1).png" alt=""><figcaption></figcaption></figure>

The **XML file** will open in a new tab in your browser -> **select and copy its entire URL**.

In Sleuth, click the "**point Sleuth to metadata file URL**" link to trigger the input modal and **paste the copied URL** into the field, then click "**Save**":

<figure><img src="../../../../.gitbook/assets/image (3) (3).png" alt=""><figcaption></figcaption></figure>

The remaining fields in Sleuth will get **populated automatically**, just click "**Test Metadata and Save**":

<figure><img src="../../../../.gitbook/assets/image (34) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Sleuth defaults all of the Advanced configuration to the most commonly used values, but depending on your IdP configuration you might need to adjust "**Advanced settings**".
{% endhint %}

## Assign People/Groups to the Application

On the Application's homepage click the "**Assignments**" tab, then click "**Assign**" and select either "**Assign to People**" (_to assign individual users_) or "**Assign to Groups**" (_to assign to groups of users_):

<figure><img src="../../../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Option 2: Input metadata manually" %}
In OKTA in the "**SAML Signing Certificates**" section under your Application, click the "**View SAML setup instructions**" button:

<figure><img src="../../../../.gitbook/assets/image (52) (1).png" alt=""><figcaption></figcaption></figure>

**Fill in the necessary metadata**, using the following reference, and click "**Test Metadata and Save**":

| SLEUTH          | OKTA                                 | EXAMPLE                                                                                                              |
| --------------- | ------------------------------------ | -------------------------------------------------------------------------------------------------------------------- |
| **Entity ID**   | Identity Provider Issuer             | `http://www.okta.com/<...>`                                                                                          |
| **SSO URL**     | Identity Provider Single Sign-On URL | `https://<...>.okta.com/app/<...>/sso/saml`                                                                          |
| **SLO URL**     | Identity Provider Single Logout URL  | `https://<...>.okta.com/app/<...>/slo/saml`                                                                          |
| **Certificate** | X.509 Certificate                    | <p><code>-----BEGIN CERTIFICATE-----</code><br><code>&#x3C;...></code><br><code>-----END CERTIFICATE-----</code></p> |

<figure><img src="../../../../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Sleuth defaults all of the Advanced configuration to the most commonly used values, but depending on your IdP configuration you might need to adjust "**Advanced settings**".
{% endhint %}
{% endtab %}
{% endtabs %}

