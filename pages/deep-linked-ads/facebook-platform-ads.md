---
title: Facebook Platform Ads
---
## Overview

Branch links can be used together with a variety of Facebook ads, allowing you to track ad performance on the Branch dashboard and to deep link new users from ad-driven installs directly to content the first time they open your app.

Note: This documentation applies for Ad placements across Facebook and the Audience Network.

This documentation supports the following Facebook Ad Campaign types:

Facebook Campaign Category | Campaign Type/Objective | Branch Ad Format
--- | --- | ---
Awareness | Brand Awareness | Cross-platform Display
Awareness | Reach | Cross-platform Display
Consideration | Video Views | Cross-platform Display
Consideration | Lead Generation | Cross-platform Display

#### Facebook Campaign Advert Format Support Table

Facebook Campaign Type | Photo | Video | Carousel | Slideshow | Collection | Dynamic | Canvas
--- | --- | --- | --- | --- | --- | --- | ---
Brand Awareness | ✔︎ | ✔︎ | ✔︎ | ✔︎ |  |  | ✔︎
Reach | ✔︎ | ✔︎ | ✔︎ | ✔︎ |  |  | ✔︎
Video Views |  | ✔︎ | ✔︎ | ✔︎ |  |  | ✔︎
Lead Generation | ✔︎ | ✔︎ | ✔︎ | ✔︎ |  |  |

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
  "body": "
	* [x] To track installs from Facebook Ads you should [integrate the Branch SDK](/apps/ios/#integrate-branch) into your app.
	* [x] To use Branch links in Facebook App Install Ads ensure you have Universal Links set up on iOS or App Links enabled on Android to ensure correct routing behavior. For setup, checkout [Universal](/deep-linking/universal-links/) and [App Links](/deep-linking/android-app-links/).
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


#### Create an Ad Link

1. Create a Branch Ad link from the [Partner Management page](https://dashboard.branch.io/ads/partner-management)'s <notranslate>**Create Facebook Link**</notranslate> button under the Facebook Partner and select <notranslate>**Create Display Link**</notranslate> or <notranslate>**Create Display Link**</notranslate> depending on your campaign type.
![image](/images/pages/deep-linked-ads/reusable-images/create-link-display.png)
1. Pick a Link Name for later reference.
1. Configure the link the Ad Partner set to <notranslate>**Facebook**</notranslate> and the Ad Format set to <notranslate>**Cross-Platform Display**</notranslate> or <notranslate>**Cross-platform Display**</notranslate>.
![Create Ad Link](/images/pages/deep-linked-ads/facebook-platform-ads/link-setup.png)
1. Under the Configure Options tab, navigate to the Redirects sub section and ensure that the iOS/Android and Desktop redirects are set to the desired destinations being promoted by the ad campaign.
![Create Ad Link](/images/pages/deep-linked-ads/reusable-images/example-link-redirect.png)
1. Under the Analytics Tags sub section additional tags can be set. It is recommended to fill in these fields as they can be used as filters in Branch's Ads Analytics view. To best connect your ad link with your Facebook Campaign, set the channel field to Facebook Ads and set the campaign field to the same ad campaign name used in Facebook Ads.
![Analytics Tags](/images/pages/deep-linked-ads/reusable-images/facebook-analytics-tags.png)

[block:callout]
{
  "type": "warning",
  "title": "Disabling Deepviews",
  "body": "In order for your campaign to run effectively, be sure to disable Deepviews. You can either [disable Deepviews](/web/deep-views/) for your entire account or [disable Deepviews for one link](/web/deep-views/)."
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "Optional: Deep Link Data",
  "body": "You can use this configuration section to specify custom link parameters that will be deep linked into the app after install. These could include a coupon code or a page identifier to route the user. Visit the [Deep Link Routing](/deep-linking/routing/) page to learn more."
}
[/block]

### Brand Awareness Campaign Setup

#### Configure an Ad

To set up Facebook Brand Awareness Campaigns, you will need to insert your Branch Ad Link as the Website destination for the created ad. Facebook's Ad guide for Brand Awareness Campaigns is available **[here](https://www.facebook.com/business/ads-guide/brand-awareness){:target="_blank"}**.

#### Create Your Campaign
1. Navigate to [https://www.facebook.com/ads/create](https://www.facebook.com/ads/create) while logged in to the account that owns your Facebook app.
1. Select <notranslate>**Brand Awareness**</notranslate> as the campaign marketing objective.
![Campaign Selection](/images/pages/deep-linked-ads/facebook-platform-ads/brand-awareness/campaign-selection.png)
1. Continue with campaign creation selecting the app to advertise, audience, placement, and budget. Then press continue to enter the Advert creation step.
1. Now select an advertisement format and customize your ad
1. Now add your Branch link to your advertisement
    - Select the <notranslate>**Add a Website URL**</notranslate> checkbox and copy your Branch Ad Link into the <notranslate>**Website URL**</notranslate> field.

	![Deep Link Placement](/images/pages/deep-linked-ads/facebook-platform-ads/brand-awareness/ad-deep-link.png)

    - If you selected to add a full screen Canvas advertisement, add your Branch Ad link as the <notranslate>**Destination URL**</notranslate> for your canvas advertisement components
1. Complete the rest of the ad campaign setup.

[block:callout]
{
  "type": "info",
  "title": "Optional: Ad formats with Multiple Links",
  "body": "Some ad formats such as Carousel format can handle multiple deep links. To have link performance data on each image or component of the advertisement, create multiple Branch Ad links to be used in each part of the multiple link advertisement format. This format is useful if you want to drive customers to different content pieces or products."
}
[/block]

### Reach Campaign Setup

#### Configure an Ad

To set up Facebook Reach Campaigns, you will need to insert your Branch Ad Link as the Website destination for the created ad. Facebook's Ad guide for Reach Campaigns is available **[here](https://www.facebook.com/business/ads-guide/reach){:target="_blank"}**.

#### Create Your Campaign
1. Navigate to [https://www.facebook.com/ads/create](https://www.facebook.com/ads/create) while logged in to the account that owns your Facebook app.
1. Select <notranslate>**Reach**</notranslate> as the campaign marketing objective.
![Campaign Selection](/images/pages/deep-linked-ads/facebook-platform-ads/reach/campaign-selection.png)
1. Continue with campaign creation selecting the app to advertise, audience, placement, and budget. Then press continue to enter the Advert creation step.
1. Now select an advertisement format and customize your ad
1. Now add your Branch link to your advertisement
    - Select the <notranslate>**Add a Website URL**</notranslate> checkbox and copy your Branch Ad Link into the <notranslate>**Website URL**</notranslate> field.

	![Deep Link Placement](/images/pages/deep-linked-ads/facebook-platform-ads/reach/ad-deep-link.png)

    - If you selected to add a full screen Canvas advertisement, add your Branch Ad link as the <notranslate>**Destination URL**</notranslate> for your canvas advertisement components
1. Complete the rest of the ad campaign setup.

[block:callout]
{
  "type": "info",
  "title": "Optional: Ad formats with Multiple Links",
  "body": "Some ad formats such as Carousel format can handle multiple deep links. To have link performance data on each image or component of the advertisement, create multiple Branch Ad links to be used in each part of the multiple link advertisement format. This format is useful if you want to drive customers to different content pieces or products."
}
[/block]

### Video Views Campaign Setup

#### Configure an Ad

To set up Facebook Video Views Campaigns, you will need to insert your Branch Ad Link as the Website destination for the created ad. Facebook's Ad guide for Video Views Campaigns is available **[here](https://www.facebook.com/business/ads-guide/video-views/){:target="_blank"}**.

#### Create Your Campaign
1. Navigate to [https://www.facebook.com/ads/create](https://www.facebook.com/ads/create) while logged in to the account that owns your Facebook app.
1. Select <notranslate>**Video Views**</notranslate> as the campaign marketing objective.
![Campaign Selection](/images/pages/deep-linked-ads/facebook-platform-ads/video-views/campaign-selection.png)
1. Continue with campaign creation selecting the app to advertise, audience, placement, and budget. Then press continue to enter the Advert creation step.
1. Now select an advertisement format and customize your ad
1. Now add your Branch link to your advertisement
    - Select the <notranslate>**Add a Website URL**</notranslate> checkbox and copy your Branch Ad Link into the <notranslate>**Website URL**</notranslate> field.

	![Deep Link Placement](/images/pages/deep-linked-ads/facebook-platform-ads/video-views/ad-deep-link.png)

    - If you selected to add a full screen Canvas advertisement, add your Branch Ad link as the <notranslate>**Destination URL**</notranslate> for your canvas advertisement components
1. Complete the rest of the ad campaign setup.

[block:callout]
{
  "type": "info",
  "title": "Optional: Ad formats with Multiple Links",
  "body": "Some ad formats such as Carousel format can handle multiple deep links. To have link performance data on each image or component of the advertisement, create multiple Branch Ad links to be used in each part of the multiple link advertisement format. This format is useful if you want to drive customers to different content pieces or products."
}
[/block]

### Lead Generation Campaign Setup

#### Configure an Ad

To set up Facebook Lead Generation Campaigns, you will need to insert your Branch Ad Link as the Website destination for the created ad. After users fill out the lead form, they'll be directed to your website or app after through the Branch Ad link. Facebook's Ad guide for Lead Generation Campaigns is available **[here](https://www.facebook.com/business/ads-guide/lead-generation){:target="_blank"}**.

#### Create Your Campaign
1. Navigate to [https://www.facebook.com/ads/create](https://www.facebook.com/ads/create) while logged in to the account that owns your Facebook app.
1. Select <notranslate>**Lead Generation**</notranslate> as the campaign marketing objective.
![Campaign Selection](/images/pages/deep-linked-ads/facebook-platform-ads/lead-generation/campaign-selection.png)
1. Continue with campaign creation selecting the app to advertise, audience, placement, and budget. Then press continue to enter the Advert creation step.
1. Now select an advertisement format and customize your ad
1. Enter the Lead form creation portal and setup your form.
1. On the final <notranslate>"Thank you"</notranslate> screen, locate and paste your Branch Ad Link into the <notranslate>**Website link**</notranslate> field.
![Campaign Selection](/images/pages/deep-linked-ads/facebook-platform-ads/lead-generation/ad-deep-link.png)
1. Complete the rest of the ad campaign setup.

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
