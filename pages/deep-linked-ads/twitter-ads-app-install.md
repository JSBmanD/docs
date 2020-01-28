---
title: Twitter Ads
---
title: Twitter Ads App Install Measurement

![image](/images/pages/deep-linked-ads/twitter-ads/twitter-ads-logo.png)

## Overview

By connecting your Twitter Ads and Branch accounts, the following is enabled:

- App conversion data collected by the Branch SDK sent to Twitter Ads for attribution.
- `Read-only` access to install data (not cost/click/impression data) from Twitter Ads in your Branch account.

[block:callout]
{
  "type": "info",
  "title": "Deep Linking Not Supported",
  "body": "Twitter Ads does not support the use of deep links at this time.  As such, this integration does not require the use of Branch links."
}
[/block]

## Prerequisites

[block:callout]
{
  "type": "warning",
  "title": "Prerequisites",
  "body": "
  * [x] Ensure Branch is the only MMP configured in your Twitter account.  This must be done before you enable the Twitter integration in your Branch dashboard.
	* [x] To track installs from Twitter Ads you should [integrate the Branch SDK](/apps/ios/#integrate-branch) into your app OR send events via server to server integration including device IDs (Google AID or Apple IFA).
	* [x] To use Twitter App Install Ads ensure you have:
		* [x] URI schemes configured on iOS
		* [x] URI schemes configured on Android
		* [x] iOS App Store ID set
		* [x] Android Package Name set
	* [x] Ads is a premium product priced on Monthly Active Users. Sign up for the Ads product to enable this functionality."
}
[/block]

## Campaign Support

| **Campaign Type** | **Attribution Supported** | **Branch Linking Supported** |
| - | - | - |
| App installs | Yes | No |
| App re-engagements | Yes | No |
| Website clicks or conversions | Yes (Branch only) | Yes |

The integration with Twitter Ads for mobile app conversion tracking is designed to support App install and re-engagement campaigns. Other campaign types can be run with Branch links, but will only attribute in Branch and is not part of the integration.

## Branch links

App campaigns do not support Branch links. Branch links can be used on Tweets, promoted Tweets, and non-app campaign types, but will only report conversions in Branch and not Twitter. To avoid high-level reporting discrepancies, you may want to segment this traffic from the integration by using Quick Links.

## Enable Twitter Ads for Measurement

[block:callout]
{
  "type": "info",
  "title": "Enabling Twitter",
  "body": "
  - Completing this section -- "Enable Twitter Ads for Measurement" -- will result in Branch sending app events to Twitter in order to attribute them back to Twitter ad campaigns.
	- Ensure Branch is the only MMP configured in your Twitter account.  This must be done before you enable the Twitter integration in your Branch dashboard."
}
[/block]

1. Navigate to the [Partner Management tab](https://dashboard.branch.io/ads/partner-management) and search for **Twitter**.

1. Click <notranslate>**Log in with Twitter**</notranslate>

    ![image](/images/pages/deep-linked-ads/twitter-ads/twitter-ads-enable.png)

1. Provide your Twitter credentials to begin the authorization process.

1. Agree to the Advertising Terms & Conditions by checking the `I agree to the Twitter Ads Terms & Conditions`.

    ![image](/images/pages/deep-linked-ads/twitter-ads/twitter-ads-tocs.png)

1. Authorize Branch Twitter Ads Manager to use your account by clicking `Authorize app`.

    ![image](/images/pages/deep-linked-ads/twitter-ads/twitter-ads-authorize.png)

1. Select the ad accounts for which you want to run app install ads and click `Save`.

    ![image](/images/pages/deep-linked-ads/twitter-ads/twitter-ads-accounts.png)

1. Finally, to create a Twitter Ads link click the `Create Twitter Link` button in the top right hand corner.


## Creating a Twitter Ads Campaign

Please follow Twitter's documentation on how to set up an [App Install Ad Campaign](https://business.twitter.com/en/help/campaign-setup/create-an-app-installs-or-app-engagement-campaign.html).

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


## Data Mapping between Twitter Ads & Branch

Branch maps the following data fields from Twitter Ads to Branch.

Twitter Data | Branch Data | Possible Values
--- | --- | ---
n/a | `~advertising_partner_name` | “Twitter”
`tpn_attribution` | `~channel` | “Twitter” if null or last touch, or “Twitter Audience Platform” if TAP is last touch
`engagement_time` | `last_attributed_touch_timestamp` | 1455675372963
`campaign_name` | `~campaign` | Light Bright Launch
`campaign_id` | `~campaign_id` | 15292426
`engagement_type` | `last_touch_type` | CLICK or IMPRESSION
`country_code` | `~user_data_geo_country_code` | US

## Forwarding Events to Twitter Ads

Once you begin tracking events through the Branch SDK, we will start sending them to Twitter Ads. Twitter Ads has pre-defined events that map to pre-defined Branch events, listed below.

Branch will forward in-app events to Twitter Ads for campaign optimization. In addition, Branch will receive attribution data for rich analysis in the Branch dashboard.

Branch Event Name | Twitter Conversion Type
--- | ---
`INSTALL` | `INSTALL`
`PURCHASE` | `PURCHASE`
`INITIATE_PURCHASE` | `CHECKOUT_INITIATED`
`ADD_TO_CART` | `ADD_TO_CART`
`VIEW_ITEM` | `CONTENT_VIEW`
`ADD_PAYMENT_INFO` | `ADDED_PAYMENT_INFO`
`COMPLETE_REGISTRATION` | `SIGN_UP`
`SEARCH` | `SEARCH`
`ACHIEVE_LEVEL` | `LEVEL_ACHIEVED`
`OPEN`, `REINSTALL` | `RE_ENGAGE`
`COMPLETE_TUTORIAL` | `TUTORIAL_COMPLETE`
`ADD_TO_WISHLIST` | `ADD_TO_WISHLIST`
`UNLOCK_ACHIEVEMENT` | `ACHIEVEMENT_UNLOCKED`
`SHARE` | `SHARE`
`SPEND_CREDITS` | `SPENT_CREDITS`
`RATE` | `RATED`
`UPDATE` | `UPDATE`
`RESERVE` | `RESERVATION`
`LOGIN` | `LOGIN`
`INVITE` | `INVITE`

In order to track these events, please refer to the [v2 Event document](/apps/v2event/#v2-event) for further information.

## Twitter Data Sharing

Twitter has a data agreement with TUNE, and there are several layers of data that are concealed and can be exposed depending on who is accessing the data, and how the data is being accessed or exported.

### Data Levels

<notranslate>**Source Level**</notranslate> > Source level is the source information including Publisher name (hardcoded to "Twitter"), Publisher ID, 3p (hardcoded to "a_twitter") and advertising partner name (hardcoded to "Twitter").

<notranslate>**Campaign Level**</notranslate> > Campaign level includes campaign information such as Campaign (Twitter Campaign Name), Campaign ID (Twitter Campaign ID), Channel (Twitter or Twitter Audience Platform), Feature (hardcoded to "paid advertising"), Ad ID (Tweet ID), Partner Ad Set ID (Line Item ID).

[block:callout]
{
  "type": "warning",
  "title": "Whitelisting for Device IDs",
  "body": "If you want to receive device IDs and campaign level information via Branch's data feeds, then you must contact your Twitter and Branch account manager. Please make use the email title of "CAMPAIGN LEVEL DATA EXPORT WHITELIST" when contacting your account manager to ensure proper handling."
}
[/block]

### Accessible Data

#### Clients

**Branch API/UI**:

 - [x] Source and campaign level data by default in aggregate reports.
 - [x] Source level data in exports by default. Campaign level data is not accessible in exports without whitelisting.

**Data Feeds**:

 - [x] Source level data with identifiers to an **internal BI endpoint only**.
 - [x] Data can not be sent to Branch data integrations, i.e. third party analytics.
 	 - [x] Postbacks set up to analytics providers will scrub source and campaign level information by default, identifiers will still pass through, and the conversions will appear organic to the third party.

#### Agencies

Agencies can access Twitter data under the following circumstances:

 - [x] If they have been provided full agency access by the client.
 - [x] If they append their agency attribution code to the Twitter campaign they are running.

## Reporting and Discrepancies

There are two main causes for Twitter Ads discrepancies with Branch:

**Not last click**

Twitter will claim and report all conversions they have tracked clicks or views for within window. Because Branch will attribute to the last partner to interact with the user, you may see up to 10-30% discrepancies.

**August 2019 user data sharing changes**

In early August of 2019, Twitter temporarily suspended sharing conversion data with MMP's. Upon resuming, Twitter will still attribute all user conversions in their reporting, but will only share conversion data if the user has allowed data sharing in their settings. This may result in up to 50% discrepancies after the first week of August depending on the settings of the users you're acquiring. For more details contact Twitter or reference [their messaging](https://help.twitter.com/en/ads-settings).

## Troubleshooting

**Why am I seeing an onboarding error or not seeing an ad account?**

- You must have permissions to configure ad accounts.
- You can only track apps that are configured with store IDs & package names in Link Settings.

**What does the error <notranslate>**Missing app event tags**</notranslate> mean?**

If you see the <notranslate>**Missing apop event tags**</notranslate> error while trying to enable the Twitter integration, please go through the onboarding flow in your Branch dashboard again.  If you continue to see this error, please [Contact Support](mailto:support@branch.io).

**What does the error `Non-Branch app event provider configuration detected` mean?**

If you see the `Non-Branch app event provider configuration detected` error while trting to enable the Twitter integration, this means you have another Twitter Mobile Measurement Partner configured for your app/ad account combination.  You must disable/delete any other MMP integration before enabling the Twitter integration in your Branch dashboard.

**Why are there so many events?**

We configure all permissible events at time of enablement so there’s no delay in tracking new events when they’re set up.

**Why can't I view cost/click/impression data?**

Twitter does not currently allow MMPs to access this data. We’re in active discussions. Please tell your Twitter AM if you’d like this data available in Branch.
