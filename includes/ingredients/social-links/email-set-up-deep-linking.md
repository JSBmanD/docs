Contact your Branch Account Manager or [accounts@branch.io](mailto:accounts@branch.io) at any time for assistance with the setup steps.

### Choose your email service provider

Navigate to the [Universal Email](https://dashboard.branch.io/email){:target="\_blank"} section of the Branch dashboard. Select {{page.title}} as your email service provider and click <notranslate>**Get Started**</notranslate>.

![image](/_assets/img/pages/email/choose-esp.png)

### Set up deep linking for email

#### Email link behavior

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

If you chose **not** to set up deep linking to specific content within your app, then you can [skip this step](#configure-your-esp).

![image](/_assets/img/pages/email/responsys/enter-web-url.png)

In this step, you will want to enter a web URL that corresponds to a specific screen within your app. In other words, the webpage should have content that also exists in your app. If you do not know whether your web content also exists in-app, try any URL other than your website homepage. Some examples:

- A product page, like a page with brown loafers
- An article
- A content page, like a video or image

Once you choose one and click <notranslate>**Submit**</notranslate>, [meta tags that can be used for deep linking](/web/hosted-data/) will be retrieved from your webpage. You will see a result indicating the mapping between your web content and your app content. For a full explanation of the tests run on this page and the possible results, check out the [support section](#deep-linking-setup-messages).

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


In the meantime, you can proceed to the next step: <notranslate>**[Configure ESP](#configure-your-esp)**</notranslate>.

#### Deep linking settings for email

The following are all the possible settings you can configure for deep linking with email.

##### Link Behavior

| Setting | Example | Link Data Result
| --- | --- | ---
| <notranslate>**Open the app homepage**</notranslate> | No settings configured to generate deep link data for email; email links will route to the app homepage. |
| <notranslate>**Open to specific app content**</notranslate> | Deep link to specific app content based on one or more of the following settings. |
| Translate query parameters on URLs into Branch link data | <notranslate>**URL:**</notranslate> `https://shop.com/shoes/brown-loafers&product_id=123456` | `product_id: 123456`
| Translate web URL into Branch link data: <br> Full URL for key ______ | <notranslate>**URL:**</notranslate> `https://shop.com/shoes/brown-loafers` <br> <notranslate>**Key:**</notranslate> `$canonical_url` | `$canonical_url: https://shop.com/shoes/brown-loafers`
| Translate web URL into Branch link data: <br> URL path for key ______ | <notranslate>**URL:**</notranslate> `https://shop.com/shoes/brown-loafers` <br> <notranslate>**Key:**</notranslate> `$deeplink_path` | `$deeplink_path: shoes/brown-loafers`
| Retrieve hosted deep link data from website and translate into Branch link data | <notranslate>**URL:**</notranslate> `https://shop.com/shoes/brown-loafers` <br> <notranslate>**Meta Tags:**</notranslate> `<meta name="branch:deeplink:product_id" content="123456" />` | `product_id: 123456`
| Strip protocol (http:// or https://): <br> from $deeplink_path <br> from $ios_deeplink_path <br> from $android_deeplink_path <br> *Note: Typically used with one of the other settings.* | <notranslate>**URL:**</notranslate> `https://shop.com/shoes/brown-loafers` <br> <notranslate>**Other Settings:**</notranslate> Translate web URL into Branch link data: Full URL for key `$deeplink_path` | `$deeplink_path: shop.com/shoes/brown-loafers`
| Translate query parameters on URLs into Branch link data from parameter ______ to key ______ <br> *Note: Not configurable in the UI. [Contact support](https://support.branch.io/support/tickets/new){:target="_blank"} to use this setting.* | <notranslate>**URL:**</notranslate> `https://shop.com/shoes/brown-loafers&product_id=123456&utm_content=shoes` <br> <notranslate>**Parameter:**</notranslate> `utm_content` <br> <notranslate>**Key:**</notranslate> `category` | `category: shoes`

##### Link behavior for users without your app

| Setting | Description
| --- | ---
| Open to specific web content | Route to the original URL specified in the email.
| Open to default redirects | Route to defaults specified in [Link Settings](https://dashboard.branch.io/link-settings){:target="_blank"}.

### Configure your ESP

To open the app directly on iOS 9.2+, you must configure your {{ page.title }} integration to support [Universal Links](/getting-started/universal-app-links/), and configure your app to support {{page.title}} + Universal Links.

#### Tell us your click tracking domain
