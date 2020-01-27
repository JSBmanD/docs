---
title: Adding Test Devices
---

## Overview

In order to easily test your Universal Ads campaign setup, we recommend you first add a test device to your Branch account. Doing so tells Branch servers that resulting conversions from said device are for testing purposes only; i.e. these conversions will not be considered normal traffic and therefore not be treated as such.

As Branch only allows one install event per unique device to ever be measured and stored, if you do not first add a test device, you will only be able to test the install conversion event once ever.

[block:callout]
{
  "type": "info",
  "title": "Part of Testing Universal Ads Campaign Setup",
  "body": "Please complete the [Testing Universal Ads Campaign Setup](/resources/testing-universal-ads-campaign-setup/) guide once you've added your test device per the instructions below."
}
[/block]

## Device IDs Supported

In order to identify your device as a test device within Branch, we require you provide one of the following device IDs:

### Android

- Google Advertising ID (GAID)

### iOS

- Identifier for Advertisers (IDFA)

[block:callout]
{
  "type": "info",
  "title": "Branch Device ID Finder",
  "body": "If you do not know how to access your device's IDs, you can use Branch's **Device ID Finder** app to easily see your device's ID.  "
}
[/block]

	- Get the [Android App](https://play.google.com/store/apps/details?id=io.branch.deviceid)
	- Get the [iOS App](https://apps.apple.com/us/app/branch-device-id-finder/id1477763736)

## Adding Your Test Device

To ensure you can use your device to test:

1. In the left-hand navigation, under **Channels & Links**, click **Link Settings**.
2. On the **Link Settings** page, click the **Test Devices** tab and click the **Add Device** button.
3. In the **Add Device** modal, provide the following:
	1. **Device Name**
	2. **Device ID**
	3. **Device Platform**
4. Click **Add Device**.

![image](/_assets/img/pages/links/add-test-device.png)

### Things to Keep In Mind

- You can add up to 50 test devices per app in your Branch dashboard.
- Any user can add a device for testing, however, you must have **Edit** access to remove a test device.
- The test device is specific to the app you add it under.  If you use it to test other apps, Branch will treat it like live traffic and it will be attributed and used for downstream analytics.

## Resetting Your Test Device Data

If you need to test the install event more than once, you need to reset your test device data after each install attempt.  Not doing so results in the next install attempt being marked as `reinstall`.

To reset your test device data:

1. On the **Test Devices** page, find the test device you want to reset and click on the **`...`** button.
2. Click **Reset Device Data**.
3. In the pop-up modal, click **Yes, Reset**.

![image](/_assets/img/pages/links/reset-device.png)
