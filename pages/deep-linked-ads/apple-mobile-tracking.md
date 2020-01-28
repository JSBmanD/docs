---
title: Apple Search Ads
---
## Overview

![Apple Search Ads](/_assets/img/pages/deep-linked-ads/apple-search/search-ads-reduced-logo.png)

Branch can help track your **[Apple Search Ads](https://searchads.apple.com/)** campaigns by fetching the Apple Search Ads Attribution API.  You can then use the parameters you've set in the Apple Search Ads dashboard, parameters such as the campaign name, and take special action in your app after an install, or simply track the effectiveness of a campaign in the Branch dashboard, along with other your other Branch statistics, such as total installs, referrals, and app link statistics.

+ [Apple Search Ads](https://searchads.apple.com/)
+ [Apple Search Ads WWDC](https://developer.apple.com/videos/play/wwdc2016/302/)

## SDK Setup

In order to check if the user came from an Apple Search Ads, you must make the attribution call before Branch initializes. As a warning, Apple's Search Ads Attribution API may take more than 1 second round trip. This means that your call to Branch's initSession to the execution of the callback block may be delayed by this additional 1 second.

[block:callout]
{
  "type": "info",
  "title": "React Native Support",
  "body": "If you are using React Native in your app, please make sure to follow the [Track Apple Search Ads](/apps/react-native/#track-apple-search-ads) section of the React Native integration in addition to the below."
}
[/block]

### Import iAd and AdSupport

You must add Apple's <notranslate>**iAd.framework**</notranslate> and <notranslate>**AdSupport.framework**</notranslate> to your <notranslate>**Linked Frameworks**</notranslate> in your Xcode project to enable Apple Search Ads checking.

![image](/_assets/img/pages/apps/ios-frameworks.png)

[block:callout]
{
  "type": "warning",
  "title": "Using Cocoapods",
  "body": "If using Cocoapods, the iAd framework is automatically added (in build phase) and the headers are imported. If not using Cocoapods, you will need to do this manually."
}
[/block]

#### Enable Apple Search Ads Check

[block:callout]
{
  "type": "info",
  "title": "Branch iOS SDK v0.30.0",
  "body": "As of v0.30.0, the Branch iOS SDK supports new logic that increases wait time for Apple Search Ads to respond with the payload, as well as ignore Apple's test data."
}
[/block]

To enable this check, add a `delayInitToCheckForSearchAds` call to your <notranslate>**AppDelegate.m**</notranslate> (or <notranslate>**AppDelegate.swift**</notranslate>) file after you create the Branch singleton, but *before* you call `initSession`. Your code will end up looking something like this:

**Objective-C**

```obj-c
Branch *branch = [Branch getInstance];

// This will usually add less than 1 second on first time startup.  Up to 3.5 seconds if Apple Search Ads fails to respond.
[branch delayInitToCheckForSearchAds];

// Increases the amount of time the SDK waits for Apple Search Ads to respond. The default wait has a better than 90% success rate, however waiting longer can improve the success rate. This will increase the usual delay to about 3 seconds on first time startup.  Up to about 15 seconds if Apple Search Ads fails to respond.
[branch useLongerWaitForAppleSearchAds];

// Branch won't callback with Apple's test data, this is still sent to the server.
[branch ignoreAppleSearchAdsTestData];

[branch initSessionWithLaunchOptions:launchOptions andRegisterDeepLinkHandler:^(NSDictionary *params, NSError *error) {
    // handle payload
    }];
```
**Swift**

```swift
let branch = Branch.getInstance()

// This will usually add less than 1 second on first time startup.  Up to 3.5 seconds if Apple Search Ads fails to respond.
branch.delayInitToCheckForSearchAds()

// Increases the amount of time the SDK waits for Apple Search Ads to respond. The default wait has a better than 90% success rate, however waiting longer can improve the success rate. This will increase the usual delay to about 3 seconds on first time startup.  Up to about 15 seconds if Apple Search Ads fails to respond.
branch.useLongerWaitForAppleSearchAds()

// Branch won't callback with Apple's test data, this is still sent to the server.
branch.ignoreAppleSearchAdsTestData()
branch.initSession(launchOptions: launchOptions, andRegisterDeepLinkHandler: { (params, error) in
    // handle payload
    })
```

If you're concerned about the additional 1 second latency, the call to `delayInitToCheckForSearchAds` can be called conditionally at run time. So, if you want to only check on first install, or the like, then just don't call this method.

[block:callout]
{
  "type": "warning",
  "title": "Testing Apple Search Ads",
  "body": "If you test using a non-production app and do not use the `ignoreAppleSearchAdsTestData()` method, the iAd framework will return fake Apple Search Ads payloads to simulate the install being claimed by Apple Search Ads. Subsequently, you will see these claims in your reporting."
}
[/block]

[block:callout]
{
  "type": "warning",
  "title": "Impact on Deferred Deep Linking",
  "body": "If you use deferred deep linking, do not use the `useLongerWaitForAppleSearchAds()` method as it will negatively impact the end user's experience by creating longer wait times for the deferred deep linking to occur."
}
[/block]

## Server to Server Setup

If you have a S2S integration with Branch (i.e. you do not use the Branch SDK to send Branch data), you will need to perform the Apple Search Ads check yourself before sending the returned payload to Branch.

Please refer to Apple Search Ads developer documentation on how to [make requests to their API](https://developer.apple.com/documentation/iad/setting_up_apple_search_ads_attribution).

### Implementation Guidelines

- Give a 2 second buffer before calling Apple's Attribution API. If your request times out after 5 seconds, please retry.
- Implement retry logic if response returns as False or Error Code [0,2,3]. Call Apple again 2 seconds later.
- After 20 seconds or successful response, call Branch with the returned Apple Search Ads payload.

## Cost Data Setup

1. Navigate to the [Apple Search Ads UI > Settings > API](https://app.searchads.apple.com/cm/app/settings/apicertificates). *Verify you have selected the correct account by using the account selector in the top right hand corner.*

    ![image](/_assets/img/pages/deep-linked-ads/apple-search/apple-api-screen.png)

1. Create an API certificate

    ![image](/_assets/img/pages/deep-linked-ads/apple-search/apple-search-api.png)

1. Download the API certificate to your computer. You'll unzip the folder and get one `.key` and one `.pem` file.

    ![image](/_assets/img/pages/deep-linked-ads/apple-search/apple-download-certs.png)

1. Navigate to the [Apple Search Ads partner manager](https://dashboard.branch.io/ads/partner-management/a_apple?tab=settings) in the Branch dashboard.
1. Upload the certificates there, selecting each file, and then clicking the blue upload arrow to upload the files. Click *Next* to continue.

    ![image](/_assets/img/pages/deep-linked-ads/apple-search/apple-upload-certs.png)

1. Select the organizations for which you would like to ingest data and click *Save* to enable Apple Search Ads with Cost Data.

### Cost Data

Branch provides the following cost metrics for this ad partner:

Analytics Tag | Description | Used for
--- | --- | ---
Cost| Total cost (spend) for those dimensions (analytics tags, user data, time range), regardless of cost model | Understanding the total amount spent
<notranslate>eCPI</notranslate> | cost / installs | Normalizing spend per install, to understand the average price of an install across networks or over time
<notranslate>eCPC</notranslate> | cost / clicks | Normalizing spend per click, to understand the average price of an click across networks or over time
<notranslate>eCPM</notranslate> | cost / (impressions / 1000) | Normalizing spend per thousand impressions, to understand the average price of 1000 impressions across networks or over time
<notranslate>eCPA</notranslate> | cost / purchases [includes web and app purchases] | Normalizing spend per purchase, to understand the average price of a purchase across networks or over time
<notranslate>Return On Investment (ROI)</notranslate> | (revenue-cost / cost) * 100 | Deriving return on investment, to understand the percentage "profit" made on ad spend
<notranslate>Return On Ad Spend (ROAS)</notranslate> | (revenue / cost) * 100 | Deriving return on investment by understanding the percentage revenue multiple for a given unit of spend

[block:callout]
{
  "type": "info",
  "title": "Cost Data Translation",
  "body": "All cost data is ingested in local currency and then translated to USD on the dashboard using the exchange rate for that currency on the day the data is stored.  In effect, this means the dashboard shows the amount that campaign cost converted to USD at the time it ran."
}
[/block]

### Cost Data Support

#### <notranslate>"Next"</notranslate> button not clickable

Please ensure you've both selected the correct files *and* pressed the blue upload arrows to complete your upload.

#### Cost, click and impression data not appearing

[block:callout]
{
  "type": "info",
  "title": "Available Compare By Dimensions for SANs",
  "body": "Self-Attributing Networks (SANs) do not always support all of the dimensions available in your Branch analytics.  Please refer to the following table when using Compare by dimensions."
}
[/block]

    |                     | <notranslate>**Facebook**</notranslate>    | <notranslate>**Google**</notranslate>      | <notranslate>**Apple Search Ads**</notranslate> | <notranslate>**Snap**</notranslate>        |
    |---------------------|-------------|-------------|------------------|-------------|
    | <notranslate>**Feature**</notranslate>             | Supported   | Supported   | Supported        | Supported   |
    | <notranslate>**Channel**</notranslate>             | Unsupported | Unsupported | Unsupported      | Unsupported |
    | <notranslate>**Campaign**</notranslate>            | Supported   | Supported   | Supported        | Supported   |
    | <notranslate>**Tags**</notranslate>               | Unsupported | Unsupported | Unsupported      | Unsupported |
    | <notranslate>**Stage**</notranslate>               | Unsupported | Unsupported | Unsupported      | Unsupported |
    | <notranslate>**Ad Partner**</notranslate>          | Supported   | Supported   | Supported        | Supported   |
    | <notranslate>**Secondary Publisher**</notranslate> | Supported   | Supported   | Unsupported      | Unsupported |
    | <notranslate>**Ad Set Name**</notranslate>         | Supported   | Unsupported | Supported        | Supported   |
    | <notranslate>**Ad Name**</notranslate>             | Supported   | Unsupported | Unsupported      | Supported   |
    | <notranslate>**Creative Name**</notranslate>       | Supported   | Unsupported | Unsupported      | Unsupported |
    | <notranslate>**Keyword**</notranslate>             | Unsupported | Supported   | Supported        | Unsupported |
    | <notranslate>**Last Touch Type**</notranslate>     | Unsupported | Unsupported | Unsupported      | Unsupported |
    | <notranslate>**Link ID**</notranslate>             | Unsupported | Unsupported | Unsupported      | Unsupported |
    | <notranslate>**Country**</notranslate>             | Supported   | Unsupported | Unsupported      | Unsupported |
    | <notranslate>**OS**</notranslate>                  | Unsupported | Unsupported | Supported        | Unsupported |
    | <notranslate>**Platform**</notranslate>            | Unsupported | Unsupported | Unsupported      | Unsupported |


Verify that you have selected the right certificates:

- *Did you create the certificate for the right accounts?* You can toggle the accounts that you are viewing in the top right hand side of the Apple Search Ads UI.
- *Does your certificate have relevant permissions?* Your certificate must have read-only permissions or higher to retrieve Apple Search Ads data.

Still not working? Try downloading a new certificate and uploading that to Branch.

#### Branch Cost data not matching the Ad Partner dashboard

Please ensure that you've selected the same time zone in your Ad Partner's dashboard and your Branch dashboard.

#### CPI metric doesn't match between Ad Partner and Branch, although cost metric does

Branch's last-click attribution model can lead to differences in install counts for Branch vs self-attributing networks (SANs) that in turn cause differences in CPI metrics. Verify whether your cost and install metrics match the Ad Partner's dashboard. If there is an install discrepancy, it is likely legitimate and due to differences in install counts, where Branch's number is more accurate. If the discrepancy is very large, investigate causes of install discrepancies through the usual troubleshooting steps.

#### Cost, click and impression data is all missing

Generally, reauthenticating a partner and waiting 24 hours will re-enable cost data.

When you reauthenticate, double check that you have selected the correct accounts. We will only pull cost data for accounts that you select as part of the authentication process.

Background:
Cost, click and impression data for SANs are generally sourced from Partner APIs (unless Branch impression pixels or links are being intentionally used for attribution, for example, in web campaigns). When you enable a SAN, you authenticate with your provider. Branch uses this authentication to retrieve click, cost and impression data. If the authentication token expires (for example, if you reset your password, or the partner force resets your token), then you may not see click, impression or cost data. In this case, simply reauthenticate and that will refresh your token.

#### Cost data is missing or incorrect for certain <notranslate>"compare by"</notranslate> breakdowns

Downstream events, such as _installs_, should always have the full range of compare by options in the dashboard. However, _clicks, impressions and cost_ data for SAN are often imported via Partner APIs. These APIs do not necessarily provide the same breakdowns for cost data that Branch supports with raw install events, so there may be cases where the Branch Dashboard cannot compare by the same dimensions for cost data vs install data.


## Adding the Agency Tag to Campaign Name

Only agencies managing advertising campaigns on behalf of a client must prepend their <notranslate>**Agency ID**</notranslate> to the campaign name when creating advertising campaigns for Self-Attributing Networks (SANs).

[block:callout]
{
  "type": "error",
  "title": "Agency ID Required",
  "body": "Failure to append the campaign name with the <notranslate>**Agency ID**</notranslate> will result in any subsequent conversion not being properly attributed to the responsible agency."
}
[/block]

### Finding Your Agency ID

You can find your Agency ID under Account Settings in the [Agency view](/dashboard/agency-view/#managing-your-agency-profile).

### Creating Your Agency Tag

Your agency tag **must** adhere to the following format:

	`agency_{YOUR AGENCY ID HERE}_`


[block:callout]
{
  "type": "info",
  "title": "Example Campaign with Agency tag",
  "body": "`agency_1234567890_My_SAN_Ad_Campaign`"
}
[/block]

	You can append the Agency Tag to either the **beginning** or the **end** of the campaign name.

[block:callout]
{
  "type": "warning",
  "title": "Agency ID Removed When Exporting",
  "body": "The "~campaign" value displayed in exports/analytics will not include the agency_id. If you set up a campaign called `test_campaign_agency_1234` in Facebook, and for any installs that came from that campaign, the "~campaign" value will be "test campaign"."
}
[/block]


## Apple Search Ads Data Mapped to Branch

Branch receives and maps the following parameters from the Apple Search Ads Attribution API:

| Apple Search Ads Parameter | Branch Mapped Field                           |
|----------------------------|-----------------------------------------------|
| `iad-campaign-name`          | `last_attributed_touch_data_tilde_campaign`     |
| `iad-campaign-id`            | `last_attributed_touch_data_tilde_campaign_id`  |
| `iad-adgroup-name`           | `last_attributed_touch_data_tilde_ad_set_name`  |
| `iad-adgroup-id`             | `last_attributed_touch_data_tilde_ad_set_id`    |
| `iad-keyword`                | `last_attributed_touch_data_tilde_keyword`      |

## View Attribution on Dashboard

All the attribution can be visible on the [Branch dashboard summary page](https://dashboard.branch.io/). All installs and opens registered from this channel will automatically be tagged with the `channel`: `Apple App Store` and the `Ad Partner`: `Apple Search Ads`. The `campaign` will be set to the Campaign Name you've configured in the Apple Search Ads dashboard.

- Installs might not be accurate, but installs + open events should match what Apple Search Ads reports.
- Due to API limitations, it may take up to 30 days for full attribution of a device.

Note that these stats are **limited to the date range** at the top of the page. You can expand the range if you'd like.

### Change attribution windows

Attribution windows can be specified at the global account level or on a per link basis with the link level window taking priority. See the below instructions for setup.

#### Account Level Attribution Windows

You can edit your attribution windows under Link Settings > Attribution Windows.

   ![image](/_assets/img/pages/dashboard/people-based-attribution/attribution-windows.png)

Learn more about account level attribution windows in [People-Based Attribution](/dashboard/people-based-attribution/#attribution-windows).

#### Ad Network Attribution Windows

You can edit your attribution windows at the ad network level, if your ad network requires it. This is recommended when you enable networks like Apple Search Ads, Facebook and Google, who may have different windows for installs. With this, you can preserve your Account Level Attribution Windows, as well.

   ![image](/_assets/img/pages/deep-linked-ads/branch-universal-ads/anaw_clear.png)

## Integration Support

### Install discrepancies when compared with Apple Search Ads dashboard

There are a few possible causes of discrepancies with Apple Search Ads. Due to the low customizability of Apple Search Ads' attribution settings, discrepancies are often higher on Apple Search Ads than other platforms, even though performance may be solid and reporting may be working as expected. The best way to attempt reconciliation with ASA installs and Branch is to look at 'New Download' counts, but subtract the percentage of LAT on users found by grouping LAT on/off in reporting. This will give an estimate of new downloads with LAT off, while Branch reports first opens from those downloads.

- *Time zones.* Ensure your Apple Search Ads time zone (in Settings > Overview > Account Information ) matches your Branch Dashboard time zone (visible under Account Settings).
- *Limit Ad Tracking (LAT) On.* Apple Search Ads doesn't report installs to third parties if the user has Limit Ad Tracking enabled. However the Apple Search Ads dashboard shows all installs by default, regardless of limit ad tracking state. You can see the approximate quantity of Limit Ad Tracking On and Limit Ad Tracking off installs by adding those columns in the Apple Search Ads Reporting Dashboard. Those installs will not appear in Branch's dashboard.
- *Attribution Windows.* Apple Search Ads attributes all installs within 30 days of an Apple Search Ads click to itself. Branch's default click to install attribution window is 7 days. You can modify Branch's click to install window. You can modify your [Apple Search Ads attribution windows](#change-attribution-windows) in Branch.
- *Last-click attribution.* Apple Search Ads attributes all installs within 30 days of an Apple Search Ads click to itself. Branch will attribute to the last click within its attribution windows, which can often be a different source than Apple Search Ads.
- *Reinstalls.* Apple Search Ads' dashboard shows reinstalls as conversions in its default view, but Branch calls these installs "REINSTALLS." In the Apple dashboard, select New Downloads or Redownloads in the column selector to align data.
- *Attribution API timeouts or delays.* Apple Search Ads Attribution API can be slow to respond. Although customers can edit the timeout, the default Branch timeout in the code above is just over 1 second. If Apple Search Ads responds after this timeout, Branch will not attribute the install to Apple Search Ads.
- *Opens vs. installs.* Branch considers the first open to be the install. Apple Search Ads considers the time that the user downloaded the app to be an install. This can cause discrepancies in counts and date of install.

### Adding deep linking to Apple Search Ads

Since this integration doesn't utilize Branch links, options for deep linking are limited. We'll pass back the value you use for `campaign` in the Apple Search Ads dashboard. Since this value is controlled by you, you can put anything there, but it will reflect on the Apple Search Ads dashboard. We will track installs regularly.

### Installs or conversion events appearing without keywords in Branch dashboard

There are <notranslate>"Keyword"</notranslate> and <notranslate>"Search Match"</notranslate> match sources for Apple Search Ads. The Search Match feature automatically matches your ad to relevant user searches on the App Store, rather than a rubric of preassigned keywords. Installs attributed to Search Matches do not have keywords associated with them. Search Match can be enabled & disabled at the Ad Group level in the Apple Search Ads dashboard.
