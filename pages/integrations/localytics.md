---
title: Localytics
---
## Overview

We've partnered with Localytics to provide an easy way to deliver Branch installs and attributions to your Localytics dashboard. This is great for segmenting your users and providing higher granularity for your organic cohorts vs paid cohorts.

### How it works

We have built a custom integration to automatically send all Branch install data to Localytics without any extra work on your side (besides integrating both SDKs). We just need some configuration information from your Localytics account, and we'll take care of the rest.

[block:callout]
{
  "type": "protip",
  "title": "How do we differentiate Localytics and Branch installs?",
  "body": "We rely on a Branch link being clicked which leads to an install. This sets an internal boolean that an install came from Branch."
}
[/block]

## Setup

### Prerequisites

- This guide requires you to have already integrated the Branch mobile SDK into your app.
- You also need to [sign up for a Localytics account](https://www.localytics.com/free-trial-signup/) and [install the Localytics SDK](http://docs.localytics.com/).

### Set up Localytics

1. On the Localytics dashboard, navigate to the <notranslate>**Attribution**</notranslate> section, click the <notranslate>**•••**</notranslate> (overflow) button, and select <notranslate>**Settings**</notranslate>.
![image](/_assets/img/pages/integrations/localytics/localytics-more.png)
1. Once there, you'll need to add your <notranslate>**Store ID**</notranslate> (iTunes for iOS, Play Store for Android).
1. Under the section <notranslate>**Ad Tracking Setup**</notranslate>, check the box labeled <notranslate>**Third-party Attribution**</notranslate>. This will enable an <notranslate>**Attribution ID**</notranslate> for you. Copy it, and have it handy for the next steps.
![image](/_assets/img/pages/integrations/localytics/localytics-attr-settings.png)

[block:callout]
{
  "type": "protip",
  "title": "What does this mean?",
  "body": "Once you have selected to allow third-party attribution, Localytics will attribute non-Localytics installs to your dashboard. <notranslate>**This information is delayed by 10 minutes.**</notranslate>"
}
[/block]



### Configure the Branch Dashboard

1. On the Branch Dashboard (dashboard.branch.io), navigate to the [Integrations page](https://dashboard.branch.io/integrations).
1. Locate Localytics and choose <notranslate>**Enable**</notranslate>.
  * If you have not yet entered billing information, please do so now.
1. Enter your Localytics Attribution ID for each platform and hit <notranslate>**Save**</notranslate>

![image](/_assets/img/pages/integrations/localytics/enable-localytics-integration.png)

[block:callout]
{
  "type": "warning",
  "title": "Please test your integration!",
  "body": "Branch is not responsible for inaccurate API keys."
}
[/block]

## Advanced

### What Branch sends to Localytics

Branch Analytics Tag | Localytics Data Placeholder Tag
--- | ---
<notranslate>Campaign</notranslate> | `campaign`

Branch will also send any arbitrary parameters you attach to a link on to Localytics.  All Branch data will appear in the Localytics <notranslate>"Attribution"</notranslate> dashboard, but not the <notranslate>"Events"</notranslate> dashboard.

## Support

### Debugging strategies

When debugging Localytics, be sure to wait 10 minutes after you simulate an install. Also be sure to collect IDFA or Google Advertising ID.
