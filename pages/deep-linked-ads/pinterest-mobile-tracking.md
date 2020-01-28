---
title: Pinterest
---
## Overview

![Pinterest](https://cdn.branch.io/branch-assets/ad-partner-manager/388787843096400122/pinterest-1539022582075.png)

This guide will walk you through how to setup your campaigns with **[Pinterest](https://www.pinterest.com/)** using Branch Universal Ads and track ad conversions across **every device, platform, and channel**.



## Setup

### Integrating the SDKs and tracking in-app events

The Branch SDKs for iOS and Android allow you to get up and running quickly.

If you haven't already integrated Branch SDK into your application, please follow our integration guide to integrate Branch SDK into your application:

1. Documentation for [Android](/apps/android/)

1. Documentation for [iOS](/apps/ios/)

[block:callout]
{
  "type": "warning",
  "title": "Limitations with setDebug and seeing data in Branch",
  "body": "When integrating the SDKs, it's often useful to use setDebug to verify that your app is able to communicate with Branch servers, and is receiving deep link data. However, our upstream systems don't register test events sent using setDebug, so events will not appear in Liveview or Analytics, nor will they fire postbacks. You should disable setDebug when looking at Liveview or testing postbacks."
}
[/block]

#### Track conversion events

Install and open events are automatically tracked using just the Branch SDK integration. However, to track custom events, such as registration or purchase, you will need to integrate them into your application.

[block:callout]
{
  "type": "warning",
  "title": "Sending event metadata from your application",
  "body": "Please make sure that you setup and pass event metadata from the application to the ad partner. Follow up with your ad partner to get the list of required parameters."
}
[/block]

Please reference the general [V2 Event Tracking Guide](/apps/v2event/#overview). This will help ensure that you've integrated the right Branch events with the correct metadata.


[block:callout]
{
  "type": "info",
  "title": "Testing your events with Liveview",
  "body": "You can test your integration by going to our [Liveview page](https://dashboard.branch.io/liveview/events){:target="\_blank"}. Set a filter with the event name to verify that the Branch SDK is recording each event."
}
[/block]


### Enable the integration

1. Visit the [Ads page](https://dashboard.branch.io/ads) on the Branch dashboard.
2. Select [Partner Management](https://dashboard.branch.io/ads/partner-management) from the sidebar.
3. Search for <notranslate>**Pinterest**</notranslate> and click <notranslate>**Enable**</notranslate>.

![image](/images/pages/deep-linked-ads/pinterest/pinterest-enable.png)

[block:callout]
{
  "type": "tip",
  "title": "Enable postbacks",
  "body": "Basic postbacks will automatically be activated for events like _Install_ and _Purchase_ when you enable your ad partner. You can then [add additional postbacks](#adding-more-postbacks), for example, if you wanted to add postbacks for custom events that are specific to your app like _Account Created_. You can also [edit postbacks](#advanced-editing-postbacks) if there's additional data you really need to pass along to your ad partner."
}
[/block]

![image](/images/pages/deep-linked-ads/pinterest/pinterest-postbacks.png)

### Create an ad link

Once you've enabled an integration it's time to create a tracking link.

1. First click <notranslate>**Create Ad Link**</notranslate> and select an ad format. For App Install or App Engagement campaigns you'll want to select the <notranslate>**App Only**</notranslate> format. For campaigns where the user should go to web if they don't have the app, then you should select <notranslate>**Cross-Platform Search**</notranslate> or <notranslate>**Cross-Platform Display**</notranslate>. <notranslate>**Product Links**</notranslate> are for shopping or dynamic re-marketing campaigns.

    ![image](/images/pages/deep-linked-ads/branch-universal-ads/create-link.png)

1. At this point you need to name your link. Select something that will make it easy to find if you need it later. Your Ad Format and Ad Partner should be selected already, but feel free to choose one if they aren't. It's important that you select the right Ad Partner for analytics later on. Click <notranslate>**Configure Options**</notranslate> to continue.

    ![image](/images/pages/deep-linked-ads/branch-universal-ads/create-link-name.png)

1. This is your chance to add deep link data and analytics tags. Analytics tags are important for later segmentation, so click the <notranslate>**Analytics**</notranslate> sub tab to add a Channel and Campaign value.

    ![image](/images/pages/deep-linked-ads/branch-universal-ads/create-link-tags.png)

    [block:callout]
{
  "type": "tip",
  "title": "Set Analytics tags",
  "body": "It's easier to slice your data in our analytics platform if you properly assign analytics parameters to your link. <notranslate>_Channels_</notranslate> generally correspond to ad networks, and <notranslate>_Campaigns_</notranslate> correspond to marketing initiatives that you're launching. For example: <notranslate>_Channel_</notranslate>: "YouTube", <notranslate>_Campaign_</notranslate>: "Summer 2017 Shoe Discounts.""
}
[/block]

    [block:callout]
{
  "type": "info",
  "title": "Links Created by Agency Users",
  "body": "When an Agency user saves an ad link/Journey/Quick Link, that ad link/Journey/Quick Link is associated with that Agency via a unique agency_id that is included as a key-value in deep linking setup."
}
[/block]


1. Click <notranslate>**Create Link Now**</notranslate>, and you have your tracking link!

    ![image](/images/pages/deep-linked-ads/branch-universal-ads/create-link-completed.png)

1. When creating your Pinterest ad campaign, make sure to:

	1. Use a direct link to the Apple Store or Google Play Store in the <notranslate>**Destination URL**</notranslate> field.
	2. Remove `$idfa_sha1={sha1_advertising_id}` from your Branch Link if your Destination URL goes to the Google Play Store.
	3. Remove `$aaid_sha1={sha1_advertising_id}` from your Branch Link if your Destination URL goes to the Apple Store.
	4. Place your Branch link in the <notranslate>**Click Tracking URL**</notranslate>.
  5. Avoid using the <notranslate>**View Tracking URL**</notranslate>  until further notice.

	![image](/images/pages/deep-linked-ads/pinterest/pinterest-links.png)

### Viewing Your Data

The Ads Analytics Page on the Branch dashboard provides an interactive time series graph and table to view the performance of your Ad campaigns:

- Easily interact with your Analytics data breakdown and compare aspects of your Ad campaigns' performance by using the <notranslate>**Compare by**</notranslate> button to add a parameter to split the data displayed data by.
- You can also use the <notranslate>**Add Filter +**</notranslate> button to refine the data displayed to gain deeper insight into the performance of your Ad campaigns.

The <notranslate>**TRENDS**</notranslate> table shows the chart and breakdown of last 7 days data on the campaign performance by ad partner.

![Example Ads Analytics Graph](/images/ingredients/deep-linked-ads/view-ad-link-data/trends-graph.png)

The <notranslate>**EVENTS**</notranslate> table shows summary data on the performance of each Ad campaign.

![Example Ads Table](/images/ingredients/deep-linked-ads/view-ad-link-data/events-table.png)

On the top right side of the table you can find a download button to retrieve the chart's content as a CSV file.  For more info about Ads Analytics refer [here](/activity-reports-analytics/paid-ads-analytics/).

## Advanced Setup

Please refer to our [Advanced Universal Ads](/deep-linked-ads/branch-universal-ads-advanced/) guide for advanced options when enabling a Universal Ads partner.

## Troubleshooting

If you are running campaigns on Pinterest and having issues with Attribution on Branch, please check if you are using correct tracking links:

1. Link to the Apple AppStore or Google Play
2. Click and Impression links, generated on Branch dashboard, configured as described below.


### Verify Link Formatting

**Click Tracking Link**

```
[https://branchster.app.link/9kLGbtxJo2?%243p=a_pinterest&&%24idfa_sha1={sha1_advertising_id}&%24s2s=true&~ad_set_id={ad_group_id}&~ad_set_name={ad_group_name}&~campaign={campaign_name}&~campaign_id={campaign_id}&~click_id={click_id}&~creative_id={creative_id}&~creative_name={creative_name}&~secondary_publisher={publisher](https://branchster.app.link/9kLGbtxJo2?%243p=a_pinterest&%24aaid_sha1={sha1_advertising_id}&%24idfa_sha1={sha1_advertising_id}&%24s2s=true&~ad_set_id={ad_group_id}&~ad_set_name={ad_group_name}&~campaign={campaign_name}&~campaign_id={campaign_id}&~click_id={click_id}&~creative_id={creative_id}&~creative_name={creative_name}&~secondary_publisher={publisher)}
```

**Impression Tracking Link**

```
[https://impression.link/impression?branch_key=key_live_hkDytPACtipny3N9XmnbZlapBDdj4WIL&%243p=a_pinterest&%24s2s=true&%24aaid_sha1={sha1_advertising_id}&~ad_set_id={ad_group_id}&~ad_set_name={ad_group_name}&~branch_ad_format=App%20Only&~campaign={campaign_name}&~campaign_id={campaign_id}&~click_id={click_id}&~creative_id={creative_id}&~creative_name={creative_name}&~feature=paid%20advertising&~secondary_publisher={publisher](https://impression.link/impression?branch_key=key_live_hkDytPACtipny3N9XmnbZlapBDdj4WIL&%243p=a_pinterest&%24s2s=true&%24aaid_sha1={sha1_advertising_id}&~ad_set_id={ad_group_id}&~ad_set_name={ad_group_name}&~branch_ad_format=App%20Only&~campaign={campaign_name}&~campaign_id={campaign_id}&~click_id={click_id}&~creative_id={creative_id}&~creative_name={creative_name}&~feature=paid%20advertising&~secondary_publisher={publisher)}
```

Since Pinterest uses server-to-server clicks, make sure the following parameters are always present on the link:

*   **%24s2s=true**
    *   Must be always present on the link
*   **%24aaid_sha1={sha1_advertising_id}**
    *   For Android campaigns only, must be removed from the link for iOS campaigns
*   **%24idfa_sha1={sha1_advertising_id}**
    *   For iOS campaigns only, must be removed from the link for Android campaigns

Only **one** OS-specific Advertiser Identifier parameter must be on the link: either **%24idfa_sha1** for iOS or **%24aaid_sha1** for Android campaigns.

### Most common issues:

*   Advertiser ID is missed on the link
    *   Solution: Add OS-specific Advertiser Identifier
*   Both Advertiser IDs presented on the link
    *   Solution: Keep only one OS-specific Advertiser Identifier
*   Clicks are getting blocked by Branch Anti-Fraud rule - GEO_CONFLICT
    *   Pinterest current can’t provide user’s IP address and this can cause a GEO_CONFLICT Fraud Rule. If you use a GEO_CONFLICT fraud rule, we recommend either disabling it or not running on Pinterest until they are able to pass the client IP to MMPs.
