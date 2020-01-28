---
title: Reporting & Discrepancies
---
##  Google Ads Resources
	- [Overview](/deep-linked-ads/google-ads-overview/)
	- [Enabling the Integration](/deep-linked-ads/google-ads-setup/)
	- **Reporting & Discrepancies (this page)**
	- [Customization & Edge Cases](/deep-linked-ads/google-ads-customization/)

[block:callout]
{
  "type": "info",
  "title": "Available Compare By Dimensions for SANs",
  "body": "Self-Attributing Networks (SANs) do not always support all of the dimensions available in your Branch analytics.  Please refer to the following table when using Compare by dimensions."

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
	}
	[/block]

## Enabling and Segmenting View-Through Conversions in Reporting

By default, Google Ads includes View-Through Conversion counts in a separate column in reporting. If you have impression windows enabled in Branch, we can also attribute VTC installs and events (when there is not a matching click from another partner). Those will be grouped into the install and event counts, and can be segmented using the 'last attributed touch type' compare by in Branch reporting. You can manage settings to enable this attribution within the attribution settings tab of the Google AdWords partner management or by reaching out to support@branch.io

[block:callout]
{
  "type": "warning",
  "title": "Not Yet Supported",
  "body": "Viewing click/impression/cost data in your Branch dashboard is not yet supported for App Engagement campaigns."
}
[/block]


## Cost Data

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


## Click Reporting

#### Universal App Campaigns (UAC) - Limited Campaign Information
These campaign parameters are not supported by UAC and will not be available in reports:

Google parameter | Branch parameter
--- | ---
`keyword` | `~keyword_id`
`placement` | `~placement`
`ad_group_id` | `~ad_set_id`
`creative_id` | `~creative_id`

#### Google Adwords Valuetrack Parameters

Branch utilizes Google's Valuetrack parameters to collect more detailed information on the source of an ad click. Furthermore, we dynamically map Adword's <notranslate>**campaign id**</notranslate> and <notranslate>**network parameters**</notranslate> to a Branch link's campaign analytics `Campaign` and `Channel` tags respectively. Leave these tags blank to have them dynamically mapped.

See below for a table of Valuetrack parameters collected by default through Branch's Ad links and refer to the table in [Google's Valuetrack docs](https://support.google.com/adwords/answer/6305348){:target="_blank"} for more parameters to append.

Default Valuetrack Parameters on Branch Ad links | What it returns
--- | ---
`\{campaignid\}` | The ad's campaign ID
`\{adgroupid\}` | The ad's ad group ID
`\{keyword\}` | For the Search Network: the keyword from your account that matches the search query, unless you are using a Dynamic Search ad, which returns a blank value. For the Display Network: the keyword from your account that matches the content.
`\{placement\}` | The content site where your ad was clicked (for keyword-targeted campaigns), or the matching placement targeting criteria for the site where your ad was clicked (for placement-targeted campaigns)
`\{network\}` | Where the click came from: "g" for Google search, "s" for a search partner, or "d" for the Display Network
`\{lpurl\}` | The final URL of the ad link clicked

#### Universal App Campaigns (UAC)
- As links are not accepted into the Google Ads UAC UI, we will only report on clicks in aggregate (via Google's reporting API)
- Individual UAC clicks will not appear in Branch's liveview dashboard, webhooks, or exports
- 'Unique' UAC data cannot be viewed on the ads analytics dashboard (Non-UACs, like regular Search campaigns, will report on clicks in all Branch dashboards)
- Reporting on UAC clicks is done every 3 hours
- Branch only reports on clicks from an Google Ads campaign that led to an install or app engagement

#### My click data is missing or duplicated for my web campaign

**A:** Click data for web campaigns is available with full breakdowns, but there are specific requirements for setting up web campaigns. Please see the [SAN Web Tracking](/deep-linked-ads/san-web-tracking) guide for more information on setting up web campaigns.

## Conversions

#### My campaign is reporting a number of conversions much higher than the number of conversions shown in the conversion table in Google Ads

**A:** When viewing a campaign, it shows the sum of all conversion events that apply to it. To view by conversion, navigate to `Segment` > `Conversions` > `Conversion name`, in order to clearly see the breakdown of your campaign's conversions.

<img src="/images/pages/deep-linked-ads/google-conversions/conversion-segment.png" alt="Google Ads Conversion Segment" class="center">

#### Post-install events are attributed to Google Ads in the Branch dashboard but are not appearing in Google Ads

**A:** Ensure that, in the [Google Ads dashboard, you have imported all Branch events](/deep-linked-ads/google-ads-overview/#import-events-in-adwords) that you want to see in Google Ads.

#### I'm seeing a discrepancy between conversion counts in Branch and Google Ads

**A:** While we should always expect around a 5% discrepancy due to time zone differences and the like, if you are seeing significant discrepancies, it could be an indication of a broader problem.

The first thing to do is to make sure you have enabled the `Use Ad Partner Attribution Windows` setting for Google Ads. Go to [Link Settings](https://dashboard.branch.io/ads/partner-management/a_google_adwords?tab=attribution_windows), and navigate down to the Attribution Windows section. Here, you should set the attribution window for `click to install`, `click to session start`, and `click to conversion event` to be 30, 90, and 90 days respectively. This aligns with Google's default attribution windows, but if you'd like to make them shorter, feel free.

Another source of discrepancies is the fact that attribution is based upon *click* time in Google Ads, whereas it is based upon *conversion* time in the Branch dashboard. This isn't a discrepancy per se, but will sometimes show different numbers in the two dashboards. This usually does not affect install numbers (because install usually happens same day as click) but will especially have impact on downstream events, where events can sometimes occur and be attributed up to 90 days after click.

Google will send attribution data for almost every app conversion that they count on their end, with the exception of iOS Search traffic within UAC, and they also do not currently confirm standalone (outside of UAC) YouTube TrueView conversions to Branch - this is estimated to be available Q4 2019.

Finally, Google Ads can delay reporting up to 24 hours. It's best to measure campaigns in a trailing manner.

#### My UAC data looks misaligned when I compare by certain filters

**A:** Google _installs_ should have the full range of compare by options in the dashboard. However, _clicks, impressions and cost_ data for UAC are imported via the Google Ads Reporting API, as noted above. The Google Ads Reporting API does not necessarily provide the same breakdowns that Branch can create with raw install events, so there may be cases where the Branch Dashboard cannot compare by the same dimensions for clicks vs installs.
