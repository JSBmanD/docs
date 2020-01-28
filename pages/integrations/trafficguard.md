---
title: TrafficGuard
---
## Overview

![TrafficGuard](https://cdn.branch.io/branch-assets/ad-partner-manager//trafficguard-1550889602563.png)

This guide will walk you through how to send your Branch data to **[TrafficGuard](https://www.trafficguard.ai/)** using Branch Data Intgeration.



## TrafficGuard Setup

[block:callout]
{
  "type": "info",
  "title": "Requirements",
  "body": "You need to be a TrafficGuard customer & must have set up your [Properties within TrafficGuard](https://support.trafficguard.ai/docs/managing-your-properties)."
}
[/block]

To link your Branch account with TrafficGuard, you will need the following:

- Property ID (of the App you want to link)
- Organization ID
- Measurement API key

### Finding Your Property ID  

1. Open the TrafficGuard Portal.
 2. Go to Properties in the Side Navigation.
3. Select the property you want to link with Branch MMP.
4. Click on Settings or Copy the Property ID.

![image](/images/pages/integrations/trafficguard/trafficguard-property-id.png)

### Finding Your Organization ID & Measurement API Key

1. Open the TrafficGuard Portal.
2. Go to Settings in the Side Navigation.
3. Copy the Identifier (i.e Organization ID) and the Measurement API key.

![image](/images/pages/integrations/trafficguard/trafficguard-id-api-key.png)

## Branch Setup

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

### Enable the integration

1. Visit the [Data Integration](https://branch.dashboard.branch.io/data-import-export/data-feeds/integrations) on the Branch dashboard.
2. Search for your <notranslate>**Data Integration Partner**</notranslate>
3. Select your <notranslate>**Data Integration Partner**</notranslate>
4. Provide the required details
5. Click <notranslate>**Enable**</notranslate>


### Provide account credentials

Enter any credentials that may be required, and click Save and Enable in the bottom right hand corner.

[block:callout]
{
  "type": "info",
  "title": "Account credentials",
  "body": "Please ask your ad partner where you can find your credentials."
}
[/block]

### What Branch sends to TrafficGuard

* Install
* Click
* Open
* Commerce Events
* Custom Events

## Advanced

### Reset Settings

1. Click the <notranslate>**Reset All Settings**</notranslate> button at the Account Settings tab..

	![image](/images/ingredients/deep-linked-ads/reset-ad-settings/reset-ad-settings.png)

1. A confirmation modal will appear, just click <notranslate>**Yes, Reset Ad Partner**</notranslate> to conform the Reset.

	![image](/images/ingredients/deep-linked-ads/reset-ad-settings/reset-ad-settings_confirmation.png)
