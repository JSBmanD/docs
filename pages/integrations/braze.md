---
title: Braze
---
## Overview

The Branch partnership with [Braze](https://www.braze.com) provides a way to deliver Branch installs and attributions to your Braze dashboard. This allows you to analyze your users coming in from Branch deep linked campaigns.

### How it works

We have built a custom integration to automatically send all Branch install data to Braze.

!!! protip "How do we differentiate Braze and Branch installs?"
    We rely on a Branch link being clicked, which leads to an install. This sets an internal boolean that an install came from Branch.

## Setup

### Prerequisites

- This guide requires you to have already integrated the Branch mobile SDKs into your app.
- You also need to [sign up for a Braze account](https://dashboard.braze.com/developers/sign_up) and [install the Braze SDK](https://documentation.braze.com/).
- Ensure Braze's iOS SDK is [collecting the IDFA](https://documentation.braze.com/iOS/#optional-idfa-collection).
- Make sure to follow the steps in Braze's [documentation here](https://www.braze.com/documentation/Partner_Integrations/#branch).

### Get the Braze API key

1. On the Braze dashboard, navigate to the **App Settings** section, and click **3rd Party Integrations**.
1. From there, grab your API key (this will be the same for all attribution partners listed on the page).


### Configure the Branch Dashboard

### Enable Data Feeds

Data Integrations are included as part of the Data Feeds product. For more information on Data Feeds, and how to enable it, please read the [Data Feeds summary](/exports/data-feeds/).

### Select the integration

1. Navigate to [Data Integrations](https://dashboard.branch.io/data-import-export/data-feeds/integrations) within Data Feeds.
1. Find the integration you need by typing in the search box.

    ![Ads Partner Management](/_assets/img/ingredients/data-integrations/search-for-integration.png)

    !!! note "We've upgraded our Data Integrations!"
 		    We've upgraded our Data Integrations to use people-based attribution. If you see the below screen instead of the screenshot above, please click <notranslate>"Preview Now"</notranslate> to upgrade to our updated integrations. We will be deprecating our legacy integrations in 2018.

        ![Ads Partner Management](/_assets/img/ingredients/data-integrations/legacy-data-integrations.png)

1. On the Branch Dashboard (dashboard.branch.io), navigate to the [Integrations page](https://dashboard.branch.io/integrations).
1. Search for Braze and click on the tile.
1. Enter your Braze API Key and hit <notranslate>**Enable**</notranslate>.

    ![image]( /_assets/img/pages/integrations/braze/braze_di.png)

!!! warning "Please test integration!"
    Branch is not responsible for inaccurate API keys.


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
