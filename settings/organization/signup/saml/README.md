# SAML 2.0 Setup

To set up SAML integration you will need admin privileges in Sleuth and in your Identity Provider (IdP) system that supports SAML 2.0. Regardless of the specific IdP, the general setup process is roughly the same:

1. ****[**Gather Sleuth Service Provider (SP) Metadata.**](./#gathering-sleuth-service-provider-metadata) This is the information you will need in order for your IdP to identify Sleuth as a trusted service provider.
2. ****[**Establish Sleuth as a trusted SP in your IdP.**](./#establish-sleuth-as-a-trusted-service-provider) This step requires administrator privileges in your IdP.
3. ****[**Enter IdP metadata into Sleuth.**](./#enter-idp-metadata-into-sleuth) Finalize communication configuration between Sleuth and IdP
4. ****[**Enable SAML login for users.**](./#enable-saml-login)****

To begin SAML configuration navigate to the "**Authentication**" tab under "**Organization settings**" and click "**Configure SAML Authentication**":

<figure><img src="../../../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

## Gather Sleuth Service Provider Metadata

To view the Sleuth SAML metadata expand the "**Sleuth Service Provider data**" section by clicking on the title.

<figure><img src="../../../../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>

Once expanded, you can either **download the metadata XML file** (_if your IdP supports metadata file imports_) or **manually copy-paste these values** when setting up Sleuth as a trusted service provider within your IdP.

<figure><img src="../../../../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

## Establish Sleuth as a trusted Service Provider

To establish Sleuth as a trusted SP you will need information from the previous step and administrator privileges in your IdP.

This section includes instructions on how to configure your Identity Provider in order to enable the login:

* [Okta](okta-configuration.md)
* [Azure AD](azure-ad-configuration.md)

{% hint style="info" %}
Even if your Identity Provider is not specified in the list above, Sleuth is respecting the **SAML 2.0 standard** so you can integrate every Identity Provider that supports the standard.

Feel free to contact us at [**support@sleuth.io**](mailto:support@sleuth.io?subject=Need%20help%20setting%20up%20SAML) in case of any problems setting up the integration.
{% endhint %}

## Enter IdP metadata into Sleuth

To enter your IdP's metadata into Sleuth you will need information from the previous steps and administrator privileges in Sleuth.

This section includes instructions on how to configure Sleuth in order to enable the login with your selected IdP:

* [Okta](okta-configuration.md#enter-oktas-metadata-into-sleuth)
* [Azure AD](azure-ad-configuration.md#enter-azures-metadata-into-sleuth)

{% hint style="info" %}
Even if your Identity Provider is not specified on the list above, Sleuth is respecting the **SAML 2.0 standard** so you can integrate any Identity Provider that supports the standard.

Feel free to contact us at [**support@sleuth.io**](mailto:support@sleuth.io?subject=Need%20help%20setting%20up%20SAML) in case of any problems setting up the integration.
{% endhint %}

## Enable SAML login

Once you saved the configuration you will need to successfully log in using SAML before you can set it to be your only [allowed login method](../#allowed-login-methods).

1. Log out of Sleuth.
2. On the login page: enter your **email** and click "**Continue**".
3. Clicking on "**SAML**" will start the login process via your IdP.
