## Overview

![XXX](https://cdn.branch.io/branch-assets/ad-partner-manager/388787843096400122/images-1527287333652.png)

This guide will walk you through how to setup your campaigns with **[XXX](https://XXX.com/)** using Branch Universal Ads and track ad conversions across **every device, platform, and channel**.



## Setup

### Integrating the SDKs and tracking in-app events

The Branch SDKs for iOS and Android allow you to get up and running quickly.

If you haven't already integrated Branch SDK into your application, please follow our integration guide to integrate Branch SDK into your application:

1. Documentation for [Android](/apps/android/)

1. Documentation for [iOS](/apps/ios/)

!!! warning "Limitations with setDebug and seeing data in Branch"
	When integrating the SDKs, it's often useful to use setDebug to verify that your app is able to communicate with Branch servers, and is receiving deep link data. However, our upstream systems don't register test events sent using setDebug, so events will not appear in Liveview or Analytics, nor will they fire postbacks. You should disable setDebug when looking at Liveview or testing postbacks.

#### Track conversion events

Install and open events are automatically tracked using just the Branch SDK integration. However, to track custom events, such as registration or purchase, you will need to integrate them into your application.

!!! warning "Sending event metadata from your application"
	Please make sure that you setup and pass event metadata from the application to the ad partner. Follow up with your ad partner to get the list of required parameters.

Please reference the general [V2 Event Tracking Guide](/apps/v2event/#overview). This will help ensure that you've integrated the right Branch events with the correct metadata.


!!! note "Testing your events with Liveview"
	You can test your integration by going to our [Liveview page](https://dashboard.branch.io/liveview/events){:target="\_blank"}. Set a filter with the event name to verify that the Branch SDK is recording each event.


### Enabling the Integration

1. Visit the [Ads page](https://dashboard.branch.io/ads) on the Branch dashboard.
2. Select [Partner Management](https://dashboard.branch.io/ads/partner-management) from the sidebar.
3. Search for your <notranslate>**Universal Ads Partner**</notranslate>.
4. Select Ad Partner Name and hit <notranslate>**Save & Enable**</notranslate>.

![image](/_assets/img/pages/deep-linked-ads/XXX/XXX-enable.png)

{! ingredients/deep-linked-ads/add-credentials.md !}

!!! tip "Enable postbacks"
    Basic postbacks will automatically be activated for events like _Install_ and _Purchase_ when you enable your ad partner. You can then [add additional postbacks](#adding-more-postbacks), for example, if you wanted to add postbacks for custom events that are specific to your app like _Account Created_. You can also [edit postbacks](#advanced-editing-postbacks) if there's additional data you really need to pass along to your ad partner.

![image](/_assets/img/pages/deep-linked-ads/XXX/XXX-postbacks.png)

### Creating an ad link

Once you've enabled an integration it's time to create a tracking link.

1. First, select an ad format. For App Install or App Engagement campaigns you'll want to select the <notranslate>**App Only**</notranslate> format. For Search or Display campaigns where the user should go to web if they don't have the app, then you should select <notranslate>**Cross-Platform Search**</notranslate> or <notranslate>**Cross-Platform Display**</notranslate>. <notranslate>**Product Links**</notranslate> are for shopping or dynamic remarketing campaigns.

    ![image](/_assets/img/pages/deep-linked-ads/branch-universal-ads/create-link.png)

1. At this point you need to name your link. Select something that will make it easy to find if you need it later. Your Ad Format and Ad Partner should be selected already, but feel free to choose one if they aren't. It's important that you select the right Ad Partner for analytics later on. Click <notranslate>**Configure Options**</notranslate> to continue.

    ![image](/_assets/img/pages/deep-linked-ads/branch-universal-ads/create-link-name.png)

1. This is your chance to add deep link data and analytics tags. Analytics tags are important for later segmentation, so click the <notranslate>**Analytics**</notranslate> sub tab to add a Channel and Campaign value.

    ![image](/_assets/img/pages/deep-linked-ads/branch-universal-ads/create-link-tags.png)

    !!! tip "Set Analytics tags"

        It's easier to slice your data in our analytics platform if you properly assign analytics parameters to your link. <notranslate>_Channels_</notranslate> generally correspond to ad networks, and <notranslate>_Campaigns_</notranslate> correspond to marketing initiatives that you're launching. For example: <notranslate>_Channel_</notranslate>: "YouTube", <notranslate>_Campaign_</notranslate>: "Summer 2017 Shoe Discounts."

    !!! info "Links Created by Agency Users"
        When an Agency users saves an ad link/Journey/Quick Link, that ad link/Journey/Quick Link is associated with that Agency via a unique agency_id that is included as a key-value in deep linking setup.


1. Click <notranslate>**Create Link Now**</notranslate>, and you have your tracking link! Take this link and give it to your Ad Partner's Account Manager or paste it into the tracking section of your campaign yourself.

    ![image](/_assets/img/pages/deep-linked-ads/branch-universal-ads/create-link-completed.png)


### Viewing Your Data

The Ads Analytics Page on the Branch dashboard provides an interactive time series graph and table to view the performance of your Ad campaigns:

- Easily interact with your Analytics data breakdown and compare aspects of your Ad campaigns' performance by using the <notranslate>**Compare by**</notranslate> button to add a parameter to split the data displayed data by.
- You can also use the <notranslate>**Add Filter +**</notranslate> button to refine the data displayed to gain deeper insight into the performance of your Ad campaigns.

The <notranslate>**TRENDS**</notranslate> table shows the chart and breakdown of last 7 days data on the campaign performance by ad partner.

![Example Ads Analytics Graph](/_assets/img/ingredients/deep-linked-ads/view-ad-link-data/trends-graph.png)

The <notranslate>**EVENTS**</notranslate> table shows summary data on the performance of each Ad campaign.

![Example Ads Table](/_assets/img/ingredients/deep-linked-ads/view-ad-link-data/events-table.png)

On the top right side of the table you can find a download button to retrieve the chart's content as a CSV file.  For more info about Ads Analytics refer [here](/activity-reports-analytics/paid-ads-analytics/).

#### View your data with People-Based Attribution

The [Ads Analytics Page](https://dashboard.branch.io/ads/analytics) on the Branch dashboard shows the performance of your ad campaigns _across both web and app_. You can view performance over time, including purchase and other custom events.

Events are attributed using Branch's unified last-click attribution model. This means that Branch will attribute to the last click across channels, and across platforms.

For example, if a customer clicks a Branch email link, and then clicks an ad, installs the the app and purchases an item, Branch will attribute the install and the purchase to the last clicked ad link.

If the customer then goes on to purchase an item on web within the attribution window, Branch will also attribute the web purchase to the same ad link, connecting the web and app actions taken by a single user for a more accurate view of your marketing channels and customer behavior.

![image](/_assets/img/pages/deep-linked-ads/branch-universal-ads/install-by-secondary-pub.png)

You can read more about [People-Based Attribution here](/dashboard/people-based-attribution/).


#### View-Through Attribution (VTA) with Impression Pixels

View-through attribution allows you to track installs, session starts and conversion events back to an ad impression, even if the ad was never clicked on.

Our view-through attribution logic is currently as follows for any given event:

- If there's a click within a valid attribution window, give credit to the click.
- If there's no click within a valid attribution window, give credit to the last impression that was within a valid attribution window.

Currently, view through attribution is supported for Self Attributing Networks (SANs), such as Facebook and Google, and non-SAN networks with server to server impression link support. To create a impression tracking link for non-SAN networks, simply [create an ad link](#create-an-ad-link), and grab the impression link from the final step of link creation. SAN networks support VTA without any additional links.


## Advanced

#### Adding/Enabling More Postbacks

Basic postbacks are automatically activated for events like _Install_ and _Purchase_ when you enable your ad partner. You can then add additional postbacks, for example, if you wanted to add postbacks for custom events that are specific to your app like _Account Created_.

To add a postback:

1. Under <notranslate>**Partner Management**</notranslate>, select the partner for whom you want to add/edit their postback.
2. Click on the <notranslate>**Postback Config**</notranslate> tab on said partner’s page.
3. Click the <notranslate>**Add New Postback**</notranslate> button at the bottom of the screen.
4. A modal will appear with Branch default events, as well as any commerce (reserved events like _PURCHASE)_ or custom events you've set up. Select an event, enter a postback URL if you're asked to, and click <notranslate>**Save**</notranslate>. This will be the event that triggers your new postback.
    1. NOTE: If Branch does not already have a postback template for a partner, please provide a valid URL for your partner.

![image](/_assets/img/pages/partner-management/postback-add.gif)

#### Sending All Events

If you want to send <notranslate>**All Events**</notranslate> - whether attributed to this partner or not  - you can enable this setting by checking the <notranslate>**All Events**</notranslate> box on a per postback basis.

!!! warning "Privacy Implications"
	As this setting will send <notranslate>**All Events**</notranslate> - with the name and customer event alias listed in this row, whether attributed to this partner or not - we recommend using caution when/if enabling, especially if you have enabled agencies to access your account.

![image](/_assets/img/pages/deep-linked-ads/branch-universal-ads/all-events.png)


#### Editing Templates

In most cases, the default postback URL generated from your selections is sufficient to provide postback notification to interested parties.

But sometimes you may need/want to edit or remove a parameter from the postback URL, or append a macro expression/variable to include additional information.

!!! tip "Example"
	You want to send your partner the actual items a user adds to their cart so they can optimize based off those items.  Their current <notranslate>**Add to Cart**</notranslate> postback template does not include this information.  Therefore, you need to add [Content Items](https://docs.branch.io/resources/postback-macros-and-functions/#content-items-data) macros to their URL. To do so, you’ll first need to get the correct field from the partner in which to pass this data; e.g. `cart_items`.  Finally, you’d append `&cart_item=${(content_items[0].$product_name)!}` to the postback template.

Please refer to [Postback Macros & Functions](#postback-macros-functions) when looking to append additional macros.

To edit the postback template:

1. Under <notranslate>**Partner Management**</notranslate>, select the partner for whom you want to add/edit their postback.
2. Click on the <notranslate>**Postback Config**</notranslate> tab on said partner’s page.
3. In the <notranslate>**Postback URL**</notranslate> field, add/edit/remove the key-value pairs necessary.
    1. You must include a `&` before each key-value pairs you append.
4. Click <notranslate>**Save**</notranslate>.
5. Alternatively, hover on the three dots icon to the right of the postback and click <notranslate>**Advanced Edit**</notranslate>.
6. In the <notranslate>**Send a Webhook to**</notranslate> field, add/edit/remove the key-value pairs necessary.
    2. You must include a `&` before each key-value pairs you append.
7. Click <notranslate>**Save**</notranslate>.

!!! tip "Reset Postbacks"
    We all make mistakes from time to time. If you need to reset your postbacks and your credentials, navigate to the <notranslate>**Account Settings**</notranslate> tab and look for the <notranslate>**Reset all settings**</notranslate> button. Be careful though! This will disable the ad partner, clear out all credentials and postbacks that you've set up, and return the ad partner to its basic configuration. You can then start afresh.


Branch Tracking links allow tracking many parameters about the performance of your ad campaigns and individual ads. You can see each partner's specific link Parameters under the <notranslate>**Link Parameters**</notranslate> tab:

![image](/_assets/img/ingredients/deep-linked-ads/link-parameters.png)

Additional parameters for advanced analysis may be added to the link after the '?' or '&' character, to trace extra information.

!!! tip "Example Tracking Link with Additional Parameters"
    Example Branch link including additional parameters to pass Agency and Sub Publisher information:`https://tracking.app.link?$3p=a_partner&~agency=myAgency&~secondary_publisher=best_publisher`

The following parameters are available to use within the pre-generated tracking link:

#### Campaign Information

Branch Parameter | Description
--- | ---
`~agency` | Agency name
`~secondary_publisher` | Sub Publisher
`~campaign` | Campaign name
`~campaign_id` | Campaign ID
`~channel` | Channel
`~feature` | Feature
`~stage` | Stage
`~tags` | Tags
`~creative_name` | Creative name
`~creative_id` | Creative ID
`~ad_set_name` | Ad set name
`~ad_set_id` | Ad set ID
`~ad_name` | Ad unit name
`~ad_id` | Ad unit ID
`~banner_dimensions` | Banner Dimension
`~placement` | Placement
`~keyword_id` | Keyword ID
`~keyword_text` | Keyword Text

#### Device Information

Branch Parameter | Description
--- | ---
`%24aaid` | Google AAID
`%24idfa` | Apple IDFA

#### Spend Calculation

!!! info "Cost Data Availability"
    Cost data passed via these macros is available in exports but is not visible in the Branch dashboard.

Branch Parameter | Description
--- | ---
`~cost_model` | Cost Model; e.g. CPI, eCPC
`~cost_value` | Cost Value; e.g. 10.00
`~cost_currency` | Cost Currency; e.g. USD


#### Changing Attribution Windows

Attribution windows can be specified at the global account level or on a per link basis with the link level window taking priority. See the below instructions for setup.

For customer experience and data accuracy, please do not set your deep linking window longer than the other attribution windows.

#### Account Level Attribution Windows

You can edit your attribution windows under Link Settings > Attribution Windows.

   ![image](/_assets/img/pages/dashboard/people-based-attribution/attribution-windows.png)

Learn more about account level attribution windows in [People-Based Attribution](/dashboard/people-based-attribution/#attribution-windows).

#### Ad Network Attribution Windows

You can edit your attribution windows at the ad network level, if your ad network requires it. This is recommended when you enable networks like Facebook and Google, who may have different windows for installs. With this, you can preserve your Account Level Attribution Windows, as well.

   ![image](/_assets/img/pages/deep-linked-ads/branch-universal-ads/anaw_clear.png)

#### Link Level Attribution Windows

To set attribution windows on a link level, you can append the following parameters to your generated Branch link.

Key | Example Link
--- | ---
`$click_install_window_days`| https://branchster.app.link/hpNVE52gxE?$click_install_window_days=3
`$click_session_start_window_days` | https://branchster.app.link/hpNVE52gxE?$click_session_start_window_days=7
`$click_conversion_window_days` | https://branchster.app.link/hpNVE52gxE?$click_session_start_window_days=30
`$impression_install_window_days`| https://branchster.app.link/hpNVE52gxE?$impression_install_window_days=3
`$impression_session_start_window_days` | https://branchster.app.link/hpNVE52gxE?$impression_session_start_window_days=1
`$impression_conversion_window_days` | https://branchster.app.link/hpNVE52gxE?$impression_session_start_window_days=7

!!! warning "Link Level Attribution Support for Standard Branch links"
    As of July 2017, link level attribution window setting is only available on standard Branch links. Special Branch links such as the ones used for Google's Universal App Campaign or Play Store links with Branch link id parameters are currently not supported.


{! ingredients/deep-linked-ads/reset-ad-settings.md !}

{! ingredients/deep-linked-ads/support.md !}
