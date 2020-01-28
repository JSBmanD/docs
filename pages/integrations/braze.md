---
title: Braze
---
## Overview

The Branch partnership with [Braze](https://www.braze.com) provides a way to deliver Branch installs and attributions to your Braze dashboard. This allows you to analyze your users coming in from Branch deep linked campaigns.

### How it works

We have built a custom integration to automatically send all Branch install data to Braze.

[block:callout]
{
  "type": "info",
  "title": "How do we differentiate Braze and Branch installs?",
  "body": "We rely on a Branch link being clicked, which leads to an install. This sets an internal boolean that an install came from Branch."
}
[/block]

## Setup

### Prerequisites

- This guide requires you to have already integrated the Branch mobile SDKs into your app.
- You also need to [sign up for a Braze account](https://dashboard.braze.com/developers/sign_up) and [install the Braze SDK](https://documentation.braze.com/).
- Ensure Braze's iOS SDK is [collecting the IDFA](https://documentation.braze.com/iOS/#optional-idfa-collection).
- Make sure to follow the steps in Braze's [documentation here](https://www.braze.com/documentation/Partner_Integrations/#branch).

### Get the Braze API key

1. On the Braze dashboard, navigate to the **App Settings** section, and click **3rd Party Integrations**.
1. From there, grab your API key (this will be the same for all attribution partners listed on the page).

### Enable the integration

1. Visit the [Data Integration](https://branch.dashboard.branch.io/data-import-export/data-feeds/integrations) on the Branch dashboard.
2. Search for your <notranslate>**Data Integration Partner**</notranslate>.
3. Select your <notranslate>**Data Integration Partner**</notranslate>.
4. Provide the required details:
    1. **API Key**
    2. **Endpoint Default (rest.iad-01.braze.com)**
        1. Do not include `http://` or `https://` as Branch adds the protocol on the backend.
        2. Do not add `/attribution/branch` at the end of your endpoint as Branch adds it on the backend.
        3. The default Braze endpoint is `rest.iad-01.braze.com`; if you wish to use a different endpoint, please  refer to [Braze's documentation](https://www.braze.com/docs/api/basics?redirected=true#endpoints).
5. Click <notranslate>**Enable**</notranslate>.

![image](/_assets/img/pages/integrations/braze/braze-di.png)

### Pass Braze Android Install Tracking ID

When you're ready to send data through Branch, you'll need to make sure to pass through the Braze Android Install Tracking ID to the Branch SDKs. In order to do so, retrieve the ID from the Braze SDK and pass this value through `setRequestMetadataKey` on the Branch SDKs.

Here's a sample snippet showing this. **NOTE** This is only required for Android. You must set the correct key before calling <notranslate>*initSession*</notranslate>. You must also initialize the Braze SDK before setting the request metadata in the Branch SDK.


**Android**

Before you initialize in your Application#onCreate or Deep Link Activity's #onCreate.

```java

Branch.getInstance().setRequestMetadata("$braze_install_id", Appboy.getInstance(this).getInstallTrackingId());

...

Branch.initSession(...);
```

In the above snippet, `this` is the Activity context.


## Advanced

### What Branch sends to Braze

Branch Analytics Tag | Braze Data Placeholder Tag
--- | ---
<notranslate>Campaign</notranslate> | `campaign`
<notranslate>Channel</notranslate> | `source`
<notranslate>Adgroup</notranslate> | `adgroup`
<notranslate>Ad</notranslate> | `ad`

### Braze Endpoints.

By default, Branch uses the new Braze endpoint https://rest.iad-01.braze.com. If your Braze app is using a different Braze endpoint please contact your Branch account manager or reach out to us at [integrations@branch.io](mailto:integrations@branch.io). If you are not sure what endpoint your app uses please open a support ticket with Braze or use the [Braze REST Endpoint table](https://www.braze.com/documentation/REST_API/#endpoints) to find your correct REST endpoint.
