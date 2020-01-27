---
title: Netcore Smartech
---
## Overview

![Netcore Smartech](https://cdn.branch.io/branch-assets/ad-partner-manager//bcad3b4c0c31-netcore_1527812078091-1567147518764.png)

This guide will walk you through how to send your Branch data to **[Netcore Smartech](https://www.netcoresmartech.com/)** using Branch Data Integration.



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
  "type": "note",
  "title": "Account credentials",
  "body": "Please ask your ad partner where you can find your credentials."
}
[/block]

### What Branch sends to Netcore Smartech

* Install
* Commerce Event
* Custom Event

## Advanced

### Reset Settings

1. Click the <notranslate>**Reset All Settings**</notranslate> button at the Account Settings tab..

	![image](/_assets/img/ingredients/deep-linked-ads/reset-ad-settings/reset-ad-settings.png)

1. A confirmation modal will appear, just click <notranslate>**Yes, Reset Ad Partner**</notranslate> to conform the Reset.

	![image](/_assets/img/ingredients/deep-linked-ads/reset-ad-settings/reset-ad-settings_confirmation.png)

