---
title: Organization View
---
The <notranslate>"Organization"</notranslate> view of a Branch account is an additional level of entity access and is intended for Branch accounts with a portfolio of distinctly managed apps tied to a single organizational entity. Organization view allows companies to manage separate teams associated with their distinct apps and maintain autonomy. Organization team members can switch between the Organization view and the App view at any time.

[block:callout]
{
  "type": "info",
  "title": "INFO",
  "body": "Depending on your business and how you manage your apps, you may elect to add the Organization Entity to your Branch account."
}
[/block]

    All TUNE migrated accounts include the Organization entity in their Branch account.

**The Organization view is for managing account-level functionality; e.g. managing org team members and access.  Toggle to the [App view](app-view.md) to access the majority of your day-to-day needs for creating links and viewing reporting.**

## Organization View Overview

When viewing your Branch account via the Organization entity, you can access (either edit or read-only) the following functionality:

<table>
  <tr>
    <th rowspan="6"><img src="/images/pages/dashboard/access-levels/org-level-nav.png"></th>
  </tr>
	<tr>
		<th></th>
		<th></th>
		<th></th>
		<th></th>
    <th></th>
    <th></th>
	</tr>
	<tr>
		<th><b>Org Entity Access</b></th>
		<th></th>
		<th></th>
		<th></th>
    <th></th>
    <th></th>
	</tr>
  <tr>
		<th><b>Ads</b></th>
		<td><a href="/dashboard/organization-level-access/#partner-management">Partner<br/>Management</a></td>
		<td></td>
		<td></td>
    <td></td>
    <td></td>
	</tr>
	<tr>
		<th><b>Link<br/>Settings</b></th>
		<td><a href="/dashboard/organization-level-access/#attribution-windows">Attribution<br/>Windows</a></td>
    <td></td>
		<td></td>
    <td></td>
    <td></td>
  </tr>
	<tr>
		<th><b>Account<br/>Settings</b></th>
		<td><a href="/dashboard/organization-level-access/#managing-your-organization-profile">Profile</a></td>
		<td><a href="/dashboard/organization-level-access/#managing-your-user-profile">User</a></td>
    <td><a href="/dashboard/organization-level-access/#managing-your-organizations-team">Team</a></td>
    <td><a href="/dashboard/organization-level-access/#managing-agency-access">Agencies</a></td>
    <td><a href="/dashboard/organization-level-access/#single-sign-on">SSO</a></td>
  </tr>
</table>

## Ads

### Partner Management

[block:callout]
{
  "type": "info",
  "title": "COMING SOON",
  "body": "Allow enabling and editing of ad networks at the org level."
}
[/block]

## Link Settings

### Attribution Windows

[block:callout]
{
  "type": "info",
  "title": "Default Attribution Window Settings",
  "body": "Each attribution window has its own default measured in days.  Please refer to the image below for these defaults."
}
[/block]

![image](/images/pages/dashboard/people-based-attribution/attribution-windows.png)

- <notranslate>**Deep Linking Duration**</notranslate> refers to the duration of time someone is eligible to receive deep link data. This includes anyone clicking a Branch link, or being automatically redirected to the app through a Branch Web SDK call. Measured in minutes.

- <notranslate>**Click to x**</notranslate> refers to events that occur after someone clicks a Branch link. If someone clicks and installs from a link, and comes back 10 days later to purchase, we would count that as a conversion, and it would surface in our dashboard. Measured in days.

- <notranslate>**Impression to x**</notranslate> refers to events that occur after someone views a Branch impression link. Measured in days.

- `Re-engagement Inactivity` defines the period between two events that a user must be inactive in order to define the later event as a re-engagement. Used in re-engagement cohort analysis but not activity analysis.

## Account Settings

### Managing your Organization Profile

![image](/images/pages/dashboard/access-levels/org-profile.png)

If you are an Organization Admin, you have edit access to the <notranslate>**Profile**</notranslate> tab.

- <notranslate>**Organization Name**</notranslate> - provided by you; editable.
- <notranslate>**Organization ID**</notranslate> - assigned by Branch; not editable.
- <notranslate>**Time Zone**</notranslate> - Your time zone affects your dashboard analytics and how your Branch data matches up with external data sources. Use the drop-down to select the appropriate time zone.

### Managing your User Profile

![image](/images/pages/dashboard/access-levels/org-level-user.png)

Any user type - Admin, Team Member, Full Read, Limited Read - has the ability to edit the <notranslate>**User**</notranslate> tab.

- <notranslate>**Dashboard UID**</notranslate> - assigned by Branch; not editable.
- <notranslate>**Access Token**</notranslate> - assigned by Branch; resettable.
- <notranslate>**First and Last Names**</notranslate> - provided by you; editable.
- <notranslate>**Email Address**</notranslate> - provided by you; editable.
- <notranslate>**Update Password**</notranslate> - provided by you; editable.

### Managing Your Organization's Team

If you are an Organization Admin, you have edit access to the <notranslate>**Team**</notranslate> tab.

#### Adding an Organization User

![image](/images/pages/dashboard/access-levels/org-team-add.gif)

To add a new Organization User:

1. Click the <notranslate>**Add Organization Team Member**</notranslate> button.
2. In the <notranslate>**Add Organization Team Member**</notranslate> modal:
	1. Provide the user's <notranslate>**Email Address**</notranslate>
	1. Provide the user's <notranslate>**First**</notranslate> and <notranslate>**Last**</notranslate> names
	1. Select the appropriate <notranslate>**Access Level**</notranslate>
		- <notranslate>**Admin**</notranslate> - Edit access to all settings and export access to all data.
		- <notranslate>**Team Member**</notranslate> - Edit access to channels and links, read-only access to app settings, and access to aggregate data.
		- <notranslate>**Full Read**</notranslate> - Read-only access to all settings and access to aggregate data.
		- <notranslate>**Limited Read**</notranslate>  - Access to aggregate data only.
		- <notranslate>**Custom**</notranslate> - Customize settings and data access.
		- <notranslate>**No Access**</notranslate> - no dashboard access.
  1. Check the <notranslate>**Export**</notranslate> box if you want to allow the user to export sensitive data from pages they can view.
	1. Click <notranslate>**Invite**</notranslate>.
  1. In the <notranslate>**Organization Settings**</notranslate> modal, select either:
    - All apps that inherit from the organization
    - All apps
  1. Click <notranslate>**Save**</notranslate>

#### Defining Permissions

Each access level - as defined above - comes with predefined permissions which you can edit if you choose.

[block:callout]
{
  "type": "tip",
  "title": "Modifying Permissions",
  "body": "If you want to modify a predefined access level, click the pencil icon to (de)select the available options."
}
[/block]

- <notranslate>**Link-level Settings**</notranslate> - Settings or features that can impact functionality for single links.
- <notranslate>**Channel-level Settings**</notranslate> - Settings or features that can impact functionality across a marketing channel.
- <notranslate>**App-level Settings**</notranslate> - Settings or features that can impact functionality app-wide.
- <notranslate>**Aggregate Data**</notranslate> - Summary data that contains no granular data.
- <notranslate>**Sensitive Data**</notranslate> - Data that can contain user-identifying, payment-related, or secret information.
- <notranslate>**Fraud Settings & Data**</notranslate> - Settings or data associated with fraud detection and prevention.

#### Modifying an Organization Team Member

![image](/images/pages/dashboard/access-levels/org-team-edit.png)

To modify an existing Organization Team Member:

1. Find the Organization Team member you want to modify and click the <notranslate>**...**</notranslate> button in the <notranslate>**Actions**</notranslate> column for that user.
1. To edit the Organization Team member:
	1. Click <notranslate>**Edit**</notranslate> and modify any of the following:
		- Email
		- First and Last names
		- Access Level
	1. Click <notranslate>**Save**</notranslate>.
1. To resend the invitation to join the account:
	1. Click <notranslate>**Resend Invite**</notranslate>.
1. To delete the Organization Team member:
	1. Click <notranslate>**Delete**</notranslate>.
	1. In the <notranslate>**Are you sure you want to delete?**</notranslate> modal, click <notranslate>**Yes, Delete**</notranslate>.

### Managing Agency Access

If you are an Organization Admin, you have full edit access to all of the Account Settings mentioned above including the ability to add an Agency - both a Full Access and/or Limited Access Agency - to your Branch account.

[block:callout]
{
  "type": "info",
  "title": "Additional Info",
  "body": "You can only add agencies via the <notranslate>**Agencies**</notranslate> tab. Trying to add agencies via the <notranslate>**Team**</notranslate> tab will throw an error as only non-agency users should be added via the Team Tab."
}
[/block]

#### Adding an Agency

To add an Agency:

1. Go to <notranslate>**Account Settings**</notranslate> and click on the <notranslate>**Agencies**</notranslate> tab.
1. On the <notranslate>**Agencies**</notranslate> tab, click the <notranslate>**Add New Agency**</notranslate> button.
1. In the <notranslate>**Add New Agency**</notranslate> modal:
	1. Select the Agency name from the drop-down.
	1. Select the appropriate level of access.
		- <notranslate>**Admin**</notranslate> - Edit access to all settings and export access to all data.
		- <notranslate>**Team Member**</notranslate> - Edit access to channels and links, read-only access to app settings, and access to aggregate data.
		- <notranslate>**Full Read**</notranslate> - Read-only access to all settings and access to aggregate data.
		- <notranslate>**Limited Read**</notranslate>  - Access to aggregate data only.
		- <notranslate>**Custom**</notranslate> - Customize settings and data access.
		- <notranslate>**No Access**</notranslate> - no dashboard access.
	1. Click "Invite".
	1. All Agency Admins on the agency account will receive an invitation email, and any of those Agency Admins can accept the invitation on behalf of their agency.

[block:callout]
{
  "type": "warning",
  "title": "Granting agencies Sensitive Data & App-Level Settings permissions",
  "body": "Agencies with Sensitive Data & App-Level Settings permissions to an Org or App will have access to that Org/App's API keys, which can be used to access Branch's [HTTP](https://docs.branch.io/apps/deep-linking-api/) and [Data Export](https://docs.branch.io/exports/api-v3/#__search) APIs. Agency data filters (e.g. Only Show Agency-tagged Data) will not apply to data accessed via the Daily Export API, so we recommend against granting agencies these permissions and providing them with API keys."
}
[/block]

#### Defining Permissions

Each access level - as defined above - comes with predefined permissions which you can edit if you choose.

[block:callout]
{
  "type": "tip",
  "title": "Modifying Permissions",
  "body": "If you want to modify a predefined access level, click the pencil icon to (de)select the available options."
}
[/block]

- <notranslate>**Link-level Settings**</notranslate> - Settings or features that can impact functionality for single links.
- <notranslate>**Channel-level Settings**</notranslate> - Settings or features that can impact functionality across a marketing channel.
- <notranslate>**App-level Settings**</notranslate> - Settings or features that can impact functionality app-wide.
- <notranslate>**Aggregate Data**</notranslate> - Summary data that contains no granular data.
- <notranslate>**Sensitive Data**</notranslate> - Data that can contain user-identifying, payment-related, or secret information.
- <notranslate>**Fraud Settings & Data**</notranslate> - Settings or data associated with fraud detection and prevention.

#### Additional Data Filters

During the process of granting an agency access to your Branch account, you can also impose limitations around what data is available to the agency at any given time.

- <notranslate>**Only Show Agency-tagged Data**</notranslate> - When toggled on, agency users can only see events tagged with their Agency ID.
- <notranslate>**Restrict Access to Revenue Data**</notranslate> - When toggled on, agency users cannot view revenue data.
- <notranslate>**Only Show Data from Specific Ad Networks**</notranslate> - When toggled on, agency users can only view events from a specific list of ad networks.
- <notranslate>**Only Show Data from Specific Locations**</notranslate> - When toggled on, agency users can only view events that have taken place in a specific list of countries.

[block:callout]
{
  "type": "warning",
  "title": "Agency Invitation",
  "body": "Once you've defined the appropriate levels of access for your Agency, you must <notranslate>**Invite**</notranslate> them to access the Branch dashboard. Only Organization Admins can invite an Agency to access the Branch dashboard."
}
[/block]

#### Modifying an Agency Team Member

To modify an existing Agency Team member:

1. Find the Agency Team member you want to modify and click the <notranslate>**...**</notranslate> button in the <notranslate>**Actions**</notranslate> column for that user.
1. To edit the Agency member:
	1. Click <notranslate>**Edit**</notranslate> and modify any of the following:
		- Email
		- First and Last names
		- Access Level
	1. Click <notranslate>**Save**</notranslate>.
1. To resend the invitation to join the Agency account:
	1. Click <notranslate>**Resend Invite**</notranslate>.
1. To delete the Agency member:
	1. Click <notranslate>**Delete**</notranslate>.
	1. In the <notranslate>**Are you sure you want to delete?**</notranslate> modal, click <notranslate>**Yes, Delete**</notranslate>.

### Single Sign On

Branch offers Security Assertion Markup Language (SAML) / Single Sign-on (SSO) support for the dashboard. This allows you to use your identity provider (IdP) to centralize access to various services for your team and leverage existing directory systems and security groups.

Please see [Enabling Single Sign On](/dashboard/sso/) for instructions.
