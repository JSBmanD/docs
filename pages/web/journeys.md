---
title: Journeys App Banners
---
## Overview

On a daily basis, Google Search drives **more app installs** than all of Facebook's paid install products combined. Converting your mobile web visitors into native app users is one of the most effective acquisition channels available, and Branch's Journeys App Banners platform makes this easy.

![image](/_assets/img/pages/journeys/journeys-examples.png)

- **Customizable presentation.** WYSIWYG designer for smart banner or full-page interstitial, with more coming soon.
- **Powerful targeting rules.** Want to show your Journey only visitors without your app installed already? All iOS users from Japan? Just users viewing your checkout page? Android users who have visited your website twice AND purchased something using your app? The possibilities are infinite.
- **AMP-compatible.** You can convert mobile search traffic to your app by [showing Journeys on AMP pages](/web/amp-journeys/).
- **Run A/B tests.** Design multiple campaign versions to see which converts most effectively.
- **Optimized user experience.** If installed, your app will open and users can be routed directly to the content they expect. If not, the App/Play store will open and users can still be routed directly to the content they expect after installing.
- **Comprehensive analytics.** Measure the downstream performance and retention of every Journeys campaign.


!!! note "Paid Product"
    Journeys is a premium product priced on Monthly Active Users. [Sign up](https://branch.io/journeys/) for the Journeys product to enable this functionality.

!!! note "Pre-reqs"
    You should integrate the Branch SDK into your app and configure deep link routing for deferred deep linking and attribution before implementing Journeys.

## Setup

!!! note "Include your alternate domain for Universal Links"
    Journeys uses your alternate domain for Universal Links. Make sure you include your `xxxx-alternate.app.link` domain in your [Associated Domains](/apps/ios/#configure-associated-domains). If you use a custom domain or subdomain for your Branch links, you should instead add entries for `applinks:[mycustomdomainorsubdomain]` and `XXXX-alternate.app.link`. If you’re unsure of your Branch-assigned app.link subdomain, [contact support](https://support.branch.io), and we can provide it.

### Add the Branch Web SDK to your site

Add the following code somewhere inside the `<head></head>` tags on your website. We recommend loading the SDK as early as possible for optimal Journeys performance. More information about this SDK can be found in the [Github README](https://github.com/BranchMetrics/web-branch-deep-linking).

```html
<script type="text/javascript">
{! partials/web-sdk-init.md !}
</script>
```

{! partials/replace-branch-key.md !}

!!! note "GDPR considerations"
    In order to help our customers comply with [GDPR](https://branch.io/gdpr/), and other laws that restrict data collection from certain users, we’ve updated our Web SDK with a [Do Not Track mode](/web/integrate/#enable-do-not-track-mode). This way, if a user indicates that they want to remain private on your website, or if you otherwise determine that a particular user should not be tracked, you can continue to make use of the Branch Web SDK (e.g. for creating Branch links) while not tracking that user. This setting can also be enabled across all users for a particular link, or across your Branch links. Click [here](/web/journeys/#journeys-and-gdpr) for information on how this mode impacts Journeys.


### Deep linking from the banner or interstitial

Like all Branch deep links, you can pass custom parameters by specifying keys in the link's [data dictionary](/links/integrate/#configure-deep-links). This is useful if you are showing the Smart Banner on a website page with equivalent in-app content, because you can route directly to that content in your app.

This example will take the visitor straight to a picture with id “12345” after installing and opening the app.

```javascript
branch.setBranchViewData({
    data: {
        '$deeplink_path': 'picture/12345',
        'picture_id': '12345',
        'user_id': '45123'
    }
});
```


Alternatively, you can dynamically specify the deep link path depending on which website page is loaded.

```javascript
branch.setBranchViewData({
    data: {
        '$deeplink_path': window.location.pathname + window.location.search + window.location.hash,
        'user_id': '45123'
    }
});
```

If a user is referred to a page running Journeys via a Branch link, then referring link data will be passed into the Journeys call-to-action by default. If you’re using setBranchViewData() to specify link data for Journeys on that page, the only data from setBranchViewData() that will be used are [dynamic Journeys layout parameters](/web/journeys/#dynamic-journeys-layout-customization); all other data in that call will be ignored, unless `make_new_link` is set to `true` in `branch.init()`. You can find more information [here](/web/journeys/#preserve-or-discard-referring-link-data).

### Create Journey banner or interstitial

1. Head to the [Journeys page](http://dashboard.branch.io/journeys) on the Branch dashboard.
2. Click the <notranslate>**Create New Journey**</notranslate> button to get started.

![image](/_assets/img/pages/journeys/create-journey-button.png)

3. In the <notranslate>**Journey Name:**</notranslate> field, enter a name to use for internal reference (this will never be shown to your users).

![image](/_assets/img/pages/journeys/journeys-name.png)

### Select audience

You can customize the audience that will see your Journey by choosing target platforms and device types, and by adding additional targeting rules.

![image](/_assets/img/pages/journeys/journeys_select_audience.png)

| Option | Description |
| --- | --- |
| <notranslate>Platform</notranslate> | Branch currently offers Journeys on one platform: **Mobile web**. This will display for mobile users on your website. _More options coming soon._
| <notranslate>Devices</notranslate> | Which devices would you like to target? For example, if you only have an iOS app, then you might want to show a Journey only to users viewing your mobile website on iOS.
| <notranslate>Additional Filters</notranslate> | Read about advanced filtering criteria [here](/web/journeys/#advanced-audience-rules).

### Select and style the banner or interstitial

1. First, click the <notranslate>**Select a Template**</notranslate> button. ![image](/_assets/img/pages/journeys/select-template.png)
1. Next, click to select the type of template that you want to show. There are three template options:
    - Smart Banner at bottom of screen.
    - Smart Banner at top of screen
    - Full Screen Interstitial (SEO friendly!)
    - _The fourth option shown is an alternate preconfiguration of the full screen interstitial_![image](/_assets/img/pages/journeys/select-template-type.png)
1. Click <notranslate>**Customize**</notranslate> to make changes to the template.
1. In the <notranslate>**Customize Template**</notranslate> heading, you may edit the the name to use for internal reference.
1. Click any object in the preview to edit it. To see documentation on all customization options, [click here](/web/journeys/#template-customization-options).
1. When finished, click <notranslate>**Save & Close**</notranslate> button to continue.

**Note about generic deep linking params** If you are running a generic download campaign or a site-wide discount offer, your users would go to the same place inside your app regardless of where they originated on your website. You can configure this destination by setting **Deep Link Data** for the **Button** element when you [customize your template options](/web/journeys/#template-customization-options).

### Validate & Test

This screen allows you to preview your Journey variations, and is where you can perform final validation and testing on your Journey before publishing it.

![image](/_assets/img/pages/journeys/validate-and-test.png)

#### Preview

Use the dropdown menu to switch between your Journey variations.

![image](/_assets/img/pages/journeys/select-preview-variation.png)

To preview your Journey in your live, production website, enter your website URL in the <notranslate>**Test on your mobile device**</notranslate> field, and press the copy button. <notranslate>**The URL you enter must have the Branch Web SDK integrated and be using your Branch Key.**</notranslate>

![image](/_assets/img/pages/journeys/test-on-device.png)

!!! protip "How does this work?"
    The Branch SDK integrated into your website listens for a unique, one-time URL parameter that is generated by the preview tool. It looks something like `_branch_view_id=296449069883323397`. When this parameter is detected, the SDK loads a temporary preview of that specific Journey. This parameter is only valid for your Branch Key, and will not work on any other website even if the Branch SDK is integrated.

#### Validation

![image](/_assets/img/pages/journeys/validation-messages.png)

There are a number of errors and warnings you may encounter.

#### Web SDK errors

You must have the web SDK installed on your website to run a Journey.

#### App SDK warnings

If you choose to target iOS or Android users but haven’t integrated those SDKs, your Journeys will still show on the correct devices and direct users to your app. However, you won’t be able to get any install or event attribution for your Journeys, and you will not be able to deep link users to content inside your app. Be sure to integrate the Branch SDK into your app.

#### Audience rule warnings

You will see a warning if your audience rules do not add up to 100%. If less than 100%, the remainder will see whatever is normal behavior for your website. Your Journey will still run.

#### Premium account warnings
If you have built a Journey that includes premium-only functionality, you will see a warning, as certain features are only available by purchasing.

### Managing your Journeys App Banners

The [Journeys Manager](https://dashboard.branch.io/journeys) is your homepage for all of the personalized experiences create. You can turn Journeys on and off, clone them, or view performance.

![image](/_assets/img/pages/journeys/journeys-manager.png)

A Journey can have one of four states:

| State | Meaning | Next Stage |
| --- | --- | --- |
| <notranslate>Draft</notranslate> | Not yet published, editable | <notranslate>**Active**</notranslate> |
| <notranslate>Active</notranslate> | Live for your users, editable | <notranslate>**Stopped**</notranslate> |
| <notranslate>Stopped</notranslate> | Not live for your users, editable | <notranslate>**Active**</notranslate> or <notranslate>**Archived**</notranslate> |
| <notranslate>Archived</notranslate> | Not live for your users, editable | _none_ |

You can activate a journey directly from the creation flow, or from <notranslate>**Start**</notranslate> in the Actions menus in the Journeys Manager.

![image](/_assets/img/pages/journeys/edit-journeys.png)

!!! protip "Editing a live Journey"

You may edit Journeys in all states; if you do, however, your Journeys' performance and analytics may change. If you do decide to make a change, we recommend making a note of what you changed and when you made the change.


### Prioritizing Journeys

The Journeys Priority View allows you to set the priority of multiple Journeys when they **overlap**. They **overlap** when a single person is eligible to see multiple Journeys. You can prioritize the Journey that should show ahead of any others.

Let's say you have two Journeys that may reach the same audience.

1. A half page interstitial that promotes an offer on your "Shoes" category page.
2. A smart banner that should show for all visitors.

In general, you'd like the interstitial to show ahead of the smart banner on the "Shoes" category page (where both audience segments overlap).

To prioritize Journeys, switch to the Priority View by clicking on the toggle.

![image](/_assets/img/pages/journeys/priority-view-toggle.png)

You're now in Priority View.

1. Drag and drop Journeys in the order you'd like them to show. The lower numbers mean higher priority (i.e. a Journey with priority 1 is going to show ahead of a Journey with priority 2).

![image](/_assets/img/pages/journeys/first-priority-view.png)

2. Click the <notranslate>**Save**</notranslate> button.

![image](/_assets/img/pages/journeys/save-priority.png)

3. Your Journeys have now been prioritized.

![image](/_assets/img/pages/journeys/final-priority-view.png)

!!! warning "Caution"

    When you save Journeys priorities, <notranslate>**ALL**</notranslate> Journeys will be prioritized in the order they appear in the table.


For more detailed Journeys prioritization questions, visit our [Advanced section](/web/journeys/#prioritization).


### Visualizing Journeys performance

#### Analytics & attribution

Journeys map to [standard Branch analytics labels](/getting-started/configuring-links/#analytics-labels):

- All Journeys: `feature` = `journeys`
- Each Journey: `campaign` = `[Journey Name]`
- Individual Templates: `tags` = `[Template Name]` (+ any additional tags you specify during configuration)

You can access your Journey’s performance by selecting <notranslate>**View Performance**</notranslate> from the actions menu in the Journeys Manager.

![image](/_assets/img/pages/journeys/view-performance.png)

#### Using Source Analytics

You can also access Journeys analytics by selecting the above filters from the [Source Analytics](http://dashboard.branch.io/analytics/source) page of the Branch dashboard.

![image](/_assets/img/pages/journeys/view-source-analytics.png)

##### To compare all of your Journeys

1. Filter by `feature` = `journeys`

##### To compare variations within one Journey

1. Filter by `feature` = `journeys`
2. Filter by `campaign` = `[Journey Name]`

!!! protip "Attribute Journeys events to referring links"

    By default, when users arrive on a page running Journeys via a Branch link, then any interaction with the Journey (click/install/re-open) will be attributed to the referring Branch link, rather than to the Journey. [Learn how](/web/journeys/#preserve-or-discard-referring-link-data) to attribute this data to the Journey instead.


## Advanced

### Advanced audience filters

You can target users on a more granular level - based on behavior like where they came from, whether they already have your app installed, and what they’ve done on your website or in your app. We've created a bunch of great examples on the [next tab](/web/journeys/#examples).

![image](/_assets/img/pages/journeys/advanced-audience-rules.png)

#### Has completed event

If you have [custom event tracking](/apps/ios/#track-events) set up, you can target users based on events that you define. For instance, you might want to show a Journey to users who have completed a purchase within the last week, or who add an item to their shopping cart more than three times.

<!-- #### Referred from site

You can target a user based on the last touch point before they entered your website. For example, if you want to target users that found you through Google Search, you can select “Referred from site” and fill in `google.com`. Currently, we only support domain names in the Referred from site field. -->

#### Is located

Use this filter to target (or exclude) users viewing your website in different regions. Target by country, state/province, or city.

#### Is viewing a page url

You can define which subsets of your website the Journey will appear. For example, maybe you have a page `yoursite.com/settings` and `yoursite.com/products/1234`. You could fill in `products` here and only users visiting a URL with that substring present would see the Journey.

!!! warning "Exact URL Match Required"
    If you create an audience rule that relies on matching against a URL, please be advised it must be an **exact** match.  For example, if you set up the rule for `https://www.branch.io`only visitors to that URL will apply.  Users who view `https://www.branch.io/` (notice the `/`) will not be included in the rule.

#### Has visited web

Here, you can use website visits to determine who to target. For instance, you might decide that someone who visits your site five times is ready to see a Journey with some extra incentive to open the app.

#### Has visited the app

Similar to visited web, you can target users by number of app visits. For example, someone who has visited the app two times and opens up the mobile web could be lured back into the app with a Journey.

!!! warning "Relies on has_app"
    Note that this audience filter relies on `has_app`, which has [limitations](https://docs.branch.io/web/journeys/#has-app-limitations).

#### Has the app installed

You might choose to only show a Journey that asks a user to open the app to those that already have it installed.

!!! warning "Relies on has_app"
    Note that this audience filter relies on `has_app`, which has [limitations](https://docs.branch.io/web/journeys/#has_app-limitations).

#### Has clicked on ad

A user is grouped into <notranslate>"Has clicked on Ad"</notranslate> when they've clicked a link from [Deep Linked Feeds](/deep-linked-ads/dynamic-product-feeds/).

Use this to target users who have been part of an ad campaign to improve your ROI; maybe with a specific call to action to open the app and buy something if they've also never made a purchase in the app.

The technical definition is that they've clicked on a link with an Ad Network's custom `$3p` value in link data, but you just need to consider the way the link is created - in this case, through Deep Linked Feeds.

#### Has clicked on email

A user is grouped into <notranslate>"Has clicked on Email"</notranslate> when they've clicked a link from [Universal Email](https://dashboard.branch.io/email).

Use this to target users who have been part of an email campaign; maybe with a specific call to action to get them download the app if they don't have it and they've landed on mobile web.

The technical definition is that they've clicked on a link with an Email Service Provider's custom `$3p` value in link data, but you just need to consider the way the link is created - in this case, through a Universal Email integration.

#### Is viewing a page with metadata key

Use this filter to target users viewing web pages with certain metadata specified. This data can be specified in HTML `<meta>` tags on a webpage, passed in as options in the `init()` call that you use to initialize the Branch web SDK, or passed in using the `track()` call in Branch’s web SDK. Note that if you opt to use HTML `<meta>` tags, your tags should be formatted as [Branch hosted deep link data](/web/hosted-data/#add-metatags-to-your-site).

For example, you could target users on pages containing the metadata key “foo” and value “bar” by adding this tag to the page’s HTML: `<meta name="branch:deeplink:foo" content="bar" />`

Or by initializing Branch’s web SDK with the following options object:

```javascript
branch.init( 'BRANCH_KEY',
    {
        metadata : {
            'foo' : 'bar'
        }
    }
);
```

Or, finally, by using the track() call to [programmatically trigger a Journey to show](/web/journeys/#trigger-a-journey-to-show-by-firing-an-event):

```javascript
branch.track(‘pageview’,
    {
        ‘foo’ : ‘bar’
    }
);
```

Once metadata has been specified on a page in any or all of the three locations specified above, you can target users on that page using the “Is viewing a page with metadata key” audience filter. If metadata with the same key has been specified in either `init()` or `track()` _and_ in an HTML `meta` tag, the metadata passed into either `init()` or `track()` will take precedence.

#### Has interacted with Journey

Use this filter to target users who have interacted with a specific Journey before. Choose the Journey, the type of interaction, and the window in which that interaction occurred. For example, you could use this filter to display a Journey (Journey A) only to users who had dismissed a different Journey (Journey B) in the past 7 days.

### has_app limitations

Several pieces of Journeys functionality rely on Branch’s understanding of whether an end user has a customer’s app installed (indicated in Branch’s system using the `has_app` flag). For example, the <notranslate>**Has the app installed**</notranslate> advanced audience rule will only be satisfied if Branch believes the app is installed on that user’s device. Similarly, the CTA text on a Journey will only switch from “install” to “open” if Branch believes the app is installed on that user’s device.

Unfortunately, Branch does not - and cannot - know with 100% accuracy whether a given user actually has the app installed, since the operating systems (e.g. iOS, Android) do not make this information available to developers. We’ve developed our own methods for gleaning this information, and while our methods are quite accurate, there are nevertheless opportunities for both false positives and false negatives.

Several of the complicating factors are:

- **Install vs. Open:** If a user installs an app but doesn’t open it, we won’t know that they have the app installed.
- **Uninstalls:** We won’t necessarily know if a user uninstalls an app, which could result in a false positive.
- **Apple’s Intelligent Tracking Prevention:** As a result of ITP, we’re less accurate on Safari on iOS than on all other browsers.
- **Time to update:** Latency in our system occasionally means that for a given user, in the moments (or minutes) following an install, Journeys may not know that the install has occurred.

While we don’t think these limitations should discourage you from using features that rely on “has_app”, we would recommend keeping them in mind when designing your Journeys.

### Set up split testing

This feature allows you to run A/B tests by designing multiple templates and assigning a percentage of your audience to each one.

1. Click the <notranslate>**Add Variation**</notranslate> button to add another design variation. ![image](/_assets/img/pages/journeys/add-variation.png)
1. To remove an unwanted variation, click the `-` button. ![image](/_assets/img/pages/journeys/remove-variation.png)
1. Use the percentage fields to control the ratio of your audience that will see each variation.![image](/_assets/img/pages/journeys/multiple-templates.png)

!!! protip "Variation Display Limitations"
    You may have up to three variations in each Journey. Your total percentage allocation must not equal more than **100%**. Your total percentage allocation may be _less_ than **100%**. In this situation, the remainder of your audience will be shown your standard website without a Journey. This allows you to A/B test against your non-Journeys website experience.

### Auto-open

You can auto-open the app for users have your app installed with Journeys. You can find this setting by selecting the CTA in the template editor:

![image](/_assets/img/pages/journeys/auto-open-find.png)

When this box is checked, if a user views this Journey variation on your website and they have the app installed, the app will automatically open without them clicking.

![image](/_assets/img/pages/journeys/auto-open.png)

As opening the app automatically is the best user experience in most cases, this is checked by default for all new templates.

!!! caution "Web SDK open app setting"
    If you use the open_app setting within the web SDK, this setting will still work for old Journeys (older than 10/25). For all new Journeys, the template setting will take precedence.

!!! caution "Open app behavior in in-app webviews"
    Please avoid using the Branch Web SDK on webpages inside of native webviews in your own app. The Branch Web SDK's auto-open can cause unexpected user experiences.

!!! warning "Open app behavior on Android Chrome"
    Auto-open will only work on Android Chrome from a link click; redirecting from a manually inserted URL will not auto-open the app.

#### Auto-open the app on iOS

The auto-open setting in the template editor will work on iOS Chrome and Android. Because auto-open is powered by URI schemes and these can lead to error messages on iOS Safari for users without your app, this is not enabled on iOS by default.

If you would like the app to open automatically on iOS Safari as well, you'll need to use a setting called `$uri_redirect_mode`. Since Branch has a massive pool of cookies tied to device identifiers, we know if your app is installed when the user clicks a link. We use this intelligence to determine when to use URI schemes. If we have the history that the user installed your app, we’ll use URI schemes to open up the app.

You can [reach out to support](https://support.branch.io/support/tickets/new){:target="\_blank"} to enable this behavior across all your links, or set it just for Journeys in the web SDK:

```
<script type="text/javascript">
// load the Branch web lib
(function(b,r,a,n,c,h,_,s,d,k){if(!b[n]||!b[n]._q){for(;s<_.length;)c(h,_[s++]);d=r.createElement(a);d.async=1;d.src="build.min.js";k=r.getElementsByTagName(a)[0];k.parentNode.insertBefore(d,k);b[n]=h}})(window,document,"script","branch",function(b,r){b[r]=function(){b._q.push([r,arguments])}},{_q:[],_v:1},"addListener applyCode banner closeBanner creditHistory credits data deepview deepviewCta first getCode init link logout redeem referrals removeListener sendSMS setBranchViewData setIdentity track validateCode".split(" "), 0);
// init Branch and pass in your preference to open the app
branch.init('BRANCH_KEY');
// Trigger your Journeys banner to use the correct redirect mode
branch.setBranchViewData({
        '$uri_redirect_mode': 1
});
</script>
```

Or, set it for individual templates by adding deep link data `$uri_redirect_mode:1`:

![image](/_assets/img/pages/journeys/uri-redirect-mode.png)

[Read our blog](https://blog.branch.io/making-uri-schemes-great-again-uri_redirect_mode/){:target="\_blank"} to learn more about the challenges of URI schemes on iOS and the URI redirect mode feature.

### Dismissal settings

In some cases, rather than simply ignoring your Journeys, your users may want to dismiss them (by clicking either the “X” or the dismissal text on the Journey in question). In order to make sure that your users are having the best possible experience while also converting at the highest rate, you can adjust your Journeys’ dismissal settings. You can access these settings while you’re setting up your templates by navigating to the Dismissal Settings tab. In that tab you’ll have control over a number of settings:

#### Dismissal behavior

Choose what happens when a user dismisses a Journey. “Close Journey” will simply cause the Journey to close upon being dismissed; “Redirect to a web page” will cause the Journey to close and redirect to the webpage of your choice.

#### Dismissal period

First, use the dropdown to choose how long the Journey should be dismissed for. Next, decide whether dismissing this Journey should cause only this Journey to be dismissed for the chosen dismissal period, or whether it should cause all Journeys to be dismissed for that period.

![image](/_assets/img/pages/journeys/dismissal_settings.png)

### Preserve or discard referring link data

By default, when users arrive on a page running Journeys via a Branch link and `make_new_link` is not set to `true`, then any interaction with the Journey (click/install/re-open) will be attributed to the referring Branch link, rather than to the Journey. If `make_new_link` is set to `true`, the same events will be attributed to the Journey, instead.

This can help you collect data on how the referring links are contributing to app growth/engagement, even when users aren’t installing from those links directly. For example, if a user clicked a Branch link on Facebook, landed on your website, and installed from a Journey, this would allow you to attribute the install to the link on Facebook. If the original link was also configured to deep link into your app, that deep link would be preserved, too.

Branch will pass the referring link into Journeys by default. In order to discard referring link data, include the `make_new_link` flag, with a value of  `true`, into the options during initialization:

```javascript
branch.init( 'BRANCH_KEY',
    {
        'make_new_link' : true
    }
);
```

### Prioritization

#### When do my Journeys prioritization rules apply?
Prioritization only takes effect when two Journeys are overlapping. If you have a Journey targeting iOS users and a Journey targeting Android users, the prioritization won't matter. If you update the Journey targeting iOS to now target iOS and Android users, the higher priority Journey will show to Android users.

#### What happens if a user dismisses a banner or interstitial?
When a user dismisses a banner or interstitial, that banner or interstitial will be dismissed for the amount of time specified in the Journey’s [dismissal settings](/web/journeys/#dismissal-settings).

If the Journey has been configured to dismiss all Journeys when dismissed, no other Journey will be shown to the user for the duration of the dismissal period. If the Journey has been configured to dismiss only that Journey when dismissed, other Journeys will be shown to the user if they apply.

#### Why do I have to prioritize Stopped and Draft Journeys?
We ask you to prioritize all non-Archived Journeys because Journeys can be set live from *Draft* or *Stopped* mode.

#### What happens if I have some Journeys with priorities set and some without?
We recommend setting priority for all Journeys. All new Journeys you create will automatically have the lowest priority assigned to them, as well as *Draft* or *Stopped* Journeys *without priority* that are set live (Journeys with priority will not have their priority changed unless you explicitly set them). If you don't set a priority for all your Journeys, then any matching Journey (i.e. Journey passing the audience filter you set) without priority will be picked at random to show.

### Scheduling

You can set a time when your Journey will become active and be visible to your users and/or a time when it will no longer be displayed. You can also schedule Journeys on a recurring basis.

You can access this feature from the <notranslate>**Validate & Test**</notranslate> step or directly from the action menu on the Journeys manager page.

![image](/_assets/img/pages/journeys/schedule-action.png)

!!! example "Example: Scheduling a Journey"
    Imagine you want to show your users a Journey during the month of November that advertises a 25% sale if they download your app. You can set it to start at 12 AM on November 1st, and end at 12 AM on December 1st:


    ![image](/_assets/img/pages/journeys/schedule-modal.png)

!!! example "Example: Recurring Schedules"
    Imagine you have a show that airs from 9-10 PM every Sunday, and you want to encourage users to view the episode in-app during that time. You can set a start time of 9 PM on the upcoming Sunday, set a stop time of 10 PM that same day, and then set it to repeat weekly:


    ![image](/_assets/img/pages/journeys/schedule-modal-recurring.png)

#### Scheduling FAQ

1. **When does my scheduled Journey become active or stopped?**
   There can be up to a 5 minute delay between a scheduled time and your Journey becoming active or stopped.
1. **How do I set an end date for a Journey with a recurring schedule?**
   This is not supported with scheduling at this time. To do this, set a start and stop time for your Journey and add your repeat rules. When you want the Journey to stop for good, stop it from the action menu or Edit Schedule > Delete.


### Dynamic Journeys layout customization

We now support the use case where you can customize the appearance of a Journey depending on which link referred the web session. So, you can create a Branch link with a set of defined keys and values that will change properties such as the title or images when the user is referred to your website from this link.

| **Link Data Key** | **Value** | **Example Value** |
| ---: | --- | --- |
| `$journeys_button_get_has_app` | The call to action button when the app is currently installed | "Open App" |
| `$journeys_button_get_no_app` | The call to action button when the app is **not** currently installed | "Install App" |
| `$journeys_title` | The title or main text of your Journey | "Download Appsolutely today" |
| `$journeys_description` | This is the description or subtitle in the frame | "This app is disrupting apps" |
| `$journeys_icon_image_url` | The app icon displayed in the layout | "https://mysite.com/image.png" |

Note that not all template support all override keys. For example, the floating button does not support title, description or icon image url (floating buttons will support the custom liquid tags detailed below though). If a template is to be rendered and the key you've specified does not exist, we'll simply ignore it while rendering the template.

#### Custom tags for dynamic Journeys layout customization

In addition to using [pre-defined keys](/web/journeys/#dynamic-journeys-layout-customization) (e.g. $journeys_title) to dynamically customize the appearance/content of a Journey, you can use custom liquid tags. Custom tags can be inserted in both the View Editor and the CSS Editor when you’re setting up a Journeys template. Then, you can use `setBranchViewData()` to dynamically provide values for these tags.  You can also embed those values statically on a page with [Branch Meta Tags](/web/hosted-data/#add-metatags-to-your-site).

**Note that if you include custom liquid tags in your templates and also set a value for a pre-defined key (e.g. $journeys_title) in `setBranchViewData()`, the value of the pre-defined key will take precedence.**

The format for a custom liquid tag is as follows. Note that a default value must be specified for every custom tag you include:

```
{{ key_name | default_value }}
```

For example, if you were adding a custom liquid tag in CSS to dynamically control the font size of one of your Journeys’ title, you might use a tag like the one below:

```
{{ fontSize | 12px }}
```
![image](/_assets/img/pages/journeys/custom-tags-1.png)

And if you were adding a custom liquid tag in your template text, you might use a tag like the one below:
```
{{ adjective | best }}
```
![image](/_assets/img/pages/journeys/custom-tags-2.png)

Then, to dynamically update values for the “fontSize” and “adjective” variables, you would set values for those variables using `setBranchViewData()`:

```
branch.setBranchViewData({
    data: {
        'fontSize': '20px',
        'adjective': 'most entertaining',
    }
});
```

Or, you can set the values by embedding Branch Meta Tags on the page:

```
<meta name="branch:deeplink:fontSize" content="20px" />
<meta name="branch:deeplink:adjective" content="most entertaining" />
```

### Clientside Javascript Journeys controls

There are a number of clientside APIs to help you build quality user experiences. See below:

#### Use Javascript to block a Journey from showing

You can prevent Journeys from showing on a certain page by inserting `no_journeys` with the value of `true` into the options during initialization.

```
<script type="text/javascript">
// load the Branch SDK file
branch.init('BRANCH_KEY',
    {
      'no_journeys': true
    }
);
</script>
```

### Closing a Journey Programmatically

Journeys include a close button the user can click, but you may want to close the Journey with a timeout, or via some other user interaction with your web app.
In this case, closing the Journey is very simple by calling:


```javascript
branch.closeJourney(function(err) { console.log(err); });
```

### Trigger a Journey to Show by Firing an Event

If you block or programatically close a Journey via one of the calls above, then you can trigger a Journey to show by firing the following event:

```Javascript
branch.track('pageview');
```

**Note:** If a user has closed a Journey in the past, then firing the aforementioned event will not override a user's preference.

### Disable Journeys Animations

You can disable Journeys animations on a page by setting two flags - `disable_entry_animation` and `disable_exit_animation` - when you’re calling either init() or track() with Branch’s Web SDK.

Journeys animations can be disabled in order to reduce the amount of time it takes to load a Journey on a page. They can also be disabled in order to improve Journeys UX on single-page web apps, where Journeys animations can be jarring. When switching between multiple Journeys on a single-page web app, remember to use [setBranchViewData()](/web/journeys/#deep-linking-from-the-banner-or-interstitial) to change the link behind the CTA.

To disable animations during initialization, insert `disable_entry_animation` and/or `disable_exit_animation`, with values of `true`, into the options:

```javascript
branch.init(‘BRANCH_KEY’,
    {
        ‘disable_entry_animation’ : true,
        ‘disable_exit_animation’ : true
    }
);
```

To disable animations using track(), insert `disable_entry_animation` and/or `disable_exit_animation`, with values of `true`, into the event metadata:

```javascript
branch.track(
    ‘pageview’,
    {},
	{
	    ‘disable_entry_animation’ : true,
        ‘disable_exit_animation’ : true
    }
);
```

### Listen to Journeys lifecycle events

You can easily listen to Journeys lifecycle events by registering listener functions like so:

```javascript
var listener = function(event, data) { console.log(event, data); }

// Specify an event to listen for
branch.addListener('willShowJourney', listener);

// Listen for all events
branch.addListener(listener);
```


| Listener Name | Description |
| --- | --- |
| `willShowJourney` | Journey is about to be shown. |
| `didShowJourney` | Journey's entrance animation has completed and it is being shown to the user. |
| `willNotShowJourney` | Journey will not be shown and no other events will be emitted. |
| `didClickJourneyCTA` | User clicked on Journey's CTA button. |
| `didClickJourneyClose` | User clicked on Journey's close button. |
| `willCloseJourney` | Journey close animation has started. |
| `didCloseJourney` | Journey's close animation has completed and it is no longer visible to the user. |

### Journeys text localization

#### Client-side

You can easily customize the Journey text dynamically client side using `setBranchViewData` and by reading the browser's language.

```javascript
var lang_code;
if (navigator.languages && navigator.languages.length>0) {
    lang_code = navigator.languages[0];
} else if (navigator.language) {
    lang_code = navigator.language;
}

// Change Journeys text if language is Spanish (ES)
if (lang_code == 'es') {
    branch.setBranchViewData(
        {
            data: {
                 "$journeys_title": 'Mi App',
                 "$journeys_description": 'Mi descripción',
                 "$journeys_button_get_has_app": 'Avrir',
                 "$journeys_button_get_no_app": 'Ver',
             }
         }
    );
}
```

#### Server-side
Journeys provides limited server-side localization. This functionality is currently in beta, so please reach out to your account manager or integrations@branch.io to receive access.

### CSS Editor

If you have an upgraded premium account, you may also modify your CSS code directly in addition to using the WYSIWYG View Editor. To do so, go to the <notranslate>**Configure Views**</notranslate> step, click to edit a template, and then select the <notranslate>**CSS Editor**</notranslate> tab on the <notranslate>**Customize Template**</notranslate> screen.

![image](/_assets/img/pages/journeys/view-css-editor.png)

#### Adding a Second Line of Text

You can add a second line of text to your Journey either before or after by adding it to the CSS element:

- Before
```
branch-banner .branch-banner-description::before

{ display: block; content: 'Chat with other Fans'; }
```

- After
```
#branch-banner .branch-banner-description::after

{ display: block; content: 'Watch in Dark Mode'; }
```

#### Custom fonts with Journeys

1) Go to [Google Fonts](https://fonts.google.com/) and select a font.

![image](/_assets/img/pages/journeys/font_embedding.png)

2) Add to CSS EDITOR in Journeys. Please note: trailing semicolon on @import line is important. It's always good to have a fallback web font in case the google font fails to load.

![image](/_assets/img/pages/journeys/custom_font.png)

### Template customization options

The customization options available depend on the template chosen:

- [Smart Banner](/web/journeys/#smart-banner)
- [Interstitial](/web/journeys/#full-screen-interstitial)
- [Button Template](/web/journeys/#button-template)

#### Smart Banner

The available configuration options are identical for banners at both the top and the bottom of the screen.

##### Background

![image](/_assets/img/pages/journeys/customize-banner-background.png)

| Option | Usage |
| --- | --- |
| Text Color | Specify the text color for elements without a specific setting. _Not currently used_ |
| Background Color | Set the background color of the banner |

##### Title

![image](/_assets/img/pages/journeys/customize-banner-title.png)

| Option | Usage |
| --- | --- |
| Formatting Bar | WYSIWYG styling for title text |
| Title | The text of the title. Maximum 35 characters |

##### Description

![image](/_assets/img/pages/journeys/customize-banner-description.png)

| Option | Usage |
| --- | --- |
| Formatting Bar | WYSIWYG styling for description text |
| Description | The text of the description. Maximum 60 characters, will wrap to two lines |

##### Rating

![image](/_assets/img/pages/journeys/customize-banner-rating.png)

| Option | Usage |
| --- | --- |
| Formatting Bar | WYSIWYG styling for rating stars. Primarily useful for changing color |
| Rating Star Count | The number of stars of your App/Play Store rating average. We encourage you to be honest! |

##### Reviews

![image](/_assets/img/pages/journeys/customize-banner-reviews.png)

| Option | Usage |
| --- | --- |
| Formatting Bar | WYSIWYG styling for reviews count |
| Reviews | The number of reviews of your app on the App/Play Store. We encourage you to be honest! |

##### Button

![image](/_assets/img/pages/journeys/customize-banner-button.png)

| Option | Usage |
| --- | --- |
| Text Color | Change the color of the button text and button outline |
| Background Color | Change the color of the button background
| Button Text | Change the text shown when the app is installed and not installed. |
| Channel | Set the <notranslate>**[Channel](/links/integrate/#analytical-labels)**</notranslate> for the Branch link attached to the button. For example, `website`
| Tags | Set the <notranslate>**[Tags](/links/integrate/#analytical-labels)**</notranslate> for the Branch link attached to the button. For example, `purchase` and `fall-sale`
| Deep Link Data | Insert deep link data and advanced link control parameters. Can contain any [Branch link parameter](/links/integrate/#configure-deep-links)

!!! warning "Relies on has_app"
    Note that button text relies on `has_app`, which has [limitations](https://docs.branch.io/web/journeys/#has_app-limitations).

##### Dismiss

![image](/_assets/img/pages/journeys/dismissal_banner.png)

| Option | Usage |
| --- | --- |
| Formatting Bar | WYSIWYG styling for dismiss button |

##### App Icon

![image](/_assets/img/pages/journeys/customize-banner-icon.png)

| Option | Usage |
| --- | --- |
| App Icon | Enter the URL for your app icon, or upload an image |

#### Full screen interstitial

##### Background

![image](/_assets/img/pages/journeys/customize-fullpage-background.png)

| Option | Usage |
| --- | --- |
| Text Color | Specify the text color for elements without a specific setting. _Not currently used_ |
| Background Color | Set the background color of the interstitial |
| Background | Enter the URL for your background graphic, or upload an image |
| Image Position | Control the vertical alignment of the background graphic |
| Content Position | Control the vertical alignment of the content block |

| Image Position | Usage |
| --- | --- |
| Top | Pin to top of screen, scale to full screen width |
| Center | Pin to middle of screen, scale to full screen width |
| Bottom | Pin to bottom of screen, scale to full screen width |
| Cover | Anchor to top of screen, scale to fill entire screen |

The content block contains everything except for the background image. Dimensions _within_ this block are preset and cannot be modified.

| Content Position | Usage |
| --- | --- |
| Top | Pin to top of screen |
| Center | Pin to center of 'safe' screen height (accounting for browser controls and device dimensions) |
| Bottom | Pin to bottom of 'safe' screen height (accounting for browser controls and device dimensions) |
| Custom | Position by relative percentage. Be sure to test for appropriate real-world alignment

##### Title

![image](/_assets/img/pages/journeys/customize-fullpage-title.png)

| Option | Usage |
| --- | --- |
| Formatting Bar | WYSIWYG styling for title text |
| Title | The text of the title. Maximum 35 characters, will wrap to multiple lines |

##### Description

![image](/_assets/img/pages/journeys/customize-fullpage-description.png)

| Option | Usage |
| --- | --- |
| Formatting Bar | WYSIWYG styling for description text |
| Description | The text of the description. Maximum 60 characters, will wrap to multiple lines |

##### Button

![image](/_assets/img/pages/journeys/customize-fullpage-button.png)

| Option | Usage |
| --- | --- |
| Text Color | Change the color of the button text and button outline |
| Background Color | Change the color of the button background
| Button Text | Change the text shown when the app is installed and not installed. |
| Channel | Set the <notranslate>**[Channel](/links/integrate/#analytical-labels)**</notranslate> for the Branch link attached to the button. For example, `website`
| Tags | Set the <notranslate>**[Tags](/links/integrate/#analytical-labels)**</notranslate> for the Branch link attached to the button. For example, `purchase` and `fall-sale`
| Deep Link Data | Insert deep link data and advanced link control parameters. Can contain any [Branch link parameter](/links/integrate/#configure-deep-links)

!!! warning "Relies on has_app"
    Note that button text relies on `has_app`, which has [limitations](https://docs.branch.io/web/journeys/#has_app-limitations).

##### Dismiss

![image](/_assets/img/pages/journeys/dismissal_interstitial.png)

| Option | Usage |
| --- | --- |
| Dismiss Journey configuration | Choose whether the user should be able to dismiss the Journey via a button and/or via text |
| Dismiss Text | Text to show users wanting to continue to your mobile website instead of downloading the app.
| Formatting Bar | WYSIWYG styling for dismiss button & text |

#### Button Template

##### Button Text

![image](/_assets/img/pages/journeys/customize-button-template.png)

| Option | Usage |
| --- | --- |
| Text Font | Specify the text font for the button |
| Text Size | Specify the text size for the button |
| Text Color | Specify the text color for for the button |
| Background Color | Set the background color of the button |
| Bold | Bold the text of the button |
| Text Alignment | Control the alignment - left / center / right adjusted - of the button text |
| Button Text - App Installed | The text of the button when the user already has the app installed on the device |
| Button Text - App Not Installed | The text of the button when the user does not have the app installed on the device |
| Auto-Open| When this box is checked, if a user views this Journey on your website and they have the app installed, the app will automatically open without them clicking |
| Tags | Set the <notranslate>**[Tags](/links/integrate/#analytical-labels)**</notranslate> for the Branch link attached to the button. For example, `purchase` and `fall-sale`
| Deep Link Data | Insert deep link data and advanced link control parameters. Can contain any [Branch link parameter](/links/integrate/#configure-deep-links)

!!! warning "Relies on has_app"
    Note that button text relies on `has_app`, which has [limitations](https://docs.branch.io/web/journeys/#has_app-limitations).

##### Dismiss

![image](/_assets/img/pages/journeys/dismissal-button.png)

| Option | Usage |
| --- | --- |
| Dismissal behavior | Choose what should happen when the Journey is dismissed |
| Dismissal Period | Decide how long the Journey should be dismissed for, and whether that dismissal period should apply to all Journeys or just this one |

#### Customizing the Template's Container (iFrame)

!!! warning "Advanced Feature / CSS Knowledge Required"
    Customizing a template's container (iFrame) may impact the way it displays on your website. Please test thoroughly before deploying Journeys with customized containers.

To access the template's container (iFrame) CSS code:

1. Once you've chosen a template for your Journey, click on the <notranslate>**Page Placement**</notranslate> tab.
2. Under <notranslate>**Page Settings**</notranslate> on the <notranslate>**Page Placement**</notranslate> tab, click the <notranslate>**Customize Container (iFrame)**</notranslate> radio button.
3. Modify the iFrame as you see fit and click <notranslate>**Save & Close**</notranslate>.

![image](/_assets/img/pages/journeys/customize-container-iframe.png)

!!! info "Access Required"
    This advanced feature is currently only available upon request.  Please contact your Account Manager to request access.

### Limitations for apps with free accounts

- Any number of Journeys may be created in <notranslate>**Draft**</notranslate> mode using all features.
- An invitation to upgrade will be displayed when premium-only functionality is enabled
- Only a single Journey using the Smart Banner template (either top or bottom position) may be <notranslate>**Active**</notranslate> at any one time.
- To enable a different Journey, the currently active Journey must first be put into <notranslate>**Stopped**</notranslate> mode.
- Any Journey using premium-only features cannot be placed into <notranslate>**Active**</notranslate> mode until the app has been upgraded.

## Web to app routing without Journeys

If you maintain a mobile website, Branch allows you to deep link mobile visitors directly into your app, or easily and automatically give them the option of downloading it.

### Open app if installed

Add the following code somewhere inside the `<head></head>` tags on your website and customize the [link parameters](/links/integrate/#configure-deep-links) to suit your needs.

!!! protip
    What this script does is move a lot of the Branch redirection logic to the Javascript on your own page, effectively 'clicking a Branch link' on page load.


```javascript
<script type="text/javascript">
// load the Branch SDK file
{! partials/web-sdk-init.md !}
// define the deepview structure
branch.deepview(
    {
      'channel': 'mobile_web',
      'feature': 'deepview',
      data : {
        '$deeplink_path': 'page/1234',
        'user_profile': '7890',
        'page_id': '1234',
        'custom_data': 1234
      }
    },
    {
      'open_app': true  // If true, Branch attempts to open your app immediately when the page loads. If false, users will need to press a button. Defaults to true
    }
);
</script>
```

{! partials/replace-branch-key.md !}

### Add an install call to action

Trigger the `branch.deepviewCta()` function with a button or hyperlink on your page. Executing this function (whether by button, link, or some other method) 'clicks' the link you defined using `branch.deepview()` above.

| Platform | Result of Call To Action
| --- | ---
| Mobile, app installed | Open app, deep link directly to content. This is a failsafe action in case the 'link click' on page load didn't fire correctly.
| Mobile, app NOT installed | Open App Store or Play Store page for your app, deep link directly to content after download.
| Desktop | Redirect to `$desktop_url` specified in the `deepview()` call, or fall back to your default web url from [Link Settings](https://dashboard.branch.io/link-settings).


Here's how to add a simple hyperlink call to action:

```html
<a id='downloadapp' onclick='branch.deepviewCta()'>View this in app</a>
```

## Troubleshooting

### Calls to [branchsubdomain] blocked

{! ingredients/branchsubdomain.md !}

Please make sure to add `[branchsubdomain]` to the CSP header for your pages. We've seen some browsers that attempt to block it outright. You can deliver this in an HTTP header from your web server or you can add a simple metatag to your site like so:

```html
<meta http-equiv="Content-Security-Policy" content="default-src https://[branchsubdomain]; child-src 'none'; object-src 'none'">
```

### Non-mobile optimized sites

If you're not using a mobile viewport tag (`<meta name="viewport" content="width=device-width initial-scale=1, maximum-scale=1, user-scalable=no">`) because your site isn't mobile optimized, Journeys will look shrunken and weird. Don't worry, we have you covered:

1. design the banner as you would like it to look on your site
2. Go to the CSS editor and scroll to the bottom of the CSS code
3. Add two properties to the #branch-banner selector
    - `height: 228;`
    - `zoom: 3;`

The image will not look scaled properly in the editor view. This is because the dashboard is mobile optimized. Use the preview test link on the validation page to make sure the banner looks right

### Prevent overlap between top banners and persistent navigation bars

- Navigate to [Dashboard Journey Page](https://branch.dashboard.branch.io/web/journeys)
- Select <notranslate>**Journey**</notranslate> -> <notranslate>**Edit**</notranslate> -> <notranslate>**Configure Views**</notranslate> -> <notranslate>**Banner**</notranslate> -> <notranslate>**Page Placement**</notranslate>
- Banner Scroll = <notranslate>**sticky**</notranslate>
- Press <notranslate>**Save & Close**</notranslate>
- Add the following div to your nav

    ```html
    <div class="branch-journeys-top"></div>
    ```

    ![image](/_assets/img/pages/journeys/sticky.png)


## Examples

### Example audiences

The Journeys audience tool is extremely powerful, but sometimes a few examples can help kickstart your creative juices. Here are are a couple common audience use cases to help you get started.

1. [New users](/web/journeys/#example-new-users)
2. [Loyal users](/web/journeys/#example-loyal-users)
3. [Retargeting users who have taken some action](/web/journeys/#example-retargeting-users)
4. [Users from Google (for SEO)](/web/journeys/#example-seo-friendly)
5. [iOS users from English-speaking countries](/web/journeys/#example-english-speaking-ios-users)

All of these examples require you to configure advanced audience rules, which is a premium feature. You can add any set of complex rules using the following button:

![image](/_assets/img/pages/journeys/examples/advanced_add_filter.png)

#### New Users

In this example, you'll configure an audience to target people who have visited your site **less than 3 times** historically. Anyone who had visited more than this will be excluded. First, you'll add a new rule for <notranslate>**Has visted web**</notranslate> in the advanced section.

![image](/_assets/img/pages/journeys/examples/new_users_0.png)

Next, you'll choose the <notranslate>**Less than or equal to**</notranslate> in the middle section:

![image](/_assets/img/pages/journeys/examples/new_users_1.png)

Finally, you'll enter 2 in the last part to indicate you want to target people who have visited less than 3 times historically.

![image](/_assets/img/pages/journeys/examples/new_users_2.png)

Save and continue!

#### Loyal Users

In this example, you'll configure an audience to target people who have visited your site **more than 4 times** historically. Anyone who had visited less than this will be excluded. First, you'll add a new rule for <notranslate>**Has visted web**</notranslate> in the advanced section.

![image](/_assets/img/pages/journeys/examples/new_users_0.png)

Next, you'll choose the <notranslate>**More than or equal to**</notranslate> in the middle section:

![image](/_assets/img/pages/journeys/examples/loyal_users_1.png)

Finally, you'll enter 5 in the last part to indicate you want to target people who have visited more than 4 times historically.

![image](/_assets/img/pages/journeys/examples/loyal_users_2.png)

Save and continue!

#### Retargeting Users

In this example, you'll configure an audience to target people who have completed some action on your site in a past or current session. For example, if a user had added something to their cart or had previously completed a purchase. You can retarget these users with a custom call to action to download. We'll use a generic event called `MyAction` in the example. First, you'll add a new rule for <notranslate>**Has completed event**</notranslate> in the advanced section.

![image](/_assets/img/pages/journeys/examples/retargeting_users_0.png)

In this next dropdown, you'll choose the custom event to retarget from. Here, we'll use a generic event called `MyAction` but you would select `Purchase` or something more meaningful to your use case.

![image](/_assets/img/pages/journeys/examples/retargeting_users_1.png)

Next, you'll choose the <notranslate>**More than or equal to**</notranslate> in the middle section:

![image](/_assets/img/pages/journeys/examples/retargeting_users_2.png)

Finally, you'll enter 3 in the last part to indicate you want to target people who have completed `MyAction` more than 2 times historically.

![image](/_assets/img/pages/journeys/examples/retargeting_users_3.png)

Save and continue!

#### SEO Friendly

Google has recently announced that it will begin punishing sites that show a full page interstitial when a user comes from search. Because of this, you'll likely need to treat Google search traffic differently than traffic that comes from any other source. In this example, you'll set up an audience specific to users who come from Google. First, you'll add a new rule for <notranslate>**Came directly from a url**</notranslate> in the advanced section.

![image](/_assets/img/pages/journeys/examples/seo_friendly_0.png)

Next, you'll choose the <notranslate>**starts with**</notranslate> in the middle section to match a substring:

![image](/_assets/img/pages/journeys/examples/seo_friendly_1.png)

Finally, you'll enter `google.com` to target users who came from Google search (where the referrer starts with google.com):

![image](/_assets/img/pages/journeys/examples/seo_friendly_2.png)

Alternatively, you can target users who did NOT come from Google search (where the referrer doesn't start with google.com):

![image](/_assets/img/pages/journeys/examples/seo_friendly_3.png)

#### Example: English speaking iOS users

In this example, you'll restrict the audience to users in countries where English is the native language who are on the iOS operating system. Note that this is not in the advanced audience section, but rather in the top section. First, select `iOS` of the mobile OS checkboxes.

![image](/_assets/img/pages/journeys/examples/ios_english_0.png)

Next, go through and choose the following countries: `United States`, `Canada`, <notranslate>**United Kingdom**</notranslate> and `Australia`.

![image](/_assets/img/pages/journeys/examples/ios_english_1.png)

Save and continue!

## Journeys and GDPR
In order to help our customers comply with [GDPR](https://branch.io/gdpr/), and other laws that restrict data collection from certain users, we’ve updated our Web SDK with a [Do Not Track mode](/web/integrate/#enable-do-not-track-mode). This way, if a user indicates that they want to remain private on your website, or if you otherwise determine that a particular user should not be tracked, you can continue to make use of the Branch Web SDK (e.g. for creating Branch links) while not tracking that user. This setting can also be enabled across all users for a particular link, or across your Branch links.

If you enable that mode, you can still display some Journeys to your users. Whether or not a Journey will display for users in Do Not Track mode depends on the targeting criteria you’ve defined for that Journey. If the Journey uses any of the following audience filters, it will *not* display for users in Do Not Track mode. Otherwise, the Journey will display.

<notranslate>
* Has completed event
* Has visited web
* Has visited the app
* Has clicked on email
* Has clicked on ad
* Has the app installed
</notranslate>

If a Journey does display for a user in Do Not Track mode, any analytics related to the Journey’s display or the user’s interactions with that Journey *will not be published in the Branch dashboard.*
