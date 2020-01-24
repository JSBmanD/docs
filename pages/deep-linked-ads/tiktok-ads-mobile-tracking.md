---
title: Tiktok Ads
---
## Overview

![Tiktok Ads](https://cdn.branch.io/branch-assets/ad-partner-manager/388787843096400122/Tiktok_ads_logo-1547166341261.png)

This guide will walk you through how to setup your campaigns with **[Tiktok Ads](http://ads.tiktok.com/)** using Branch Universal Ads and track ad conversions across **every device, platform, and channel**.



## Setup

### Integrating the SDKs and tracking in-app events

The Branch SDKs for iOS and Android allow you to get up and running quickly.

If you haven't already integrated Branch SDK into your application, please follow our integration guide to integrate Branch SDK into your application:

1. Documentation for [Android](/apps/android/)

1. Documentation for [iOS](/apps/ios/)

!!! warning "Limitations with setDebug and seeing data in Branch"
	When integrating the SDKs, it's often useful to use setDebug to verify that your app is able to communicate with Branch servers, and is receiving deep link data. However, our upstream systems don't register test events sent using setDebug, so events will not appear in Liveview or Analytics, nor will they fire postbacks. You should disable setDebug when looking at Liveview or testing postbacks.

#### Track conversion events

Install and open events are automatically tracked using just the Branch SDK integration. However, to track custom events, such as registration or purchase, you will need to integrate them into your application.

!!! warning "Sending event metadata from your application"
	Please make sure that you setup and pass event metadata from the application to the ad partner. Follow up with your ad partner to get the list of required parameters.

Please reference the general [V2 Event Tracking Guide](/apps/v2event/#overview). This will help ensure that you've integrated the right Branch events with the correct metadata.


!!! note "Testing your events with Liveview"
	You can test your integration by going to our [Liveview page](https://dashboard.branch.io/liveview/events){:target="\_blank"}. Set a filter with the event name to verify that the Branch SDK is recording each event.


### Enabling the Integration

1. Visit the [Ads page](https://dashboard.branch.io/ads) on the Branch dashboard.
2. Select [Partner Management](https://dashboard.branch.io/ads/partner-management) from the sidebar.
3. Search for your <notranslate>**Universal Ads Partner**</notranslate>.
4. Select Ad Partner Name and hit <notranslate>**Save & Enable**</notranslate>.

![image](/images/pages/deep-linked-ads/tiktok-ads/tiktok-ads-enable.png)

#### Provide account credentials

Enter any credentials that may be required, and click Save and Enable in the bottom right hand corner.

!!! note "Account credentials"
	Please ask your ad partner where you can find your credentials.

!!! tip "Enable postbacks"
    Basic postbacks will automatically be activated for events like _Install_ and _Purchase_ when you enable your ad partner. You can then [add additional postbacks](#adding-more-postbacks), for example, if you wanted to add postbacks for custom events that are specific to your app like _Account Created_. You can also [edit postbacks](#advanced-editing-postbacks) if there's additional data you really need to pass along to your ad partner.

![image](/images/pages/deep-linked-ads/tiktok-ads/tiktok-ads-postbacks.png)

### Creating an ad link

Once you've enabled an integration it's time to create a tracking link.

1. First, select an ad format. For App Install or App Engagement campaigns you'll want to select the <notranslate>**App Only**</notranslate> format. For Search or Display campaigns where the user should go to web if they don't have the app, then you should select <notranslate>**Cross-Platform Search**</notranslate> or <notranslate>**Cross-Platform Display**</notranslate>. <notranslate>**Product Links**</notranslate> are for shopping or dynamic remarketing campaigns.

    ![image](/images/pages/deep-linked-ads/branch-universal-ads/create-link.png)

1. At this point you need to name your link. Select something that will make it easy to find if you need it later. Your Ad Format and Ad Partner should be selected already, but feel free to choose one if they aren't. It's important that you select the right Ad Partner for analytics later on. Click <notranslate>**Configure Options**</notranslate> to continue.

    ![image](/images/pages/deep-linked-ads/branch-universal-ads/create-link-name.png)

1. This is your chance to add deep link data and analytics tags. Analytics tags are important for later segmentation, so click the <notranslate>**Analytics**</notranslate> sub tab to add a Channel and Campaign value.

    ![image](/images/pages/deep-linked-ads/branch-universal-ads/create-link-tags.png)

    !!! tip "Set Analytics tags"

        It's easier to slice your data in our analytics platform if you properly assign analytics parameters to your link. <notranslate>_Channels_</notranslate> generally correspond to ad networks, and <notranslate>_Campaigns_</notranslate> correspond to marketing initiatives that you're launching. For example: <notranslate>_Channel_</notranslate>: "YouTube", <notranslate>_Campaign_</notranslate>: "Summer 2017 Shoe Discounts."

    !!! info "Links Created by Agency Users"
        When an Agency users saves an ad link/Journey/Quick Link, that ad link/Journey/Quick Link is associated with that Agency via a unique agency_id that is included as a key-value in deep linking setup.


1. Click <notranslate>**Create Link Now**</notranslate>, and you have your tracking link! Take this link and give it to your Ad Partner's Account Manager or paste it into the tracking section of your campaign yourself.

    ![image](/images/pages/deep-linked-ads/branch-universal-ads/create-link-completed.png)


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
