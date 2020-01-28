---
title: Link Level Access
---
The <notranslate>"Link"</notranslate> level of a Branch account is the fourth level of access and includes access (either edit or read-only) to the following functionality:

<table>
  <tr>
    <th rowspan="5"><img src="/images/pages/dashboard/access-levels/org-level-nav.png"></th>
  </tr>
	<tr>
		<th></th>
		<th></th>
		<th></th>
		<th></th>
    <th></th>
	</tr>
	<tr>
		<th><b>Link Level</b></th>
		<th></th>
		<th></th>
		<th></th>
    <th></th>
	</tr>
  <tr>
		<th><b>Ads</b></th>
		<td><a href="/dashboard/link-level-access/#links">Links</a></td>
		<td></td>
		<td></td>
    <td></td>
	</tr>
	<tr>
		<th><b>Channels & Links</b></th>
		<td><a href="/dashboard/link-level-access/#quick-links">Quick Links</a></td>
    <td></td>
		<td></td>
    <td></td>
  </tr>
</table>

## Ads

### Links

If you are an Admin, you have edit access to the following tabs in the <notranslate>**Links**</notranslate> section.

#### Ad Links

You can create new ad links, as well as edit/duplicate/archive current ad links.

![image](/images/pages/dashboard/access-levels/link-ad-links.png)

[block:callout]
{
  "type": "info",
  "title": "Creating an Ad Link",
  "body": "Please refer to any [Universal Ads Partner Integration](/deep-linked-ads/1plusads-mobile-tracking/#create-an-ad-link) article for an in-depth tutorial on how to create an ad link."
}
[/block]

## Channels & Links

### Quick Links

[block:callout]
{
  "type": "warning",
  "title": "Aggregate Data Access Required",
  "body": "Access to the Quick Link Export functionality also requires access to [Aggregate Data](aggregate-data-access.md)"
}
[/block]

If you are an Admin, you have edit access to the <notranslate>**Quick Links**</notranslate> section.

![image](/images/pages/dashboard/access-levels/link-quick-links.png)

You can create new Quick Links, as well as edit/view stats/debug/duplicate/archive existing quick links.

[block:callout]
{
  "type": "info",
  "title": "Creating a Quick Link",
  "body": "Please refer to the [Creating Quick Links](/links/quick-links/) article for an in-depth tutorial on how to create quick links."
}
[/block]

#### Bulk Create Links

[block:callout]
{
  "type": "warning",
  "title": "Aggregate Data Access Required",
  "body": "Access to the Quick Link Export functionality also requires access to [Aggregate Data](aggregate-data-access.md)"
}
[/block]

![image](/images/pages/dashboard/access-levels/link-bulk-create.png)

To create quick links in bulk:

1. Click the <notranslate>**Bulk Create Links**</notranslate> button.
1. Select your CSV that includes the following for each quick link:
	- campaign
	- channel
	- feature
	- stage
	- tags
	- alias
	- data
		- $marketing_title
		- $og_description
1.  Click <notranslate>**Create Links**</notranslate>

#### Export

[block:callout]
{
  "type": "warning",
  "title": "Aggregate Data Access Required",
  "body": "Access to the Quick Link Export functionality also requires access to [Aggregate Data](aggregate-data-access.md)"
}
[/block]

![image](/images/pages/dashboard/access-levels/link-export-csv.png)

To export your existing quick links:

1. Click the <notranslate>**Export**</notranslate> button.
1. Provide the following:
	- Time Range
	- Interval
1. Click <notranslate>**Export CSV**</notranslate>
