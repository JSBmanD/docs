---
title: SearchAdsHQ
---
## Overview

![SearchAdsHQ](https://cdn.branch.io/branch-assets/ad-partner-manager//1479b0002dff-18A02F13_B1DF_40A9_B097_D7421ED91A0B-1559413705882.png)

This guide will walk you through how to send your Branch data to **[SearchAdsHQ](https://searchadshq.com/)** using Branch Data Integration.



## Setup

### Integrating the SDKs and tracking in-app events

The Branch SDKs for iOS and Android allow you to get up and running quickly.

If you haven't already integrated Branch SDK into your application, please follow our integration guide to integrate Branch SDK into your application:

1. Documentation for [Android](/apps/android/)

1. Documentation for [iOS](/apps/ios/)

!!! warning "Limitations with setDebug and seeing data in Branch"
	When integrating the SDKs, it's often useful to use setDebug to verify that your app is able to communicate with Branch servers, and is receiving deep link data. However, our upstream systems don't register test events sent using setDebug, so events will not appear in Liveview or Analytics, nor will they fire postbacks. You should disable setDebug when looking at Liveview or testing postbacks.

### Enable the integration

1. Visit the [Data Integration](https://branch.dashboard.branch.io/data-import-export/data-feeds/integrations) on the Branch dashboard.
2. Search for your <notranslate>**Data Integration Partner**</notranslate>
3. Select your <notranslate>**Data Integration Partner**</notranslate>
4. Provide the required details
5. Click <notranslate>**Enable**</notranslate>


### Provide account credentials

Enter any credentials that may be required, and click Save and Enable in the bottom right hand corner.

!!! note "Account credentials"
	Please ask your ad partner where you can find your credentials.

### What Branch sends to SearchAdsHQ

* Install
* Open
* Commerce Event
* Custom Event

## Advanced

### Reset Settings

1. Click the <notranslate>**Reset All Settings**</notranslate> button at the Account Settings tab..

	![image](/_assets/img/ingredients/deep-linked-ads/reset-ad-settings/reset-ad-settings.png)

1. A confirmation modal will appear, just click <notranslate>**Yes, Reset Ad Partner**</notranslate> to conform the Reset.

	![image](/_assets/img/ingredients/deep-linked-ads/reset-ad-settings/reset-ad-settings_confirmation.png)

