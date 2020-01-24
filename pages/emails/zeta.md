---
title: Zeta
---
## Overview

![Zeta](/images/pages/email/zeta/zeta.png)

This guide will walk you through how to setup your email campaigns with **[Zeta](https://zetaglobal.com/){:target="\_blank"}** using Branch Universal Email to automatically convert your email links into **multi-platform deep links**

The basic integration involves four parts:

1. [Activate integration and setup link behavior](#activate-integration)
1. [Configure your mobile app](#configure-your-mobile-app)
1. [Configure your ESP](#configure-your-esp)
1. [Updating the links in your email](#using-universal-email)

Universal Email allows you to automatically convert your email links into multi-platform deep links that take users directly to content in the app on mobile devices, while still maintaining the same web experience for desktop and mobile users without the app.

When a link is clicked by a user without the app, it will route that user to the original web URL (including on desktop). When a link is clicked by a user with your app, it will direct that user into the relevant in-app content regardless of platform or email client.

## Setup

### Prerequisites

This guide requires you to have already [integrated the Branch SDK](/apps/ios/) into your app.

To open the app directly on iOS 9.2+, you must configure your email integration and your app to support [Universal Links](/deep-linking/universal-links/) in emails.

Contact your Branch Account Manager or [accounts@branch.io](mailto:accounts@branch.io) at any time for assistance with the setup steps.

## Activate integration

### Choose your email service provider

Navigate to the [Universal Email](https://dashboard.branch.io/email){:target="\_blank"} section of the Branch dashboard. Select <notranslate>**Zeta**</notranslate> and click <notranslate>**Enable**</notranslate>.

### Set up Email link behavior

Branch turns the web URLs you put into your emails into Branch deep links, opening the app for users with your app installed to that same content in the app.

![image](/images/pages/email/users-with-app.png)

To do this, it must be possible to map your web URL content (e.g. a page with brown loafers at `https://shop.com/shoes/brown-loafers`) into a working deep link that takes users to brown loafers in the app. The Universal Email [setup flow](https://dashboard.branch.io/email){:target="\_blank"} will attempt to automatically detect this mapping for you.

If you do not want to set this up yet, you can select <notranslate>**No, just open to app homepage for now**</notranslate>.

![image](/images/pages/email/app-homepage.png)

By default, email deep links will redirect users _without your app_ to the same content on the web instead.

![image](/images/pages/email/users-without-app.png)

If you would like to send users to the App Store or another default you have specified in Link Settings, you can select <notranslate>**Open to default redirects**</notranslate>.

![image](/images/pages/email/default-redirects.png)

#### Checking your deep linking setup

If you chose **not** to set up deep linking to specific content within your app, then you can [skip this step](#next-steps).

![image](/images/pages/email/responsys/enter-web-url.png)

In this step, you will want to enter a web URL that corresponds to a specific screen within your app. In other words, the webpage should have content that also exists in your app. If you do not know whether your web content also exists in-app, try any URL other than your website homepage. Some examples:

- A product page, like a page with brown loafers
- An article
- A content page, like a video or image

Once you choose one and click <notranslate>**Submit**</notranslate>, [meta tags that can be used for deep linking](/web/hosted-data/) will be retrieved from your webpage. You will see a result indicating the mapping between your web content and your app content. For a full explanation of the tests run on this page and the possible results, check out the [support section](https://support.branch.io/support/solutions/articles/6000194014-understanding-deep-linked-email-validation-errors).

#### We couldn't determine your deep linking setup

If an app deep linking scheme that maps to your web content cannot be successfully detected, you can [configure your settings manually](#deep-linking-settings-for-email), or you can reach out to your Branch account manager or support for assistance.

![image](/images/pages/email/failure-result.png)

We will help you set up one of the following methods:

If you use unique key/value data as deep link values:

1. _Recommended:_ <notranslate>**Hosted deep link data:**</notranslate> You can host your deep link data on your website with a metatag that looks like this `<meta name="branch:deeplink:my_key" content="my_value" />` where `my_key` and `my_value` will become a key value pair in deep link data. For each web URL, Branch will look for those tags and embed the deep link data (if found) into the deep link. Note that Branch also accepts App Links tags for deep linking. For more details, please read [Hosted Deep Link Data](/getting-started/hosted-deep-link-data/guide/).
1. <notranslate>**As query parameters:**</notranslate> Simply append query parameters on to your web url and Branch will take those parameters and put them in deep link data.

If you use your web URL as a deep link value:

1. <notranslate>**URL path:**</notranslate> If you use the path of your web URL as your  `$deeplink_path` value, or any other deep link value, then the configuration will automatically take the path of the URL and put it in deep link data.
1. <notranslate>**Full URL:**</notranslate> If you use the full web URL as your `$deeplink_path` value, or any other deep link value, then the configuration will take the entire URL and put it in deep link data.

!!! protip "Host deep link data for more than just emails"
    The Branch [Quick Link creator](/getting-started/creating-links/dashboard/) also scrapes your web URL for deep link data to make link creation even easier. [Hosting Deep Link Data](/getting-started/hosted-deep-link-data/guide/) on your website will make using Branch products easier in future.

#### Deep linking settings for email

The following are all the possible settings you can configure for deep linking with email.

##### Link Behavior

Setting | Example | Link Data Result
--- | --- | ---
<notranslate>**Open the app homepage**</notranslate> | No settings configured to generate deep link data for email; email links will route to the app homepage.
<notranslate>**Open to specific app content**</notranslate> | Deep link to specific app content based on one or more of the following settings.
Translate query parameters on URLs into Branch link data | <notranslate>**URL:**</notranslate> `https://shop.com/shoes/brown-loafers&product_id=123456` | `product_id: 123456`
Translate web URL into Branch link data: <br> Full URL for key ______ | <notranslate>**URL:**</notranslate> `https://shop.com/shoes/brown-loafers` <br> <notranslate>**Key:**</notranslate> `$canonical_url` | `$canonical_url: https://shop.com/shoes/brown-loafers`
Translate web URL into Branch link data: <br> URL path for key ______ | <notranslate>**URL:**</notranslate> `https://shop.com/shoes/brown-loafers` <br> <notranslate>**Key:**</notranslate> `$deeplink_path` | `$deeplink_path: shoes/brown-loafers`
Retrieve hosted deep link data from website and translate into Branch link data | <notranslate>**URL:**</notranslate> `https://shop.com/shoes/brown-loafers` <br> <notranslate>**Meta Tags:**</notranslate> `<meta name="branch:deeplink:product_id" content="123456" />` | `product_id: 123456`
Strip protocol (http:// or https://): <br> from $deeplink_path <br> from $ios_deeplink_path <br> from $android_deeplink_path <br> *Note: Typically used with one of the other settings.* | <notranslate>**URL:**</notranslate> `https://shop.com/shoes/brown-loafers` <br> <notranslate>**Other Settings:**</notranslate> Translate web URL into Branch link data: Full URL for key `$deeplink_path` | `$deeplink_path: shop.com/shoes/brown-loafers`
Translate query parameters on URLs into Branch link data from parameter ______ to key ______ <br> *Note: Not configurable in the UI. [Contact support](https://support.branch.io/support/tickets/new){:target="_blank"} to use this setting.* | <notranslate>**URL:**</notranslate> `https://shop.com/shoes/brown-loafers&product_id=123456&utm_content=shoes` <br> <notranslate>**Parameter:**</notranslate> `utm_content` <br> <notranslate>**Key:**</notranslate> `category` | `category: shoes`

##### Link behavior for users without your app

Setting | Description
--- | ---
Open to specific web content | Route to the original URL specified in the email.
Open to default redirects | Route to defaults specified in [Link Settings](https://dashboard.branch.io/link-settings){:target="_blank"}.


### Tell us your click tracking domain

You can retrieve your click tracking domain from the <notranslate>**Account Settings**</notranslate> section of your Zeta account. If you have not added a custom click tracking domain yet, follow the instructions [here](#setup-a-custom-click-tracking-domain).

![image](/images/pages/email/zeta/setup-config.png)

### Configure your app for your click tracking domain

You can send ESP configuration to your development team

![image](/images/pages/email/send-email.png)

In this prompt, enter the email of someone on your team who is qualified to modify your iOS app, and then click <notranslate>**Send**</notranslate>. They will complete the [technical setup](#configure-your-mobile-app) steps below.

Click Next to proceed to Validate and test the integration

### Validate and Test

![image](/images/pages/email/setup-verification.png)

The last step of the [Universal Email setup flow](https://dashboard.branch.io/email){:target="\_blank"} validates whether you have completed all necessary steps and whether an engineer on your team has completed the integration steps. You will also see recommendations for how to improve your email integration.

Once it's done the AASA file and SSL certificate - required for Universal Links - specific to that domain will be generated.

The conversion to Branch links will only work when your links are wrapped in your click tracking domain. To test links without wrapping, please generate a test link on the Verification step of email onboarding, also accessible by clicking the gear icon for your ESP on the [email page](https://dashboard.branch.io/email){:target="\_blank"}.

![image](/images/pages/email/setup-test.png)

!!! protip "What happens to your links behind the scenes?"
    This is what a link looks like within your email template:

    ```html
    http://example.com/?foo=bar
    ```

    When a user clicks your link, Branch processes the link and converts it to something like this:

    ```html
    https://vza3.app.link/3p?%243p=e_xx&%24original_url=http%3A%2F%2Fexample.com%2F%3Ffoo%3Dbar
    ```

    Where `vza3.app.link` is your Branch domain.

## Configure your mobile app

### Technical setup

The following app changes ensure that your email integration supports [Universal Links](/getting-started/universal-app-links/). You will need access to your app code to make these changes.

You should have [received an email from Branch](#configure-your-app-for-your-click-tracking-domain) with your ESP's click tracking domain. If not, likely you or someone on your team still needs to complete the [Universal Email setup flow](#set-up-email-link-behavior).

!!! protip "How does it work?"
    Apple recognizes the click tracking domain as a Universal Link, and opens the app immediately without the browser opening. Once the app has opened, Branch will collect the referring URL that opened the app (at this time, it will be the click tracking url). Inside the app, Branch will robotically “click” the link, registering the click with the ESP, and returning the Branch link information to the Branch SDK inside the app. This information is then used to deep link the user to the correct in-app content. See the [Support](#support) section for more information.


### Add your click tracking domain to your Associated Domains

To enable Universal Links on your click tracking domain, you'll need to add the click tracking domain to your Associated Domains entitlement.

1. In Xcode, go to the `Capabilities` tab of your project file.
1. Scroll down and enable <notranslate>**Associated Domains**</notranslate> if it is not already enabled.

    ![image](/images/pages/email/enable-associated-domains.png)

1. Copy your click tracking domain from the [email you received from Branch](#configure-your-app-for-your-click-tracking-domain), or retrieve it from your ESP's settings.
1. In the `Domains` section, click the `+` icon and add your click tracking domain. For example, if your click tracking domain is `email.example.com`, add an entry for `applinks:email.example.com`.

    ![image](/images/pages/email/add-domain.png)

!!! protip "Having trouble or new to Universal Links?"
    Follow [these instructions](/deep-linking/universal-links/) for more details on enabling Universal Links in the Branch dashboard and in Xcode.

### Handle links for web-only content

If you have links to content that exists only on web, and not in the app (for example, a temporary marketing webpage that isn't in the app) then this code snippet will ensure all links that have not had the deep linking script applied will open in a browser.

You should add this code snippet inside the deep link handler code block. Note that this uses query parameter `$web_only=true`. This should match the [query parameter on the web URL](#flag-your-web-only-links) you enter in the email.

```
[branch initSessionWithLaunchOptions:launchOptions andRegisterDeepLinkHandler:^(NSDictionary *params, NSError *error) {
  // params are the deep linked params associated with the link that the user clicked before showing up.
  if (params[@"$3p"] && params[@"$web_only"]) {
            NSURL *url = [NSURL URLWithString:params[@"$original_url"]];
            if (url) {
                [application openURL:url]; // check to make sure your existing deep linking logic, if any, is not executed, perhaps by returning early
            }
  } else { 
    // it is a deep link
    GDLog(@"branch deep link: %@", [params description]); 
    [self handleBranchDeeplink:params];
  }
}];
```

### Return YES to continueUserActivity

When users enter your app via a Universal Link, we check to see to see if the link URL contains `app.link`. If so, `handledByBranch` will return `YES`. If not, `handledByBranch` will return `NO`. This allows us to explicitly confirm the incoming link is from Branch without making a server call.

For most implementations this will never be an issue, since your deep links will be routed correctly either way. However, if you use a custom link domain *and* you rely on `handledByBranch` to return `YES` for every incoming Branch-generated Universal Link, you can inform the Branch SDK by following these steps:

1. In your <notranslate>**Info.plist**</notranslate> file, create a new key called `branch_universal_link_domains`.
1. Add your custom domain(s) as a string. ![image](/images/pages/deep-linking/universal-links/branch-universal-link-domain.png)
1. Save the file.

!!! tip "Multiple custom domains"
	If you have an unusual situation with multiple custom link domains, you may also configure `branch_universal_link_domains` as an array of strings. ![image](/images/pages/deep-linking/universal-links/branch-universal-link-domains.png)

## Configure your ESP

### Setup a custom click tracking domain

1. Add and verify a custom click tracking domain in the <notranslate>**Account Settings**</notranslate> section of your Zeta account:

!!! tip "Adding a custom click-tracking domain"
    If you need help with setting up a custom click-tracking domain - please ask your account manager or request support at Zeta.

### Set up your click tracking domain

After you added and verified a click tracking domain you have to update DNS CNAME for it and point it to **`thirdparty.bnc.lt`**. Once the CNAME record is added, please allow up to an hour for Branch to generate SSL and AASA files for your click tracking domain.

!!! warning "SSL Changes"
	Please be aware that it may take up to an hour to resolve SSL errors once you change the CNAME. During this time, link redirects on the click tracking domain will redirect to `branch.io`. If you are making this change to a live domain that has email click traffic from your users, it’s best to schedule time with your Branch account manager to expedite the changes during a time of low click traffic.

## Using Universal email

Once you’ve completed the [one time setup steps](#setup), it’s time to send your first email.

This guide will identify which web links you'd like to open the app and deep link, as well as convert them to Branch links.

### Flag your deep links

For the email links that you would like to deep link to content, add `$deep_link=true` to the URL as a query parameter, for example:

```html
<a href="links.example.com?$deep_link=true" >Link to your app!</a>
```

This will ensure that your links are converted to Branch links that will open the app on iOS and Android, with full tracking and attribution.

### Flag your web-only links

With your email service provider, all email links will open the app by default. In order for your app to know that the email link should bounce to web after opening the app, add `$web_only=true` to your links as a query parameter, for example:

```html
<a href="links.example.com?$web_only=true" >Link to your app!</a>
```

!!! caution "Handle links for web-only content"
    Make sure you have completed the [technical setup steps](#handle-links-for-web-only-content) to handle web-only links within your app.

## Support

Curious about how email works and more FAQ? **Visit our [Universal Email Overview](/emails/universal-email/) page**.
