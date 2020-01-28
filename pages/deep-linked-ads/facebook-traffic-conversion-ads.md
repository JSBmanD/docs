---
title: Facebook Traffic and Conversion Ads
---
# Facebook Traffic and Conversion Ads

## Overview

Branch links can be used together with Facebook Traffic and Conversion ads, allowing you to track engagement with your advertisements and ad-driven installs which deep link new users directly to content the first time they open your app.

Note: This documentation applies for Ad placements across Facebook and the Audience Network.

This documentation supports the following Facebook Ad Campaign types:

Facebook Campaign Category | Campaign Type/Objective | Branch Ad Format
--- | --- | ---
Consideration | Traffic | Cross-platform Display
Conversion | Conversions | Cross-platform Display

#### Facebook Campaign Advert Format Support Table

Facebook Campaign Type | Photo | Video | Carousel | Slideshow | Collection | Dynamic | Canvas
--- | --- | --- | --- | --- | --- | --- | ---
Traffic | ✔︎ | ✔︎ | ✔︎ | ✔︎ | ✔︎ | ✔︎ | ✔︎
Conversion | ✔︎ | ✔︎ | ✔︎ | ✔︎ |  |  | ✔︎

[block:callout]
{
  "type": "info",
  "title": "Facebook Campaign Types",
  "body": "Looking for other Facebook Ad campaign types? Please check out our [Facebook Ads Overview guide](/deep-linked-ads/facebook-ads-overview)."
}
[/block]

## Setup

[block:callout]
{
  "type": "warning",
  "title": "Prerequisites",
  "body": "* [x] To track installs from Facebook Ads you should [integrate the Branch SDK](/apps/ios/#integrate-branch) into your app.
	* [x] To use Branch links in Facebook App Install Ads ensure you have:
		* [x] URI schemes configured on iOS
		* [x] URI schemes configured on Android
		* [x] iOS App Store ID set
		* [x] Android Package Name set
		* [x] Social Media Settings filled out (i.e. OG tags at the bottom of [Link Settings](/links/default-link-behavior/#social-media))
	* [x] If you want to deep link from your ads directly to content, you should [configure deep link routing](/deep-linking/routing/).
	* [x] Ads is a premium product priced on Monthly Active Users. Sign up for the Ads product to enable this functionality."
}
[/block]

#### Enable Facebook as an Ad Partner (for measurement)

[block:callout]
{
  "type": "info",
  "title": "Enable Facebook as an Ad Partner",
  "body": "Completing this section -- "Enable Facebook as an Ad Partner" -- will result in Branch sending app events to Facebook in order to attribute them back to ad campaigns. <notranslate>**This does not enable deep linking for the ad**</notranslate>. Further work below is required for deep linking."
}
[/block]

If you haven't enabled Facebook as an Ad Partner on the Branch dashboard follow this section to do so. Advanced options for sending events can be found [here](/deep-linked-ads/facebook-ads-faq/#facebook-mmp-event-options).

1. Navigate to the [Partner Management tab](https://dashboard.branch.io/ads/partner-management).

    ![Ads Partner Management](/images/ingredients/deep-linked-ads/enable-facebook-ad-partner/ads-partner-management.png)

1. Search for <notranslate>**Facebook**</notranslate>.

1. Click <notranslate>**Connect With Facebook**</notranslate>

    ![Connect with Facebook](/images/ingredients/deep-linked-ads/enable-facebook-ad-partner/1-connect.png)

1. Login to Facebook if you are not logged in

    ![Login](/images/ingredients/deep-linked-ads/enable-facebook-ad-partner/2-login.png)

1. Confirm that Branch can receive your public profile

    ![Public profile](/images/ingredients/deep-linked-ads/enable-facebook-ad-partner/3-profile.png)

1. Confirm that Branch can have permissions `ads_read`

    ![OAuth scopes](/images/ingredients/deep-linked-ads/enable-facebook-ad-partner/4-scopes.png)

 	`ads_read` is used to surface impressions and clicks on the Branch Dashboard.

1. Select the ad accounts for which you want to run app install ads or app engagement ads

    ![Choose ad accounts](/images/ingredients/deep-linked-ads/enable-facebook-ad-partner/5-adaccounts.png)

		[block:callout]
		{
		  "type": "info",
		  "title": "Ad Account FAQ",
		  "body": "If you are having trouble finding or selecting the ad account(s) for which you want to run ads, please visit our [FAQ](/deep-linked-ads/facebook-ads-faq/#im-having-problems-finding-or-choosing-the-correct-ad-accounts)."
		}
		[/block]

1. Click to select a Facebook app id for which you want to run Facebook ads

    ![enter app id](/images/ingredients/deep-linked-ads/enable-facebook-ad-partner/6-app-1.png)

1. Copy the app id

    ![find app id](/images/ingredients/deep-linked-ads/enable-facebook-ad-partner/7-app-2.png)

1. Paste the app id and press `Save`

    ![paste app id](/images/ingredients/deep-linked-ads/enable-facebook-ad-partner/8-app-3.png)

1. Facebook is now enabled as an ad partner!

	Note that if you have different attribution windows between Facebook and Branch, those will be highlighted. The warning has a link to the docs on how to align these attribution windows.

    ![complete](/images/ingredients/deep-linked-ads/enable-facebook-ad-partner/9-complete.png)

1. Finally, to create a Facebook Ads link click the <notranslate>**Create Facebook Link**</notranslate> button in the top right hand corner.

    ![Create Facebook Ad Link](/images/ingredients/deep-linked-ads/enable-facebook-ad-partner/create-facebook-link.png)

## Create an Ad Link

[block:callout]
{
  "type": "info",
  "title": "Optional if Running App-Only Ads",
  "body": "This section is optional if you are running app-only ads. We will automatically pull in campaign, ad set, ad, and creative information from Facebook. However, if you want users to be deep linked, you should follow the instructions in this section."
}
[/block]

1. Create a Branch Ad link from the [Partner Management page](https://dashboard.branch.io/ads/partner-management)'s `Create Facebook Link` button under the Facebook Partner and select `Create Display Link`
![image](/images/pages/deep-linked-ads/reusable-images/create-link-display.png)
1. Under the Define Section, pick a Link Name for later reference.
1. Configure the link with the Ad Partner set to <notranslate>**Facebook**</notranslate>, and the Ad Format set to <notranslate>**Cross-platform Display**</notranslate>.
![Create Ad Link](/images/pages/deep-linked-ads/facebook-traffic-conversion-ads/link-setup.png)
1. Under the Configure Options tab, navigate to the Redirects sub section and ensure that the iOS/Android and Desktop redirects are set to the desired destinations being promoted by the ad campaign.
![Create Ad Link](/images/pages/deep-linked-ads/reusable-images/example-link-redirect.png)
1. Under the Analytics Tags sub section additional tags can be set. It is recommended to fill in these fields as they can be used as filters in Branch's Ads Analytics view. To best connect your ad link with your Adwords Campaign, set the channel field to Facebook Ads and set the campaign field to the same ad campaign name used in Facebook Ads.
![Analytics Tags](/images/pages/deep-linked-ads/reusable-images/facebook-analytics-tags.png)

[block:callout]
{
  "type": "warning",
  "title": "Disabling Deepviews",
  "body": "In order for your campaign to run effectively, be sure to disable Deepviews. You can either [disable Deepviews](/web/deep-views/#setup) for your entire account or [disable Deepviews for one link](/web/deep-views/#disable-per-link-deepviews)."
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "Optional: Deep Link Data",
  "body": "You can use this configuration section to specify custom link parameters that will be deep linked into the app after install. These could include a coupon code or a page identifier to route the user. Visit the [Deep Link Routing](/deep-linking/routing/) page to learn more."
}
[/block]

### Traffic Campaign Setup

#### Configure an Ad

To set up a Facebook Traffic campaign, you will need to first create your campaign and use a Branch link as the Deep Link URL for the advertisements. Facebook Traffic Campaign information is available **[here](https://www.facebook.com/business/ads-guide/traffic){:target="_blank"}**.

#### Create Your Campaign
1. Navigate to [https://www.facebook.com/ads/create](https://www.facebook.com/ads/create) while logged in to the account that owns your Facebook app.
1. Select <notranslate>**Traffic**</notranslate> as the campaign marketing objective.
![Campaign Selection](/images/pages/deep-linked-ads/facebook-traffic-conversion-ads/traffic/campaign-selection.png)
1. Select either to drive traffic to your `Website` or your `App`
1. Continue with campaign creation selecting the app to advertise, audience, placement, and budget. Then press continue to enter the Advert creation step.
1. Now select an advertisement format and customize your ad
1. Add your Branch Ad Link to your advertisement
	- If you chose to drive traffic to an App, locate the <notranslate>**Deep Link**</notranslate> field and copy and paste your Branch link there.

		![Campaign Selection](/images/pages/deep-linked-ads/facebook-traffic-conversion-ads/traffic/link-setup-app.png)

	- If you chose to drive traffic to a Website, paste your Branch Ad link into the <notranslate>**Website URL**</notranslate> field.

		![Campaign Selection](/images/pages/deep-linked-ads/facebook-traffic-conversion-ads/traffic/link-setup-web.png)

	- If you chose to drive traffic to a Website and are using a full-screen Canvas, add your Branch Ad link as the <notranslate>**Destination URL**</notranslate> for your canvas advertisement components.
1. Complete the rest of the ad campaign setup.

[block:callout]
{
  "type": "info",
  "title": "Optional: Ad formats with Multiple Links",
  "body": "Some ad formats such as Carousel format can handle multiple deep links. To have link performance data on each image or component of the advertisement, create multiple Branch Ad links to be used in each part of the multiple link advertisement format. This format is useful if you want to drive customers to different content pieces or products."
}
[/block]

### Conversions Campaign Setup

#### Configure an Ad

To set up a Facebook Conversions campaign, you will need to first create your campaign and use a Branch link as the Deep Link URL for the advertisements. Facebook Conversions Campaign information is available **[here](https://www.facebook.com/business/ads-guide/conversions){:target="_blank"}**.

[block:callout]
{
  "type": "warning",
  "title": "Prerequisites",
  "body": "As a prerequisite, Facebook requires you to report events about your users interacting with your content, for example: viewing, adding to cart, and purchasing. To add the Facebook Pixel to your website, and event tracking using the Branch SDK (which forwards to Facebook) to your app, follow these instructions:"
}
[/block]

	- [Sending App Events with the Branch SDK](/deep-linked-ads/facebook-ads-faq/#tracking-other-conversion-events)
	- [Sending Web Events with the Facebook Pixel](https://developers.facebook.com/docs/marketing-api/facebook-pixel/v2.8)

#### Create Your Campaign
1. Navigate to [https://www.facebook.com/ads/create](https://www.facebook.com/ads/create) while logged in to the account that owns your Facebook app.
1. Select <notranslate>**Conversions**</notranslate> as the campaign marketing objective.
![Campaign Selection](/images/pages/deep-linked-ads/facebook-traffic-conversion-ads/conversions/campaign-selection.png)
1. Select either to have the goal of having conversions on a `Website` or in an `App`
1. Continue with campaign creation selecting audience, placement, and budget. Then press continue to enter the Advert creation step.
1. Now select an advertisement format and customize your ad
1. Add your Branch Ad Link to your advertisement
	- If you chose app conversions App, locate the <notranslate>**Deep Link**</notranslate> field and copy and paste your Branch link there.

		![Campaign Selection](/images/pages/deep-linked-ads/facebook-traffic-conversion-ads/conversions/link-setup-app.png)

	- If you chose Website conversions, paste your Branch Ad link into the <notranslate>**Website URL**</notranslate> field.

		![Campaign Selection](/images/pages/deep-linked-ads/facebook-traffic-conversion-ads/conversions/link-setup-web.png)

	- If you chose Website conversions and are using a full-screen Canvas, add your Branch Ad link as the <notranslate>**Destination URL**</notranslate> for your canvas advertisement components.
1. Complete the rest of the ad campaign setup.

[block:callout]
{
  "type": "info",
  "title": "Optional: Ad formats with Multiple Links",
  "body": "Some ad formats such as Carousel format can handle multiple deep links. To have link performance data on each image or component of the advertisement, create multiple Branch Ad links to be used in each part of the multiple link advertisement format. This format is useful if you want to drive customers to different content pieces or products."
}
[/block]

### View Your Data

The [Ads Analytics Page](https://dashboard.branch.io/ads/analytics) on the Branch dashboard provides an interactive time series graph and table to view the performance of your Ad campaigns.

![Example Ads Analytics Graph](/images/ingredients/deep-linked-ads/view-ad-link-data/analytics-graph.png)

The table shows summary data on the performance of each Ad campaign. On the right top side of the table you can find a <notranslate>**download button**</notranslate> to retrieve the chart's content as a CSV file.

![Example Ads Table](/images/ingredients/deep-linked-ads/view-ad-link-data/analytics-table.png)

[block:callout]
{
  "type": "info",
  "title": "Interacting with your data",
  "body": "Breakdown and compare aspects of your Ad campaigns' performance by using the `Compare by +` button to add a parameter to split the data displayed data by."
}
[/block]

	Then use the `and +` button to refine the data displayed to gain deeper insight into the performance of your Ad campaigns.

## Troubleshooting

We now have a dedicated [FAQ page for Facebook app ads](/deep-linked-ads/facebook-ads-faq/#sources-of-discrepancies-between-facebook-and-branch). If you are having any issues with app ads, please review the FAQ.

If you are having issues with web-only ads, you can check out the FAQ. Then please [contact us](https://support.branch.io/support/tickets/new) and include "Facebook web-only ads issues" in the subject.
