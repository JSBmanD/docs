---
title: Channel Level Access
---
The <notranslate>"Channel"</notranslate> level of a Branch account is the fourth level of access and includes access (either edit or read-only) to the following functionality:

<table>
  <tr>
    <th rowspan="10"><img src="/images/pages/dashboard/access-levels/app-level-nav.png"></th>
  </tr>
	<tr>
		<th></th>
		<th></th>
		<th></th>
		<th></th>
    <th></th>
	</tr>
	<tr>
		<th><b>Channel Level</b></th>
		<th></th>
		<th></th>
		<th></th>
    <th></th>
	</tr>
  <tr>
		<th><b>Web to App</b></th>
		<td><a href="/dashboard/channel-level-access/#journeys-banners">Journeys Banners</a></td>
		<td><a href="/dashboard/channel-level-access/#deepviews">Deepviews</a></td>
		<td><a href="/dashboard/channel-level-access/#desktop-sms">Desktop SMS</a></td>
    <td></td>
	</tr>
	<tr>
		<th><b>Ads</b></th>
		<td><a href="/dashboard/channel-level-access/#partner-management">Partner Management</a></td>
    <td></td>
		<td></td>
    <td></td>
  </tr>
	<tr>
		<th><b>Email</b></th>
		<td><a href="/dashboard/channel-level-access/#email-manager">Email Manager</a></td>
		<td></td>
    <td></td>
    <td></td>
  </tr>
	<tr>
		<th><b>Organic Search</b></th>
		<td><a href="/dashboard/channel-level-access/#organic-search">Organic Search</a></td>
		<td></td>
    <td></td>
    <td></td>
  </tr>
	<tr>
		<th><b>Referrals</b></th>
		<td><a href="/dashboard/channel-level-access/referrals-reward-rules">Reward Rules</a></td>
		<td></td>
    <td></td>
    <td></td>
  </tr>
	<tr>
		<th><b>Data Import & Export</b></th>
		<td><a href="/dashboard/channel-level-access/#data-feeds-manager">Data Feeds Manager</a></td>
		<td><a href="/dashboard/channel-level-access/#data-integrations">Data Integrations</a></td>
    <td><a href="/dashboard/channel-level-access/#webhooks">Webhooks</a></td>
    <td></td>
  </tr>
</table>

## Web to App

### Journeys Banners

If you are an Admin, you have edit access to the <notranslate>**Manager**</notranslate> tab.

You can turn Journeys on and off, clone them, or view performance.

![image](/images/pages/journeys/journeys-manager.png)

A Journey can have one of four states:

| State | Meaning | Next Stage |
| --- | --- | --- |
| `Draft` | Not yet published, editable | <notranslate>**Active**</notranslate> |
| `Active` | Live for your users, editable | <notranslate>**Stopped**</notranslate> |
| `Stopped` | Not live for your users, editable | <notranslate>**Active**</notranslate> or <notranslate>**Archived**</notranslate> |
| `Archived` | Not live for your users, editable | _none_ |

You can activate a journey directly from the creation flow, or from <notranslate>**Start**</notranslate> in the Actions menus in the Journeys Manager.

![image](/images/pages/journeys/edit-journeys.png)

[block:callout]
{
  "type": "tip",
  "title": "Editing a live Journey",
  "body": "You may edit Journeys in all states; if you do, however, your Journeys' performance and analytics may change. If you do decide to make a change, we recommend making a note of what you changed and when you made the change."
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "Creating a Journeys Banner",
  "body": "Please refer to the [Journeys App Banners](/web/journeys/) article for an in-depth tutorial on how to create a Journeys Banner."
}
[/block]

### Deepviews

If you are an Admin, you have edit access to the <notranslate>**Deepviews**</notranslate> section.

You can create new Deepview templates either by duplicating the default Branch Public Template, or by creating a new one from scratch. New Deepview templates are shared between all platforms (iOS, Android, and desktop), and cannot be deleted after creation.

![image](/images/pages/dashboard/access-levels/channel-deepviews.png)

[block:callout]
{
  "type": "info",
  "title": "Creating a Deepview",
  "body": "Please refer to the [Deepviews](/web/deep-views/) article for an in-depth tutorial on how to create a Deepview."
}
[/block]

### Desktop SMS - Text Me the App

When users click your links on desktop, they have the option to text themselves a link to download your app. We provide this by default on every Branch link, but you can also create your own fully-branded Text Me The App page.

![image](/images/pages/text-me-the-app/default-and-drafted.png)

Left: Branch default. Right: a customized version.

[block:callout]
{
  "type": "info",
  "title": "Text Me the App",
  "body": "Please refer to the [Text Me the App](/web/text-me-the-app/) article for an in-depth tutorial on how to create a Text Me the App page."
}
[/block]

## Ads

### Partner Management

If you are an Admin, you have edit access to the <notranslate>**Partner Management**</notranslate> tab.

![image](/images/pages/dashboard/access-levels/app-partner-management.gif)

Each Universal Ad Partner has the following settings:

- <notranslate>**Account Settings**</notranslate>
    - Partner Credentials; e.g. API Key, SDK Key, Security Token.
- <notranslate>**Postback Config**</notranslate>
    - Partner supported postback templates per conversion type
- <notranslate>**Link Parameters**</notranslate>
    - Parameters added to the Partner's link by default; not editable.
- <notranslate>**Attribution Windows**</notranslate>
    - Use a custom attribution window to match AdAction Engage's attribution windows. This overrides your app level attribution windows.

[block:callout]
{
  "type": "info",
  "title": "Enabling an Ad Partner",
  "body": "Please refer to Branch's [List of Universal Ad Partners](/deep-linked-ads/ad-networks-list/) to view a complete list of our integrated Universal Ad Partners and instructions on how to enable each partner."
}
[/block]

## Email

### Email Manager

If you are an Admin, you have edit access to the <notranslate>**Manager**</notranslate> tab.

You can enable/disable Universal Email Partners and view integration information.

![image](/images/pages/dashboard/access-levels/channel-email-manager.gif)

[block:callout]
{
  "type": "info",
  "title": "Enabling an Universal Email Partner",
  "body": "Please refer to Branch's [List of Universal Email Partners](/emails/email-partners-list/) article to view a complete list of our integrated Universal Email Partners and instructions on how to enable each partner."
}
[/block]

## Organic Search

[block:callout]
{
  "type": "warning",
  "title": "Aggregate Data Access Required",
  "body": "Access to the Organic Search section also requires access to [Aggregate Data](aggregate-data-access.md)"
}
[/block]

Enable automatic sitemap generation by checking the <notranslate>**Automatic sitemap generation**</notranslate> checkbox.

![image](/images/pages/organic-search/firebase/db-settings.png)

Once you enable this, your app will be included in our nightly job to automatically generate sitemaps. These sitemaps can be scraped by Google, and all of the included links can then be indexed.

After you've enabled App Indexing, this page will showcase the following data:

1. The date the sitemap files were last generated (and included at least one of your links)
2. The total number of links to unique pieces content that Branch has included in sitemaps
3. The date Google last scraped your links
4. The total number of times that Google has scraped links to your content

Both the sitemap itself and statistics about Google scraping your links are updated via nightly map-reduce jobs.

![image](/images/pages/dashboard/access-levels/channel-organic-search.png)

[block:callout]
{
  "type": "info",
  "title": "Google App Indexing & Apple Spotlight Search",
  "body": "Please refer to the [Firebase App Indexing](/organic-search/firebase/) article for an in-depth tutorial on Google's Firebase App Indexing ."
}
[/block]

	Please refer to the [Spotlight Search](/organic-search/spotlight/) article for an in-depth tutorial on Apple's Spotlight Search.

## Referrals

If you are an Admin, you have edit access to the <notranslate>**Reward Rules**</notranslate> tab.

### Reward Rules

You can create new rules, edit existing rules and archive unwanted rules.

You can automatically give awards based on events taken by users.

![image](/images/pages/dashboard/access-levels/channel-referral-rewards.gif)

Properties you can define:

1. Who gets a reward
1. How many credits the reward is
1. Which `bucket` the credits go to
1. Whether the reward occurs the first time or every time
1. Which event triggers the reward

[block:callout]
{
  "type": "warning",
  "title": "Promo codes has been deprecated",
  "body": "Our Promo codes feature on the dashboard has been deprecated. Please use reward rules to trigger referral rewards for your users."
}
[/block]

[block:callout]
{
  "type": "info",
  "title": "Example Reward Rules",
  "body": "Please refer to the [Referral Programs](/viral/referrals/) article for examples and a sample iOS app."
}
[/block]

## Data Import & Export

If you are an Admin, you have edit access to the sections below.

### Data Feeds Manager

[block:callout]
{
  "type": "warning",
  "title": "Sensitive Data Access Required",
  "body": "Access to the Data Feeds Manager tab also requires access to [Sensitive Data](sensitive-data-access.md)."
}
[/block]

![image](/images/pages/dashboard/access-levels/channel-data-feeds-manager.png)

- <notranslate>**Daily Export API**</notranslate> - Programmatically access Branch event data with granular details like timestamp, OS, and more.
- <notranslate>**Query API**</notranslate> - Programmatically query for any of the pre-aggregated Branch event data that you can see on the dashboard.

### Data Integrations

[block:callout]
{
  "type": "warning",
  "title": "Sensitive Data Access Required",
  "body": "Access to the Data Feeds Manager tab also requires access to [Sensitive Data](sensitive-data-access.md)."
}
[/block]

![image](/images/pages/dashboard/access-levels/channel-data-integrations.png)

[block:callout]
{
  "type": "info",
  "title": "Enabling a Data Integration",
  "body": "Please refer to Branch's [List of Data Integrations](/integrations/data-integrations-list/) article to view a complete list of our Data Integrations and instructions on how to enable each integration."
}
[/block]

### Webhooks

[block:callout]
{
  "type": "warning",
  "title": "Sensitive Data Access Required",
  "body": "Access to the Data Feeds Manager tab also requires access to [Sensitive Data](sensitive-data-access.md)."
}
[/block]

You can add new webhooks, edit existing webhooks and archive unwanted webhooks.

![image](/images/pages/dashboard/access-levels/channel-webhooks1.png)

[block:callout]
{
  "type": "info",
  "title": "Webhook Setup",
  "body": "Please refer to the [Webhooks](/exports/ua-webhooks/) article for an in-depth tutorial on how to configure webhooks."
}
[/block]
