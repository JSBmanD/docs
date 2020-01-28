---
title: Snap
---
## Overview

![Snap](https://cdn.branch.io/branch-assets/ad-partner-manager/104632553691939011/Group_2-1538714318018.png)

Branch can help track your **[Snap Ad](https://forbusiness.snapchat.com/ad-products)** campaigns through our integration with Snap.

Snap is a self-attributing network (SAN).

Snap campaign tracking can show you how many installs and conversion events were attributed to Snap, allowing you to make informed decisions with your advertising dollars.

Branch and Snap supports mobile app conversion attribution for the following campaign types:
  - App Installs
  - Drive Traffic to App

## Prerequisites

Before you begin, be sure the following is confirmed.

- [x] First, the Branch SDK must be integrated into your app, for both iOS and Android.
- [x] You must also collect the IDFA on iOS, or the AAID on Android. For specifics, refer to the set up guide for [iOS](/apps/ios/#install-branch) and [Android](/apps/android/#install-branch) respectively.
- [x] Make sure to track all necessary events through the SDKs, with instructions [here](#forward-events-to-snap)

## Authenticate with Snap

1. Navigate to the [partner management](https://dashboard.branch.io/ads/partner-management){:target="\_blank"} tab and search for Snap.
1. Select the tile with the ghost logo.

    ![Find Snap](/images/pages/deep-linked-ads/snap/find-snap.png)

1. Click <notranslate>**Log in with Snapchat**</notranslate>.
1. Read and accept the Snap Advertiser Agreement terms if you haven't already.

    [block:callout]
    {
      "type": "info",
      "title": "Branch Admin Required",
      "body": "You must be an Admin on the Branch account in order to accept the Snap Advertiser Agreement terms. You must accept the terms to track your Snap advertising."
    }
    [/block]

    ![Accept Terms](/images/pages/deep-linked-ads/snap/sign-terms.png)


1. Log in to Snap. Once logged in, accept permissions and click <notranslate>**Continue**</notranslate> .

    ![Log in to Snap](/images/pages/deep-linked-ads/snap/log-in-to-snap.png)
    ![Continue OAuth](/images/pages/deep-linked-ads/snap/accept-oauth.png)

    [block:callout]
    {
      "type": "warning",
      "title": "$2",
      "body": "
      Due to an issue with Snap Login, if you see the Snap "My Account" screen after logging in, you'll need to manually return to the Branch dashboard at [https://dashboard.branch.io/ads/partner-management/a_snap?tab=settings](https://dashboard.branch.io/ads/partner-management/a_snap?tab=settings){:target="\_blank"}. Click <notranslate>**Log in with Snapchat**</notranslate> again in the same browser, and you should see the <notranslate>**Continue**</notranslate>  button instead of the login screen.

      ![Snap - My Account](/images/pages/deep-linked-ads/snap/snap-my-account.png)"
    }
    [/block]

1. Click <notranslate>**Continue**</notranslate> to return to the Branch dashboard.

    ![Snap - My Account](/images/pages/deep-linked-ads/snap/oauth-redirect-return.png)

1. Confirm the ad accounts that you would like to track.

    ![Snap - My Account](/images/pages/deep-linked-ads/snap/snap-select-accounts.png)

1. Click <notranslate>**Save**</notranslate> to finish.

    ![Snap - My Account](/images/pages/deep-linked-ads/snap/snap-complete.png)

**Note:** The Snap measurement integration requires you to have configured your Android and iOS apps on the Link Settings page. If those have not been set up, you will not be able to track ads and you may see a validation warning.

## Using Branch Links in Snap Campaigns

Branch links are not necessary for attribution, however, you can insert Branch links into the <notranslate>**Drive Traffic to App**</notranslate> campaign type if you are trying to use deferred deeplinking (send users to a specific page after install+launch).

To use Branch links in your <notranslate>**Drive Traffic to App**</notranslate> campaigns:

1. Generate/fetch your Branch link from the Branch dashboard.
1. Set up your Snap campaign, selecting <notranslate>**Drive Traffic to App**</notranslate>.
  ![image](/images/pages/deep-linked-ads/snap/drive-traffic-to-app.png)
1. On the <notranslate>**Build Your Ads**</notranslate> page:
    1. Paste your Branch link into the <notranslate>**DEEPLINK URI**</notranslate> field.
    1. Select <notranslate>**Web Site**</notranslate> as the <notranslate>**FALLBACK TYPE**</notranslate> to ensure deferred deep linking via your Branch link.
  ![image](/images/pages/deep-linked-ads/snap/build-your-ad.png)
1. Finish building your Snap campaign.

[block:callout]
{
  "type": "warning",
  "title": "Web Site as Fallback Required for Deferred Deep Linking",
  "body": "Please ensure you choose <notranslate>**Web Site**</notranslate> as the <notranslate>**FALLBACK TYPE**</notranslate> and inserting the same Branch link into the provided field.  If you choose <notranslate>**App Install**</notranslate> as the `FALLBACK TYPE`, users not properly routed will be sent to the App Store without the Branch link and deferred deep linking will not occur."
}
[/block]

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


## View Attribution on Dashboard

All attribution can be visible on the [Branch dashboard summary page](https://dashboard.branch.io/). All installs and opens registered from this channel will automatically be tagged with `Ad Partner`: `Snap`. Other analytics tags will reflect the campaign, ad squad and ad names you set up in the Snap Ads dashboard.

Note that these stats are **limited to the date range** at the top of the page. You can expand the range if you'd like.

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


### Changing attribution windows

You can edit your attribution windows for Snap only. With this, you can preserve your Account Level Attribution Windows, but the attribution windows set for Snap will take precedence for Snap campaigns.

   ![image](/images/pages/deep-linked-ads/branch-universal-ads/anaw_clear.png)

 [block:callout]
 {
   "type": "info",
   "title": "Matching Attribution Windows",
   "body": "Please make sure your Branch attribution windows for Snap match those in your Snap account. See the Troubleshooting section for more detail."
 }
 [/block]

## Data Mapping between Branch & Snap

### Event Names

Branch supports sending [Standard and Custom Events](/apps/v2event/#v2-event){target:"\_blank"} to Snap. Here are the mappings for Branch events to Snap events.

By default, all events in the below table will be sent to Snap.

| Branch event name | Snap event name
| --- | ---
| `INSTALL` | `APP_INSTALL`
| `VIEW_ITEM` | `VIEW_CONTENT`
| `ADD_TO_CART` | `ADD_CART`
| `INITIATE_PURCHASE` | `START_CHECKOUT`
| `PURCHASE` | `PURCHASE`
| `ADD_PAYMENT_INFO` | `ADD_BILLING`
| `COMPLETE_REGISTRATION` | `SIGN_UP`
| `SEARCH` | `SEARCH`
| `ACHIEVE_LEVEL` | `LEVEL_COMPLETE`
| `OPEN`, `REINSTALL` | `APP_OPEN`

The below events can be sent to Snap by registering [custom events ](/apps/v2event/#track-custom-events){target:"\_blank"} that exactly match the Branch custom event name below. Snap does not accept other custom events, so they will not be sent to Snap.

| Branch custom event name | Snap event name
| --- | ---
| `SAVE` | `SAVE`
| `PAGE_VIEW` | `PAGE_VIEW`

### Campaign Data

Branch maps the following data fields from Snap to Branch.

Branch Data | Snap Data
--- | ---
`~campaign` | `campaign_name`
`~campaign_id` | `campaign_id`
`~ad_set_name` | `ad_squad_name`
`~ad_set_id` | `ad_squad_id`
`~ad_name` | `ad_name`
`~ad_id` | `ad_id`

### Metadata

| Branch metadata   | Snap Metadata  | Description                                                                                                                                                                                                                                     |
|-------------------|----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SKU (list of)     | `item_ids`       | International Article Number (EAN) when applicable, or other product or category identifier.                                                                                                                                                    |
| `Quantity`          | `number_items`   | Number of items.                                                                                                                                                                                                                                |
| `revenue`           | `price`          | Monetary value of the conversion event in float format. Valid delimiters are “|” “,” “;”. Please do not include currency symbols or commas as part of the value. (ex. single value: price=34.24, multiple values: price=99.43,45.34;34.2|23.22) |
| `currency_code`     | `currency`       | Currency in standard ISO 4217 code (ex. EUR, USD, JPY). Required if price is included.                                                                                                                                                          |
| `transactionID`     | `transaction_id` | Transaction ID.                                                                                                                                                                                                                                 |
| `searchQuery`       | `search_string`  | The text string that was searched.                                                                                                                                                                                                              |
| `custom_data.level` | `level`          | Level in the game.                                                                                                                                                                                                                              |

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

## Troubleshooting

### Discrepancies

- Snap Ads Manager time zones are set at the time your ad account is created. You can see your Snap time zone in your Snap Ad Account Settings, but you cannot change it. You can change your Branch dashboard time zone in [Account Settings](https://dashboard.branch.io/account-settings/app) to match.
- Verify your Snap attribution windows match your Branch attribution windows. Ask your Snap account manager for your attribution windows. Your Branch windows are visible either in Link Settings (global windows) or in the [Attribution Windows](https://dashboard.branch.io/ads/partner-management/a_snap?tab=attribution_windows) section of the Snap entry in Ads Partner Manager. Snap windows can be configured under "Customize Columns" in the Snap UI.

    ![Snap - Attribution Windows](/images/pages/deep-linked-ads/snap/snap-attribution-windows.png)

- When deep linking, create a link via the Branch dashboard. If you are running an app campaign, please ensure your link has `%24deeplink_no_attribution=true` as a query parameter to remove that link's ability to claim attribution, otherwise the link may claim attribution over the SAN claim. The link will still deep link.
- Snap's reporting API does not provide any <notranslate>"compare by"</notranslate> functionality outside of the ads analytics tags. So, you cannot compare Snap click + impression data by platform, OS or country, for example.

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


###Exporting Snap Data

You can see analytics on impressions, clicks, installs, opens and conversion events on various pages of the Branch Dashboard.

We cannot send device-level Snap attribution data to third parties. Thus we cannot send events attributed to Snap via Data Integrations. Please instead consider analyzing this data in-house (using Webhooks, the Daily Export API, or CSV Exports), or using the Branch Dashboard for all of your analytics and attribution needs.
