---
title: Salesforce v1
---
## Overview

![Salesforce v1](https://cdn.branch.io/branch-assets/email-providers//salesforce-1555435733478.png)

This guide will walk you through how to setup your email campaigns with **[Salesforce v1](https://www.salesforce.com/products/marketing-cloud/overview/){:target="\_blank"}** using Branch Universal Email to automatically convert your email links into **multi-platform deep links**

The basic integration involves four parts:

1. [Activate integration and setup link behavior](#activate-integration)
1. [Configure your mobile app](#configure-your-mobile-app)
1. [Configure your ESP](#configure-your-esp)
1. [Updating the links in your email](#using-universal-email)

Universal Email allows you to automatically convert your email links into multi-platform deep links that take users directly to content in the app on mobile devices, while still maintaining the same web experience for desktop and mobile users without the app.

When a link is clicked by a user without the app, it will route that user to the original web URL (including on desktop). When a link is clicked by a user with your app, it will direct that user into the relevant in-app content regardless of platform or email client.

## Setup

[block:callout]
{
  "type": "tip",
  "title": "SFMC Pre-requisite",
  "body": "You must have the <notranslate>**[Salesforce Marketing Cloud Sender Authentication Package (SAP)](https://help.salesforce.com/articleView?id=mc_es_sender_authentication_package.htm&type=5){:target="\_blank"}**</notranslate> in order to benefit from Universal Links + click tracking functionality."
}
[/block]

### Prerequisites

This guide requires you to have already [integrated the Branch SDK](/apps/ios/) into your app.

To open the app directly on iOS 9.2+, you must configure your email integration and your app to support [Universal Links](/deep-linking/universal-links/) in emails.

Contact your Branch Account Manager or [accounts@branch.io](mailto:accounts@branch.io) at any time for assistance with the setup steps.

## Activate integration

### Choose your email service provider

Navigate to the [Universal Email](https://dashboard.branch.io/email){:target="\_blank"} section of the Branch dashboard. Select <notranslate>**Salesforce**</notranslate> and click <notranslate>**Enable**</notranslate>.

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

[block:callout]
{
  "type": "info",
  "title": "Host deep link data for more than just emails",
  "body": "The Branch [Quick Link creator](/getting-started/creating-links/dashboard/) also scrapes your web URL for deep link data to make link creation even easier. [Hosting Deep Link Data](/getting-started/hosted-deep-link-data/guide/) on your website will make using Branch products easier in future."
}
[/block]

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
Open to default redirects | Route to defaults specified in [Link Settings](https://dashboard.branch.io/link-settings).

### Tell us your click tracking domain

You can retrieve your click tracking domain from your Salesforce settings. If you have not added a custom click tracking domain yet, follow the instructions [here](#setup-a-custom-click-tracking-domain).

![image](/_assets/img/pages/email/salesforce/setup-config.png)

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

[block:callout]
{
  "type": "info",
  "title": "How does it work?",
  "body": "Apple recognizes the click tracking domain as a Universal Link, and opens the app immediately without the browser opening. Once the app has opened, Branch will collect the referring URL that opened the app (at this time, it will be the click tracking url). Inside the app, Branch will robotically “click” the link, registering the click with the ESP, and returning the Branch link information to the Branch SDK inside the app. This information is then used to deep link the user to the correct in-app content. See the [Support](#support) section for more information."
}
[/block]


### Add your click tracking domain to your Associated Domains

To enable Universal Links on your click tracking domain, you'll need to add the click tracking domain to your Associated Domains entitlement.

1. In Xcode, go to the `Capabilities` tab of your project file.
1. Scroll down and enable <notranslate>**Associated Domains**</notranslate> if it is not already enabled.

    ![image](/_assets/img/pages/email/enable-associated-domains.png)

1. Copy your click tracking domain from the [email you received from Branch](#configure-your-app-for-your-click-tracking-domain), or retrieve it from your ESP's settings.
1. In the `Domains` section, click the `+` icon and add your click tracking domain. For example, if your click tracking domain is `email.example.com`, add an entry for `applinks:email.example.com`.

    ![image](/_assets/img/pages/email/add-domain.png)

[block:callout]
{
  "type": "info",
  "title": "Having trouble or new to Universal Links?",
  "body": "Follow [these instructions](/deep-linking/universal-links/) for more details on enabling Universal Links in the Branch dashboard and in Xcode."
}
[/block]

### Return YES to continueUserActivity

When users enter your app via a Universal Link, we check to see to see if the link URL contains `app.link`. If so, `handledByBranch` will return `YES`. If not, `handledByBranch` will return `NO`. This allows us to explicitly confirm the incoming link is from Branch without making a server call.

For most implementations this will never be an issue, since your deep links will be routed correctly either way. However, if you use a custom link domain *and* you rely on `handledByBranch` to return `YES` for every incoming Branch-generated Universal Link, you can inform the Branch SDK by following these steps:

1. In your <notranslate>**Info.plist**</notranslate> file, create a new key called `branch_universal_link_domains`.
1. Add your custom domain(s) as a string. ![image](/_assets/img/pages/deep-linking/universal-links/branch-universal-link-domain.png)
1. Save the file.

[block:callout]
{
  "type": "tip",
  "title": "Multiple custom domains",
  "body": "If you have an unusual situation with multiple custom link domains, you may also configure `branch_universal_link_domains` as an array of strings. ![image](/_assets/img/pages/deep-linking/universal-links/branch-universal-link-domains.png)"
}
[/block]

## Configure your ESP

### Setup a custom click tracking domain

You can retrieve your click tracking domain from your Salesforce settings. We **highly** recommend using a new click tracking domain for this implementation to ensure that the user experience for pre-Branch links on the original click tracking domain doesn't break.

[block:callout]
{
  "type": "tip",
  "title": "Adding a custom click-tracking domain",
  "body": "If you need help with setting up a custom click-tracking domain - please ask your account manager or request support at Salesforce."
}
[/block]

#### Configure your AASA file in Salesforce Marketing Cloud

Your Salesforce account must be configured to correctly handle Universal Links. Configure the settings in Deep Linking under the Send Management section in Email Studio. Ensure you're in the account corresponding to the correct click tracking domain [you selected](#tell-us-your-click-tracking-domain) above.

![image](https://cdn.branch.io/branch-assets/1559434914239-og_image.png)

1. Enter the AppID value
1. Check the "Exclude Profile" and <notranslate>"Unsub Center"</notranslate> checkboxes to force links to these items to open in the browser and not the app, if desired.
1. Click <notranslate>"Save"</notranslate> to save the configuration.
1. Let Salesforce and Branch know that you've finished this step and your Technical Account Manager will verify that everything looks good.

![image](/_assets/img/pages/email/salesforce/salesforce-aasa-form.png)

## Using Universal email

## Using Universal email

Once you’ve completed the [one time setup steps](#setup), it’s time to send your first email.

This guide will identify which web links you'd like to open the app and deep link, as well as convert them to Branch links.

### Options for generating Branch links for email

There are a few different ways you can create Branch links that are compatible with Universal Email + Salesforce. You will need to replace the web URLs in your templates with these. To create Branch links, you can either:

1. [Use Salesforce AMPscript to convert links](#add-a-new-content-area-for-easy-deep-linking)
1. [Making regular Branch links compatible with email](#making-regular-branch-links-compatible-with-email)
1. [Create email links via API without changing your email templates](#create-email-links-via-api-without-changing-your-email-templates)
1. [Convert all web links in your email to deep links](#convert-all-web-links-in-your-email-to-deep-links)

#### Add a new Content Area for easy deep linking

Using Salesforce's AMPscript, we'll add a new Content Area in Salesforce that converts web links in your email templates into Branch links.

1. Work with your Branch account manager to modify the following Salesforce AMPscript snippet, replacing `DOMAIN-HERE` with your Branch base domain (i.e., example.app.link):

    ```
    %%[ VAR @deeplink, @branch_base_url SET @branch_base_url = "https://DOMAIN-HERE/3p?%243p=e_et" SET @deeplink = CONCAT(@branch_base_url, CONCAT("&%24original_url=", URLEncode(@link_to_be_wrapped, 1, 1))) ]%%
    ```

1. After logging into Salesforce Marketing Cloud, click on <notranslate>**Email Studio**</notranslate> and then a sub-menu will appear. Click on <notranslate>**Email**</notranslate> in the dropdown menu:

    ![image](/_assets/img/pages/email/salesforce/salesforce-dropdown.png)

1. This will take you to the landing page for the Email section. Click on <notranslate>**Content**</notranslate> in the menu bar to navigate to the Content section:

    ![image](/_assets/img/pages/email/salesforce/salesforce-menu-bar.png)

1. In the Content section, you will see a list of folders on the left side. Right click on the <notranslate>**My Contents**</notranslate> folder and choose <notranslate>**New Folder**</notranslate> in the context menu:

    ![image](/_assets/img/pages/email/salesforce/salesforce-folders.png)

1. Name the folder `Branch`:

    ![image](/_assets/img/pages/email/salesforce/salesforce-name-folder.png)

1. Once the folder is created, click on the <notranslate>**Branch**</notranslate> folder. On the right side, you will see a menu bar for the Branch folder. Click on <notranslate>**Create**</notranslate> and in the sub menu, click <notranslate>**Content**</notranslate> to create new content:

    ![image](/_assets/img/pages/email/salesforce/salesforce-new-content.png)

1. In the Create Content window that appears, enter `deeplink` in the text field named Content Name. Click on <notranslate>**Next**</notranslate> after you enter the text:

    ![image](/_assets/img/pages/email/salesforce/salesforce-deeplink.png)

1. The next screen will ask you to select the format of the content. Choose <notranslate>**Free Form**</notranslate> and then click <notranslate>**Next**</notranslate>:

    ![image](/_assets/img/pages/email/salesforce/salesforce-format.png)

1. In the next screen, paste in the snippet you generated in <notranslate>**1**</notranslate>:

    ![image](/_assets/img/pages/email/salesforce/salesforce-snippet.png)

1. Click <notranslate>**Save**</notranslate>. You will now be back at your list of folders in the Content section with the file <notranslate>**deeplink**</notranslate> listed:

    ![image](/_assets/img/pages/email/salesforce/salesforce-saved.png)

You have now successfully created the deep linking AMPscript.

[block:callout]
{
  "type": "info",
  "title": "Code snippet",
  "body": "
  The snippet will follow this format:
  ```
  %%[ VAR @deeplink, @branch_base_url SET @branch_base_url = "BASE URL FROM BRANCH" SET @deeplink = CONCAT(@branch_base_url, CONCAT("&%24original_url=", URLEncode(@link_to_be_wrapped, 1, 1))) ]%%
  ```
  The code above has a placeholder for `@branch_base_url`. Replace it with yours."
}
[/block]

##### Configure your Salesforce email templates

This section covers how to convert individual links in your existing email templates into Branch deep links.  You will need to do this for all links in your email template that you want to convert to Branch deep links.

For example, if you decide to convert the link below into a Branch Link:
```
<a href="https://www.blueapron.com/"> I want it! </a>
```

This is what the link will look like in the email template, <notranslate>**after**</notranslate> you added the AMPscript to convert it into a Branch link:
```
%%[ SET @link_to_be_wrapped = "https://www.blueapron.com/" ContentAreaByName("My Contents\deeplink") ]%%
<a href="%%=RedirectTo(@deeplink)=%%">I want it!</a>
```

The process to convert links into Branch links using AMPscript is as follows (this flow converts the links in a separate document, and then pastes them back into your final template):

1. Log in to Salesforce Marketing Cloud
2. Click on <notranslate>**Email Studio**</notranslate> and then a sub-menu will appear. Click on <notranslate>**Email**</notranslate> in the dropdown menu:

    ![image](/_assets/img/pages/email/salesforce/salesforce-dropdown.png)

1. This will take you to the landing page for the Email section. Click on <notranslate>**Content**</notranslate> in the menu bar to navigate to the Content section:

    ![image](/_assets/img/pages/email/salesforce/salesforce-menu-bar.png)

1. Navigate to your folder containing your emails and open an existing email. Make sure the email is in HTML layout as shown below:

    ![image](/_assets/img/pages/email/salesforce/salesforce-email-html.png)

1. Choose a link that you want to convert to a Branch deep link. Copy the text right after the `href=` in your email template, and paste it into a separate document. In the example, it is:

    **`"https://www.blueapron.com/"`**

1. Add `%%[ SET @link_to_be_wrapped = ` before the link in your separate document. In the example, this is now:

    **`%%[ SET @link_to_be_wrapped = `**`"https://www.blueapron.com/"`

1. Add `ContentAreaByName("My Contents\deeplink")]%%` after the link:

    `%%[ SET @link_to_be_wrapped = "https://www.blueapron.com/"`**`ContentAreaByName("My Contents\deeplink")]%%`**

1. From the original link in your template, copy the text from and including `<a` until the `href=`.  Add it to the text after `%%` in the last step. Please include the `<a` but not the `href=`:

    `%%[ SET @link_to_be_wrapped = "https://www.blueapron.com/" ContentAreaByName("My Contents\deeplink") ]%%`**`<a style="_any css can be added here_"`**

1. Add `href="%%=RedirectTo(@deeplink)=%%"` to the end:

    `%%[ SET @link_to_be_wrapped = "https://www.blueapron.com/" ContentAreaByName("My Contents\deeplink") ]%% <a style="_any css can be added here_"`**`href="%%=RedirectTo(@deeplink)=%%"`**

1. From the original link in your template, copy the end of the tag, the link text, and the closing tag (`>I want it!</a>` in the example) and add it to the end:

    `%%[ SET @link_to_be_wrapped = "https://www.blueapron.com/" ContentAreaByName("My Contents\deeplink") ]%% <a style="_any css can be added here_" href="%%=RedirectTo(@deeplink)=%%"`**`>I want it!</a>`**

1. Copy your final result from the separate document back into your email template, replacing everything inside and including the `<a></a>` tags in the template.

1. Repeat this for all your links in your email template that you want to convert to Branch deep links.

[block:callout]
{
  "type": "info",
  "title": "Link Conversion Summary",
  "body": "
  Wherever you use `<a>` tags in your email templates, replace those with AMPscript to convert the web URLs into Branch links.  The AMPscript references the [Content Area](#add-a-new-content-area-for-easy-deep-linking) setup earlier.
  ```
  %%[SET @link_to_be_wrapped = "ADD YOUR LINK HERE" ContentAreaByName("My Contents\deeplink")]%%
  <a href="%%=RedirectTo(@deeplink)=%%">Click Me</a>
  ```
  For example, **before:**
  `<a href="https://branch.io/product/1234">Example link</a>`
  **After:**
  `%%[ SET @link_to_be_wrapped = "https://branch.io/product/1234" ContentAreaByName("My Contents\deeplink") ]%%`
  `<a href="%%=RedirectTo(@deeplink)=%%">Example link</a>`
  "
}
[/block]

[block:callout]
{
  "type": "warning",
  "title": "Content Area folder",
  "body": "Make sure your `deeplink` Content Area [is in the right folder](#add-a-new-content-area-for-easy-deep-linking). Either change the folder to "My Contents" or change the path used by "ContentAreaByName" in the Branch script."
}
[/block]

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


### Flag your web-only links

For links that should always open in web, even if the app is installed, add Salesforce's link attribute ```mc-deep-link="false"``` to your link tag to ensure the app does not open in iOS:

```html
<a mc-deep-link="false" href="https://my.app.link/3p?$3p=e_et&$original_url=..." >This link will not open the app.</a>
```

If the link in the "href" part of the tag is a normal web link, the app will NOT open in Android.  If the link in the <notranslate>"href"</notranslate> part of the tag is a Branch link, but you don't want the app to open, then you'll need to add `&%24web_only%3Dtrue` as a query parameter:

```html
<a href="https://my.app.link/3p?%243p=e_xx&%24original_url=http%3A%2F%2Fexample.com&%24web_only%3Dtrue" >Link to your app!</a>
```

## Support

Curious about how email works and more FAQ? **Visit our [Universal Email Overview](/emails/universal-email/) page**.
