---
title: Okta Identity Engine overview
meta:
  - name: I sorted out the information in this article, making sure to sort out legitimate new features from conceptual or background information. There were some areas in the doc that I removed completely because they described an outdated workflow, which removed a lot of confusion. I also re-ordered new features in order of importance/feature impact. I fixed a lot of passive sentences, streamlining the content for easier flow.
    content: Learn more about the Identity Engine authentication flow and new features now available.
---
Okta Identity Engine is a new authentication pipeline that provides valuable new features and a more flexible approach to your auth needs. 

> **Note**: If you are an admin, or are looking for product docs related to Identity Engine, see [Get started page](https://help.okta.com/okta_help.htm?type=oie&id=ext-get-started-oie).

There are three Identity Engine user authentication deployment models:

* **Okta-hosted Sign-In Widget (Recommended)**: Use the Okta-hosted redirect Sign-In Widget to authenticate users, then redirect back to your app. This is the recommended approach as it's the most secure and fastest to implement.
* **Embedded Sign-In Widget**: Embed the Sign-In Widget into your own code base to handle the authentication on your servers. This provides a balance between complexity and customization.
* **Embedded SDK-driven sign-in flow**: Use Okta SDKs to create a completely custom authentication experience. This option is the most complex, but offers the most control to experienced deployment managers.

See [Okta deployment models &mdash; redirect vs. embedded](/docs/concepts/redirect-vs-embedded/) for an overview of the different deployment models, and see [Sign users in](/docs/guides/sign-in-overview/) for implementation details.

## Identity Engine new features

In addition to three deployment modes, Identity Engine unlocks many new capabilities.

### App intent link support

App intent links are used to signal intent to access an application. These links are protocol-specific endpoints that you can use to initiate a sign-in flow to an application. Both Identity Provider and Service Provider initiated flows are supported.

Identity Engine app intent links location hosts the widget/sign-in experience for the app that the user is attempting to access and evaluate the Global Session Policy, authentication policy, and all other policies relevant to the sign-in experience. Since each app intent link is responsible for hosting the sign-in experience on Identity Engine, they share a common app intent link rate limit bucket/group similar to what existed for the centralized sign-in page on Classic Engine.

Example app intent link for a SAML application:
`http://${yourOktaDomain}/app/mysamlapp_1/${appInstanceID}/sso/saml`


### Authentication policies

Authentication policies [security policy frameworks](https://csrc.nist.gov/publications/detail/sp/800-63b/final) allow organizations to model security outcomes for an app. These policies are shareable across applications. For example, you can automatically step up authentication to a strong non-phishable factor when elevated risk is detected. Additionally, Identity Engine allows you to create flexible apps that can change their authentication methods without having to alter a line of code.

* [Configure a global session policy and authentication policies](/docs/guides/configure-signon-policy/)

* [Authentication policies](https://help.okta.com/okta_help.htm?type=oie&id=ext-about-asop)

* [Policies (high-level concept)](/docs/concepts/policies/)


### App context in email templates

Identity Engine makes app context available when a user enters an authentication flow. Context variables are available in our email templates, allowing customers to dynamically customize email style and content based on the app that triggers email notifications.

See [Customize email notifications > Use app context](/docs/guides/custom-email/main/#use-app-context).

### CAPTCHA support

CAPTCHA is a well-known strategy for mitigating attacks by bots. Identity Engine offers registration, sign-in, and account recovery integration of the two market-leading CAPTCHA services, [hCAPTCHA](https://www.hcaptcha.com/) and [reCAPTCHA](https://www.google.com/recaptcha/about/). 

> **Note**:  CAPTCHA support is available through the Okta-hosted and embedded Sign-In Widgets, but not SDKs.

### Interaction code grant type for embedded authentication

To enable a more customized user authentication experience, Okta introduces an extension to the [OAuth 2.0 and OpenID Connect](/docs/concepts/oauth-openid) standard called the [Interaction Code grant type](/docs/concepts/interaction-code/). This grant type allows apps using an embedded Okta Sign-In Widget and/or SDK to manage user interactions with the authorization server directly, rather than relying on a browser-based redirect to an authentication component (such as the Sign-In Widget).


## Identity Engine SDKs and sample apps

SDKs are available to integrate new Identity Engine features into your apps. Sample apps are also included to get you started. 

* [Browse our SDKs and samples](/code/)
* [Set up and explore our Identity Engine sample apps](/docs/guides/oie-embedded-common-download-setup-app/)


## Classic Engine support

Although Identity Engine is considered the default engine,  Classic Engine customers who don't yet want to upgrade can leverage existing Classic Engine functionality. 

Okta documentation refers to Identity Engine by default. If you are a Classic Engine user, you can find Classic Engine version documentation here: [Okta Classic Engine](/docs/guides/archive-overview/).

> **Note**: See [Identify your Okta solution](https://help.okta.com/okta_help.htm?type=oie&id=ext-oie-version) to determine your Okta version.
