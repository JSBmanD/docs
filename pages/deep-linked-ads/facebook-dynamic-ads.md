---
title: Facebook Dynamic Ads
---
## Overview

Branch links can be used in conjunction with Facebook's dynamic advertisements. Dynamic remarketing campaigns on desktop have been proven to deliver 16x return on ad spend. Now you can easily set up Facebook Dynamic Ads on mobile to drive incredible results.

Note: This documentation applies for Ad placements across Facebook and the Audience Network.

This documentation supports the following Facebook Ad Campaign types:

Facebook Campaign Category | Campaign Type/Objective | Branch Ad Format
--- | --- | ---
Conversion | Product Catalogue Sales | Cross-platform Product Links

#### Facebook Campaign Advert Format Support Table

Facebook Campaign Type | Photo | Video | Carousel | Slideshow | Collection | Dynamic | Canvas
--- | --- | --- | --- | --- | --- | --- | ---
Product Catalogue Sales | ✔︎ |  | ✔︎ |  |  |  |

[block:callout]
{
  "type": "info",
  "title": "Facebook Campaign Types",
  "body": "Looking for other Facebook Ad campaign types? Please check out our [Facebook Ads Overview guide](/deep-linked-ads/facebook-ads-overview)."
}
[/block]

[block:callout]
{
  "type": "warning",
  "title": "Prerequisites",
  "body": "
	* [x] To track installs from Facebook Ads you should [integrate the Branch SDK](/apps/ios/#integrate-branch) into your app.
	* [x] To use Branch links in Facebook App Install Ads ensure you have Universal Links set up on iOS or App Links enabled on Android to ensure correct routing behavior. For setup, checkout [Universal](/deep-linking/universal-links/) and [App Links](/deep-linking/android-app-links/).
	* [x] If you want to deep link from your ads directly to content, you should [configure deep link routing](/deep-linking/routing/).
	* [x] [Create Branch Links for Product Feeds](/deep-linked-ads/creating-branch-links-for-product-feeds/) to create your Facebook Dynamic Ad compatible deep links.
	* [x] Ads is a premium product priced on Monthly Active Users. Sign up for the Ads product to enable this functionality."
}
[/block]

#### Enable Facebook as an Ad Partner (for measurement)

[block:callout]
{
  "type": "info",
  "title": "Enabling Facebook as an Ad Partner",
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


## Setup

#### Create a Deep Linked Ad Feed

Branch makes it easy for you to create and manage feeds with Facebook-compatible deep links.

1. Create a Branch Deep Linked Ad Feed from the [Partner Management page](https://dashboard.branch.io/ads/partner-management)'s `Create Ad Link` button under the Facebook Partner and select `Create Product Link`
![image](_assets/img/pages/deep-linked-ads/reusable-images/create-link-product.png)
1. Enter a Deep Linked Feed Name.
1. Enter a already set up feed source or upload a new source.
1. Configure the feed with the Ad Partner set to <notranslate>**Facebook**</notranslate>, and the Ad Format set to <notranslate>**Product**</notranslate>.
![Ad Link Setup](/images/pages/deep-linked-ads/facebook-dynamic-ads/feed-setup.png)
1. On the next section, select any keys from your feed that you'd like to include in the deep linked data contained in the generated links.
![image](/images/pages/deep-linked-ads/facebook-dynamic-ads/feed-keys-setup.png)
1. If you used a Feed Source hosted on a URL (recommended), you will see two options for accessing your feed. We recommend selecting “Schedule Refresh.” If you select this option, Branch will host a URL for your Deep Linked Feed that will update itself from your Feed Source URL at regular intervals.
![image](/images/pages/deep-linked-ads/facebook-dynamic-ads/hosted-dlf.png)
1. Download the feed data or copy the deep linked feed URL (for hosted feeds) to be used in your Ad Campaign.

#### Upload your feed to Facebook

To set up a Facebook Product Catalogue campaign, you will need to first create your campaign and use a Branch link as the Deep Link URL for the advertisements. Facebook Dynamic Ads information is available **[here](https://www.facebook.com/business/help/455326144628161){:target="_blank"}**.

[block:callout]
{
  "type": "info",
  "title": "Feed Sources",
  "body": "
	Branch accepts Feed Sources that are compatible with Facebook’s [feed format](https://developers.facebook.com/docs/marketing-api/dynamic-product-ads/product-catalog#feed-format). Please use [Facebook’s Product Feed Debug Tool](https://business.facebook.com/ads/product_feed/debug) to test and debug your Product Feed format.

	While Branch requires you have at least a column for the field `link` in your Feed Source containing the link to the merchant's site where the item can be bought, Facebook requires several more fields. Please make sure you've included all of [these fields](https://developers.facebook.com/docs/marketing-api/dynamic-product-ads/product-catalog#required-fields) in your product feed.

	The largest file size accepted by the tool is 50MB. Please contact [integrations@branch.io](mailto:integrations@branch.io) if you need to upload a larger file."
}
[/block]

1. Navigate to your [Facebook Ads Manager](https://www.facebook.com/ads/manager/).
1. In the top left hand corner, click into the menu, select <notranslate>**All tools**</notranslate>, and select <notranslate>**Product Catalogues**</notranslate>.
![Facebook Product Catalogues](/images/pages/deep-linked-ads/facebook-dynamic-ads/fb-product-catalogs.png)
1. From the drop down menu click "Create new catalog...", name it (remember this name, you'll need it later) and select <notranslate>"Products sold online"</notranslate>.
![image](/images/pages/deep-linked-ads/facebook-dynamic-ads/create-new-catalog.png)
1. Now that you have a product catalog, you can add a new feed. Click "Add Product Feed."
![Add New Feed](/images/pages/deep-linked-ads/facebook-dynamic-ads/add-new-feed.png)
1. If you have a [Hosted Deep Linked Feed](/features/deep-linked-feeds/guide/#schedule-refresh) (recommended), select the option "Scheduled recurring uploads." Paste your Branch-provided URL into the <notranslate>**Feed URL**</notranslate> text field.
![Feed URL option](/images/pages/deep-linked-ads/facebook-dynamic-ads/new-feed-settings.png)
![Feed URL settings](/images/pages/deep-linked-ads/facebook-dynamic-ads/upload-feed-url.png)
1. If you've created a Deep Linked Feed CSV file to upload, select the option "Single upload: Upload a single file feed now." Select the Deep Linked Feed URL or CSV file you would like to upload to Facebook, and click "Upload".
![Feed Uploaded](/images/pages/deep-linked-ads/facebook-dynamic-ads/successful-feed-upload.png)
1. Wait for the upload to complete successfully. If you'd like to create a <notranslate>"Product set"</notranslate> (a subset of products in your catalog for use in specific ad sets) you can do that now.

#### Setting up App Events and the Facebook Pixel

Facebook requires you to report events about your users interacting with your content, for example: viewing, adding to cart, and purchasing. To add the Facebook Pixel to your website, and event tracking using the Branch SDK (which forwards to Facebook) to your app, follow these instructions:

- [Sending App Events with the Branch SDK](/deep-linked-ads/facebook-ads-faq/#tracking-other-conversion-events)
- [Sending Web Events with the Facebook Pixel](https://developers.facebook.com/docs/marketing-api/facebook-pixel/v2.8)

Use the <notranslate>"Product events"</notranslate> tab in your Product Catalog view to ensure that Facebook is registering the events against your Product Catalog items correctly.

#### Creating a Dynamic Ad Campaign

1. Navigate to [https://www.facebook.com/ads/create](https://www.facebook.com/ads/create) while logged in to the account that owns your Facebook app.
1. Choose <notranslate>**Product Catalog Sales**</notranslate>. Select the Product Catalog to which you uploaded your Deep Linked Feed.
![Feed Uploaded](/images/pages/deep-linked-ads/facebook-dynamic-ads/campaign-selection.png)
1. Select the targeting, bid, budget and placements that you'd like.
1. Select your desired ad format and launch your campaign. The Branch deep linked feed will be automatically set up in your Facebook product catalogue ads.

[block:callout]
{
  "type": "info",
  "title": "Driving Installs with Dynamic Ads",
  "body": "By default, Facebook sends customers without the app to your mobile website. To drive installs, you can send customers without your app the app store by adding a `web_should_fallback` column to your Feed Source and setting each row to `false`. Then, after you've created your campaign, edit the ad within your ad set. Under "Creative," set your "App link destination" to "Deep link, app store backup.""
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
