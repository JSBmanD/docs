---
title: Digital Turbine
---
## Overview

![Digital-Turbine](https://cdn.branch.io/branch-assets/ad-partner-manager/386574786681131050/digital_turbine-1528502999872.png)

This guide will walk you through how to setup your campaigns with **[Digital Turbine](http://digitalturbine.com)** using Branch Universal Ads and track ad conversions across **every device, platform, and channel**.



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


### Enabling the Integration

1. Visit the [Ads page](https://dashboard.branch.io/ads) on the Branch dashboard.
2. Select [Partner Management](https://dashboard.branch.io/ads/partner-management) from the sidebar.
3. Search for your <notranslate>**Universal Ads Partner**</notranslate>.
4. Select Ad Partner Name and hit <notranslate>**Save & Enable**</notranslate>.

![image](/_assets/img/pages/deep-linked-ads/digital-turbine/digital-turbine-enable.png)

[block:callout]
{
  "type": "tip",
  "title": "Enable postbacks",
  "body": "Basic postbacks will automatically be activated for events like _Install_ and _Purchase_ when you enable your ad partner. You can then [add additional postbacks](#adding-more-postbacks), for example, if you wanted to add postbacks for custom events that are specific to your app like _Account Created_. You can also [edit postbacks](#advanced-editing-postbacks) if there's additional data you really need to pass along to your ad partner."
}
[/block]

![image](/_assets/img/pages/deep-linked-ads/digital-turbine/digital-turbine-postbacks.png)

### Creating an ad link

Once you've enabled an integration it's time to create a tracking link.

1. First, select an ad format. For App Install or App Engagement campaigns you'll want to select the <notranslate>**App Only**</notranslate> format. For Search or Display campaigns where the user should go to web if they don't have the app, then you should select <notranslate>**Cross-Platform Search**</notranslate> or <notranslate>**Cross-Platform Display**</notranslate>. <notranslate>**Product Links**</notranslate> are for shopping or dynamic remarketing campaigns.

    ![image](/_assets/img/pages/deep-linked-ads/branch-universal-ads/create-link.png)

1. At this point you need to name your link. Select something that will make it easy to find if you need it later. Your Ad Format and Ad Partner should be selected already, but feel free to choose one if they aren't. It's important that you select the right Ad Partner for analytics later on. Click <notranslate>**Configure Options**</notranslate> to continue.

    ![image](/_assets/img/pages/deep-linked-ads/branch-universal-ads/create-link-name.png)

1. This is your chance to add deep link data and analytics tags. Analytics tags are important for later segmentation, so click the <notranslate>**Analytics**</notranslate> sub tab to add a Channel and Campaign value.

    ![image](/_assets/img/pages/deep-linked-ads/branch-universal-ads/create-link-tags.png)

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
  "body": "When an Agency users saves an ad link/Journey/Quick Link, that ad link/Journey/Quick Link is associated with that Agency via a unique agency_id that is included as a key-value in deep linking setup."
}
[/block]


1. Click <notranslate>**Create Link Now**</notranslate>, and you have your tracking link! Take this link and give it to your Ad Partner's Account Manager or paste it into the tracking section of your campaign yourself.

    ![image](/_assets/img/pages/deep-linked-ads/branch-universal-ads/create-link-completed.png)


### Viewing Your Data

The Ads Analytics Page on the Branch dashboard provides an interactive time series graph and table to view the performance of your Ad campaigns:

- Easily interact with your Analytics data breakdown and compare aspects of your Ad campaigns' performance by using the <notranslate>**Compare by**</notranslate> button to add a parameter to split the data displayed data by.
- You can also use the <notranslate>**Add Filter +**</notranslate> button to refine the data displayed to gain deeper insight into the performance of your Ad campaigns.

The <notranslate>**TRENDS**</notranslate> table shows the chart and breakdown of last 7 days data on the campaign performance by ad partner.

![Example Ads Analytics Graph](/_assets/img/ingredients/deep-linked-ads/view-ad-link-data/trends-graph.png)

The <notranslate>**EVENTS**</notranslate> table shows summary data on the performance of each Ad campaign.

![Example Ads Table](/_assets/img/ingredients/deep-linked-ads/view-ad-link-data/events-table.png)

On the top right side of the table you can find a download button to retrieve the chart's content as a CSV file.  For more info about Ads Analytics refer [here](/activity-reports-analytics/paid-ads-analytics/).

[block:callout]
{
  "type": "info",
  "title": "Advanced Setup",
  "body": "Please refer to our [Advanced Universal Ads](/deep-linked-ads/branch-universal-ads-advanced/) guide for advanced options when enabling a Universal Ads partner."
}
[/block]

## Journeys with SingleTap™

This guide will walk you through how to set up Branch links that can be used in SingleTap™  Journeys with [Digital Turbine](https://www.digitalturbine.com/) and track resulting conversions.

### Device Requirements

*   Android 6.0 (API 23) or above
*   Digital Turbine Client running v5.7 or above


### Integrating the SDKs and Tracking In-app Events

The Branch SDK for Android allow you to get up and running quickly.

If you haven't already integrated Branch SDK into your application, please follow our integration guide to integrate Branch SDK into your application:

- Documentation for [Android](https://docs.branch.io/apps/android/)

**Limitations with setDebug and seeing data in Branch**

When integrating the SDKs, it's often useful to use setDebug to verify that your app is able to communicate with Branch servers, and is receiving deep link data. However, our upstream systems don't register test events sent using setDebug, so events will not appear in Liveview or Analytics, nor will they fire postbacks. You should disable setDebug when looking at Liveview or testing postbacks.

#### Track Conversion Events

Install and open events are automatically tracked using just the Branch SDK integration. However, to track custom events, such as registration or purchase, you will need to integrate them into your application.

**Sending event metadata from your application**

Please make sure that you setup and pass event metadata from the application to the ad partner. Follow up with your ad partner to get the list of required parameters.

Please reference the general [V2 Event Tracking Guide](https://docs.branch.io/apps/v2event/#overview). This will help ensure that you've integrated the right Branch events with the correct metadata.

**Testing your events with Liveview**

You can test your integration by going to our [Liveview page](https://dashboard.branch.io/liveview/events). Set a filter with the event name to verify that the Branch SDK is recording each event.

### Create your Branch Link

Start from the [Quick Links](dashboard.branch.io/quick-links/qlc/define) page of your Branch dashboard.

#### Define

1. On the next Define screen, fill in the following fields:
    *   <notranslate>**Name your link**</notranslate>: Give your link a name so you can find it in the dashboard later. Try to stick to a naming convention if creating multiple quick links
    *   <notranslate>**Enter a corresponding URL (OPTIONAL)**</notranslate>: Entering a URL to your site in this field will grab social information like Title, Description and Image when shared on social media (more on this later). It will also automatically set the provided URL as the $canonical_url which is useful if that is your routing mechanism.
    *   <notranslate>**Where will you post this link?**</notranslate>: The channel this will be used in. For example, Facebook, Twitter, Instagram, Snapchat, etc. It’s important to keep the spelling of channels consistent so you can analyze the performance of these channels in aggregate.
    *   <notranslate>**What campaign is it part of?**</notranslate>: Another analytics tag you can set as it relates to a campaign you are running. “Cyber Monday”, for example.
    *   When finished, select the Configure Options button
2. If the link will be shared and visible to the user, you have the ability to set a vanity alias for your quick link. The vanity alias on a link cannot be changed after link creation. When left empty, random string of characters will be assigned for the vanity alias.

#### Configure Options

1. The next section contains information pertaining to the various sub-tabs you see under the vanity URL:
    *   <notranslate>**DEEP LINKING**</notranslate> - Information passed from web to app to control routing, promo codes, open graph tags, etc.
        1. Routing - The mechanism in which users are routed from web to app so you can direct users to the correct content. For example, this may be via $canonical_url or $deeplink_path
            *   $canonical_url will be automatically populated from step 3a if filled out
        2. Promo codes - If your app is configured to use a promo code or discount from the Branch data dictionary, you can enter that here. You’ll need to know the exact key-value syntax. Talk to your mobile app developers if you’re unfamiliar.
        3. OG Tags - Control how your links will look when shared on social media platforms. In-depth customizable options here. <notranslate>**You will not set title, description or image in this section of the dashboard.**</notranslate>
    *   <notranslate>**REDIRECTS**</notranslate> - Links you create will automatically inherit redirects on iOS, Android, and Desktop per the default settings applied at your account level. Here you have the ability to override those defaults and direct users to specific locations if the app is not installed.
        4. Default Redirect - Set at the account level within Link Settings. Typically set to the relevant mobile stores
        5. Web URL - Send users to a specific web page if they don’t have to the app to avoid any unexpected flow to the app store
        6. Deepview - Send users to a specific deepview you may have created within the branch dashboard. Copy the key and paste it into the text box. Useful if you want to present the user with a preview of the content before taking them directly to the app store. Should not be set for Desktop option
    *   <notranslate>**ANALYTICS TAGS**</notranslate> - Setting tags on links in order to view performance on them in the dashboard
        7. Channel - For example, Facebook, Twitter, Instagram, Snapchat, etc. Keep the spelling of names consistent
        8. Campaign -“Cyber Monday”, for example
        9. Tags - Further tagging granularity. For example, “US”, “UK”, Social influencer name, blog poster, etc.
    *   <notranslate>**SOCIAL MEDIA**</notranslate> - Setting Title, Description and Image for instances when this link is shared on social platforms. This will be automatically populated from OG Tags included on the redirection URL. Use the previewer on the right side of the screen.

### Making your Branch Link compatible with SingleTap™

1. Retrieve your base SingleTap™ link from your Digital Turbine Account Manager.
2. Add `&dvURL=` followed by your URL encoded Branch link to the end of your Digital Turbine URL.

Example:

Base SingleTap URL:
```
https://delivers.dtignite.com/v2/delivers/clickAd.jsp?siteId=11365&campaignId=28394
```

Branch Link:

```
https://skdm3.app.link/pzBYIfsilZ
```

Resulting URL:

```
https://delivers.dtignite.com/v2/delivers/clickAd.jsp?siteId=11365&campaignId=28394&dvURL=https%3A%2F%2Fskdm3.app.link%2FpzBYIfsilZ
```
