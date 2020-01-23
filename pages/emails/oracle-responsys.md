---
title: Oracle Responsys
---
## Overview

![Oracle Responsys](/_assets/img/pages/email/oracle-responsys/oracle-responsys.png)

This guide will walk you through how to setup your email campaigns with **[Oracle Responsys](http://responsys.com/){:target="\_blank"}** using Branch Universal Email to automatically convert your email links into **multi-platform deep links**

The basic integration involves four parts:

1. [Activate integration and setup link behavior](#activate-integration)
1. [Configure your mobile app](#configure-your-mobile-app)
1. [Configure your ESP](#configure-your-esp)
1. [Updating the links in your email](#using-universal-email)

Universal Email allows you to automatically convert your email links into multi-platform deep links that take users directly to content in the app on mobile devices, while still maintaining the same web experience for desktop and mobile users without the app.

When a link is clicked by a user without the app, it will route that user to the original web URL (including on desktop). When a link is clicked by a user with your app, it will direct that user into the relevant in-app content regardless of platform or email client.

## Setup

To use the Branch Link Conversion SDK, you'll need an <notranslate>**EMD (Email Message Designer)**</notranslate> enabled account. If you're using the Classic dashboard, or if you’re not sure, please talk to your Responsys Account Manager.

### Prerequisites

This guide requires you to have already [integrated the Branch SDK](/apps/ios/) into your app.

To open the app directly on iOS 9.2+, you must configure your email integration and your app to support [Universal Links](/deep-linking/universal-links/) in emails.

Contact your Branch Account Manager or [accounts@branch.io](mailto:accounts@branch.io) at any time for assistance with the setup steps.

## Activate integration

### Choose your email service provider

Navigate to the [Universal Email](https://dashboard.branch.io/email){:target="\_blank"} section of the Branch dashboard. Select <notranslate>**Oracle-Responsys**</notranslate> and click <notranslate>**Enable**</notranslate>.

### Set up Email link behavior

Branch turns the web URLs you put into your emails into Branch deep links, opening the app for users with your app installed to that same content in the app.

![image](/_assets/img/pages/email/users-with-app.png)

To do this, it must be possible to map your web URL content (e.g. a page with brown loafers at `https://shop.com/shoes/brown-loafers`) into a working deep link that takes users to brown loafers in the app. The Universal Email [setup flow](https://dashboard.branch.io/email){:target="\_blank"} will attempt to automatically detect this mapping for you.

If you do not want to set this up yet, you can select <notranslate>**No, just open to app homepage for now**</notranslate>.

![image](/_assets/img/pages/email/app-homepage.png)

By default, email deep links will redirect users _without your app_ to the same content on the web instead.

![image](/_assets/img/pages/email/users-without-app.png)

If you would like to send users to the App Store or another default you have specified in Link Settings, you can select <notranslate>**Open to default redirects**</notranslate>.

![image](/_assets/img/pages/email/default-redirects.png)

#### Checking your deep linking setup

If you chose **not** to set up deep linking to specific content within your app, then you can [skip this step](#next-steps).

![image](/_assets/img/pages/email/responsys/enter-web-url.png)

In this step, you will want to enter a web URL that corresponds to a specific screen within your app. In other words, the webpage should have content that also exists in your app. If you do not know whether your web content also exists in-app, try any URL other than your website homepage. Some examples:

- A product page, like a page with brown loafers
- An article
- A content page, like a video or image

Once you choose one and click <notranslate>**Submit**</notranslate>, [meta tags that can be used for deep linking](/web/hosted-data/) will be retrieved from your webpage. You will see a result indicating the mapping between your web content and your app content. For a full explanation of the tests run on this page and the possible results, check out the [support section](https://support.branch.io/support/solutions/articles/6000194014-understanding-deep-linked-email-validation-errors).

#### We couldn't determine your deep linking setup

If an app deep linking scheme that maps to your web content cannot be successfully detected, you can [configure your settings manually](#deep-linking-settings-for-email), or you can reach out to your Branch account manager or support for assistance.

![image](/_assets/img/pages/email/failure-result.png)

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

You can retrieve your click tracking domain from your Responsys settings. If you have not added a custom click tracking domain yet, follow the instructions [here](#setup-a-custom-click-tracking-domain).

![image](/_assets/img/pages/email/oracle-responsys/setup-config.png)

### Send your AASA file to your ESP

![image](/_assets/img/pages/email/responsys/configure-responsys-2.png)

Your AASA file must be uploaded to your click tracking domain by your email service provider. Your ESP account manager will do this for you - enter their email and click <notranslate>**Send**</notranslate>, and they will receive an email with the file and request to upload.

### Configure your app for your click tracking domain

You can send ESP configuration to your development team

![image](/_assets/img/pages/email/send-email.png)

In this prompt, enter the email of someone on your team who is qualified to modify your iOS app, and then click <notranslate>**Send**</notranslate>. They will complete the [technical setup](#configure-your-mobile-app) steps below.

Click Next to proceed to Validate and test the integration

### Validate and Test

![image](/_assets/img/pages/email/setup-verification.png)

The last step of the [Universal Email setup flow](https://dashboard.branch.io/email){:target="\_blank"} validates whether you have completed all necessary steps and whether an engineer on your team has completed the integration steps. You will also see recommendations for how to improve your email integration.

Once it's done the AASA file and SSL certificate - required for Universal Links - specific to that domain will be generated.

The conversion to Branch links will only work when your links are wrapped in your click tracking domain. To test links without wrapping, please generate a test link on the Verification step of email onboarding, also accessible by clicking the gear icon for your ESP on the [email page](https://dashboard.branch.io/email){:target="\_blank"}.

![image](/_assets/img/pages/email/setup-test.png)

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

    ![image](/_assets/img/pages/email/enable-associated-domains.png)

1. Copy your click tracking domain from the [email you received from Branch](#configure-your-app-for-your-click-tracking-domain), or retrieve it from your ESP's settings.
1. In the `Domains` section, click the `+` icon and add your click tracking domain. For example, if your click tracking domain is `email.example.com`, add an entry for `applinks:email.example.com`.

    ![image](/_assets/img/pages/email/add-domain.png)

!!! protip "Having trouble or new to Universal Links?"
    Follow [these instructions](/deep-linking/universal-links/) for more details on enabling Universal Links in the Branch dashboard and in Xcode.

### Return YES to continueUserActivity

When users enter your app via a Universal Link, we check to see to see if the link URL contains `app.link`. If so, `handledByBranch` will return `YES`. If not, `handledByBranch` will return `NO`. This allows us to explicitly confirm the incoming link is from Branch without making a server call.

For most implementations this will never be an issue, since your deep links will be routed correctly either way. However, if you use a custom link domain *and* you rely on `handledByBranch` to return `YES` for every incoming Branch-generated Universal Link, you can inform the Branch SDK by following these steps:

1. In your <notranslate>**Info.plist**</notranslate> file, create a new key called `branch_universal_link_domains`.
1. Add your custom domain(s) as a string. ![image](/_assets/img/pages/deep-linking/universal-links/branch-universal-link-domain.png)
1. Save the file.

!!! tip "Multiple custom domains"
	If you have an unusual situation with multiple custom link domains, you may also configure `branch_universal_link_domains` as an array of strings. ![image](/_assets/img/pages/deep-linking/universal-links/branch-universal-link-domains.png)

## Configure your ESP

### Setup a custom click tracking domain

!!! tip "Adding a custom click-tracking domain"
    If you need help with setting up a custom click-tracking domain - please ask your account manager or request support at Oracle Responsys.

### Set up your click tracking domain

After you added and verified a click tracking domain you have to update DNS CNAME for it and point it to **`thirdparty.bnc.lt`**. Once the CNAME record is added, please allow up to an hour for Branch to generate SSL and AASA files for your click tracking domain.

!!! warning "SSL Changes"
	Please be aware that it may take up to an hour to resolve SSL errors once you change the CNAME. During this time, link redirects on the click tracking domain will redirect to `branch.io`. If you are making this change to a live domain that has email click traffic from your users, it’s best to schedule time with your Branch account manager to expedite the changes during a time of low click traffic.

## Using Universal email

Once you’ve completed the [one time setup steps](#setup), it’s time to send your first email.

This guide will identify which web links you'd like to open the app and deep link, as well as convert them to Branch links.

### Options for generating Branch links for email

There are a few different ways you can create Branch links that are compatible with Universal Email + Responsys. You will need to replace the web URLs in your templates with these. To create Branch links, you can either:

1. [Use the Branch Responsys SDK](#use-the-branch-responsys-sdk)
1. [Making regular Branch links compatible with email](#making-regular-branch-links-compatible-with-email)
1. [Create email links via API without changing your email templates](#create-email-links-via-api-without-changing-your-email-templates)
1. [Convert all web links in your email to deep links](#convert-all-web-links-in-your-email-to-deep-links)

**Responsys uses the shortcode `e_rs` for links in emails** - please use this in place of `e_xx` in the guide below.

#### Use the Branch Responsys SDK

In this step, we'll upload an SDK that makes it very easy to create deep links in your emails.  Please remember that this will require an EMD (Email Message Designer) enabled account.

!!! protip "Watch how to do this instead"
    There is also a [tutorial video](https://www.youtube.com/watch?v=u8h8KlqFvo4){:target="\_blank"} that walks through these steps.

1. Work with your Branch account manager to modify the following code snippet, replacing `DOMAIN-HERE` with your Branch base domain:

    ```
    <#macro deeplink link_to_be_wrapped><#assign branch_base_url="https://DOMAIN-HERE/3p?%243p=e_rs"><#assign final_link=branch_base_url + "&%24original_url=" + link_to_be_wrapped?url("ISO-8859-1")><a href="${final_link}"><#nested></a></#macro> <#macro tracked_deeplink link_to_be_wrapped><#assign branch_base_url="https://DOMAIN-HERE/3p?%243p=e_rs"><#assign deeplink=branch_base_url + "&%24original_url=" + link_to_be_wrapped?url("ISO-8859-1")></#macro>
    ```

1. Log in to your Responsys account.
1. In the Responsys Dashboard, open your Content Library. You can also access it via the Shortcuts screen on the main page:

    ![image](/_assets/img/pages/email/responsys/responsys-shortcuts.png)

1. Once you are in the Content Manager, you’ll see a list of folders where content is stored. Under <notranslate>**All Content**</notranslate>, create a new folder named `Branch_SDK`:

    ![image](/_assets/img/pages/email/responsys/responsys-new-folder.png)

1. Select the <notranslate>**Branch_SDK**</notranslate> folder and then click <notranslate>**Create Document**</notranslate>:

    ![image](/_assets/img/pages/email/responsys/responsys-create-document.png)

1. In the Create Document window:
    * Enter `branch-sdk` in the “Document Name” field.
    * In the <notranslate>**Content Box**</notranslate>, delete all the text.
    * Paste the snippet you copied in <notranslate>**1**</notranslate>.
    * Click Save.

      ![image](/_assets/img/pages/email/responsys/responsys-snippet.png)

You have now successfully created the deep linking script. Your file structure should look as follows:

![image](/_assets/img/pages/email/responsys/deep-linked-email-manage-content.png)

##### Configure your Responsys email templates

This code is referred to as the <notranslate>"Branch script"</notranslate> - this script will convert your web URLs to deep links.

The Responsys integration requires you to add email template code in two places.

1. At the top of an email template
2. Immediately before a hyperlink

Copy the following snippet, and using the “Source” view, paste the snippet directly under the `<html>` tag for every template you plan to add deep linking to.

```
<#include "cms://contentlibrary/Branch_SDK/branch-sdk.htm">
```

##### Configuring the Responsys Link Table

For the Branch SDK to generate Branch links in the email or the 3P links while redirections, the Link Tracking table for the email template should contain the following two LINK NAME with the `${deeplink}` as the <notranslate>**LINK URL**</notranslate>.

![image](/_assets/img/pages/email/responsys/configure-responsys-5.png)

*For creating tracked links, ensure that <notranslate>**‘Track Link’**</notranslate> is set to <notranslate>**ON**</notranslate>. Tracked links will be generated under the Responsys Click Tracking Domain and will then redirect to a Branch 3p link (the link added as the base URL in the Branch_SDK.htm file.*
##### Create deep links

Wherever you are using `<a>` tags in your email templates, replace those with `<@deeplink>` tags, or add `<@tracked_deeplink />` for web URLs that you would like to deep link.

Here's how it looks with Link Tracking disabled.

*Before:*
`<a href="https://branch.io">Example link</a>`

*After:*
`<@deeplink "https://branch.io">Example link</@deeplink>`
{% endexample %}

With link tracking enabled, you can still use Branch links in emails.

*Before:*
`<a href="https://branch.io/product/1234">Example link</a>`

*After:*
`<@tracked_deeplink "https://branch.io/product/1234" />
<a href="${clickthrough('TEST_TRACKED_DEEPLINK' , 'deeplink=' + deeplink)}">Example link</a>`

This latter example pulls from a Link Table.

![image](/_assets/img/pages/email/responsys/deep-linked-email-template.png)

#### Making regular Branch links compatible with email

Be sure to add `"$3p":"e_xx"` to the deep link data of any links you use in email to ensure Universal Link and click tracking works as expected.

#### Create email links via API without changing your email templates

To create email links via API, please use the instructions on how to [create links via API](/apps/api/#link-create), but include the following key value pairs in your call:

1. `"$3p":"e_xx"` This is required for Universal Link and click tracking functionality.
1. `"$original_url":"{{your web url URI encoded}}"` For each piece of content, include a URI encoded version of your content's web URL. You can also add deep link data as query parameters on that web URL. This ensures accurate Content Analytics reporting.
   **Example:** `"$original_url":"https%3A%2F%2Fshop.com%2Fshoes%2Fbrown-shoes%3Fmy_key%3Dmy_value%26campaign%3Dshoe_discounts"`

#### Convert all web links in your email to deep links

We have provided a way of easily converting web links to Branch links, as well as [an example](https://gist.github.com/derrickstaten/f9b1e72e506f79628ab9127dd114dd83#file-sendgrid-demo-js). The example takes an html email (as a string) and applies the script to it.

Here is the script:

```javascript
var crypto = require('crypto');
module.exports = function(original_url, branch_base_url) {
    if (!original_url) { return new Error('Missing original_url'); }
    if (typeof original_url != 'string') { return new Error('Invalid original_url'); }
    if (!branch_base_url) { return new Error('Missing branch_base_url, should be similar to https://bnc.lt/abcd/3p?%243p=e_xx'); }
    if (typeof branch_base_url != 'string') { return new Error('Invalid branch_base_url'); }

    return branch_base_url + '&%24original_url=' + encodeURIComponent(original_url);
};
```

Here is how links look before and after (the latter being a Branch deep link).

1. *Before:* http://example.com/?foo=bar
2. *After:* https://vza3.app.link/3p?%243p=e_xx&%24original_url=http%3A%2F%2Fexample.com%2F%3Ffoo%3Dbar

**Note** that these are simplified examples, not actual demo links.


### Handle links for web-only content

In some cases you may have content on web that isn’t in the app - for example, a temporary Mother’s Day promotion or an unsubscribe button. You can designate links to only open on web if you use the Responsys Link Table feature. There are three URL fields in the link table when creating a new link: `LINK_URL`, `IOS_LINK_URL`, and `ANDROID_LINK_URL`. If you only enter the link in the `LINK_URL` field, the path of the final click-wrapped url will begin with `/pub/cc`.  However, if you also input the same link in `IOS_LINK_URL`, then the path of the final click-wrapped url will begin with `pub/acc`. You should set up your AASA file to whitelist only the path `/pub/acc*` in order to not launch the app from web-only links.

![image](/_assets/img/pages/email/responsys/branch_responsys_webonly.png)

![image](/_assets/img/pages/email/responsys/branch_responsys_deeplink.png)

## Support

### Styling
If you include style tags within your `<a>` tags, you’ll need to separate those out into a separate div inside the `<@deeplink>` tag. If you use tracked links with `<a>` tags, those will work fine.

Style Tags within your anchor tags like so:

**Before:**

```
<a href="https://branch.io/" style="color:#000001; text-decoration:none;">Branch Website</a>
```

**After:**

```
<@deeplink "https://branch.io/"><div style="color:#000001; text-decoration:none;">Branch Website</div></@deeplink>
```

### Launch failed error
You’ll see this error if you haven’t included the `<#import >` snippet in your template.

```obj-c
Launch Failed: Launch failed: Template /contentlibrary/branch test campaign/My Default Template.htm caused an execution error: on line 183, column 92 in cms://contentlibrary/branch test campaign/Content.htm: deeplink is not a user-defined directive. It is a freemarker.template.SimpleScalar
```

### Using dynamic data from profile extension tables

The `<@deeplink >` and `<@tracked_deeplink />` tags even work with dynamic links injected via RPL.
```
<@deeplink "${latestProduct.url}">${latestProduct.name}</@deeplink>
```

Curious about how email works and more FAQ? **Visit our [Universal Email Overview](/emails/universal-email/) page**.
