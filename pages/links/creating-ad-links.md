---
title: Creating Ad Links
---
## Overview

A Branch link is the vehicle that ensures seamless user experiences while also providing you with full attribution and analytics across email, referrals, paid advertising, social, organic search, and desktop to mobile.

If you are running paid advertising campaigns, you'll want to create a Branch Ad link so we can accurately attribute resulting app conversions to the appropriate advertising partner. Branch Ad Links support deferred deep linking, Android App Links and iOS Universal Links, as well as web and app conversions.

!!! warning "Migrated TUNE Clients only"
	If you are a migrated TUNE client creating links in your Branch account - and do not have the Branch SDK implemented in your app - you *must* have at least the following versions of the TUNE SDK - **Android v6.0.3 & iOS v6.0.4** - in your app to ensure the TUNE SDK can attribute Branch links.

## Creating an Ad Link

!!! warning "Enabled Ad Partner Required"
	As all Branch Ad Links are uniquely built to a specific advertising partner, you can only create an Ad link for enabled ad partners.

To create a Branch Ad Link:

1. From within the Ads section in your Branch dashboard, click <notranslate>**Create Ad Link**</notranslate> in the upper right-hand corner.

### Selecting Ad Format Types

1.  In the <notranslate>**Create Ad Link**</notranslate> modal, select one of the following ad formats:
	- App Install or Engagement
	- Create Display Link
	- Create Product Link
	- Create Search Link

	!!! tip "Format Types"
		For App Install or App Engagement campaigns you'll want to select the App Only format. For Search or Display campaigns where the user should go to web if they don't have the app, then you should select Cross-Platform Search or Cross-Platform Display. Product Links are for shopping or dynamic remarketing campaigns and will take you to create a Deep Linked Product Feed.

	![image](/_assets/img/pages/deep-linked-ads/branch-universal-ads/create-link.png)

1. Click <notranslate>**Continue**</notranslate>.

### Defining Ad Link Domain & Ad Partner

1. In the <notranslate>**Define**</notranslate> section, please provide the following:
	- Choose which link domain you want to use (available for ex-TUNE clients only):
		- <notranslate>**Branch domain**</notranslate> - Create a link using your Branch domain. Note that links created with this domain will use Branch link parameters by default.
		- <notranslate>**TUNE domain**</notranslate> - Create a link using your TUNE domain. Note that links created with this domain will use TUNE link parameters/macros by default.
	- Name Your Link
	- Select the ad partner the link is for

	![image](/_assets/img/pages/links/ad-link-define.png)

### Configuring Options

1. Click <notranslate>**Configure Options**</notranslate>.
1. In the <notranslate>**Configure Options**</notranslate> section, please provide the following:
	- Define your <notranslate>**Link Alias**</notranslate>; this cannot be changed after you create the ad link.
	- Provide any of the following if applicable:
		- <notranslate>**Deep Linking**</notranslate>
		- <notranslate>**Redirects**</notranslate>
		- <notranslate>**Analytics Tags**</notranslate>

		![image](/_assets/img/pages/links/ad-link-configure-options.gif)

1. Click <notranslate>**Create Link Now**</notranslate>.

#### Deep Linking

The <notranslate>**Deep Linking**</notranslate> tab allows you to include additional data to your links to be used not only for contextual deep linking, but for passing additional attributes you or your ad partner may require.

To add additional data - i.e. key-value pairs - to your Ad Link:

1. Click <notranslate>**+More Data**</notranslate>.
1. Input the parameter name in the <notranslate>**Key**</notranslate> field, and it's corresponding value or macro in the <notranslate>**Value**</notranslate> field.

![image](/_assets/img/pages/links/ad-link-deep-linking.png)

!!! tip "Available Parameters"
	For a full list of available parameters you can include in your Ad Link, refer to [TUNE <> Branch Mapped Fields](https://support.branch.io/support/solutions/articles/6000216765-tune-branch-mapped-fields).

!!! info "Force Open the App"
	If you want to force the app to open, even if it risks showing an error message when the app is not installed, add `uri_redirect_mode` in the <notranslate>**Key**</notranslate> field and `2` in the <notranslate>**Value**</notranslate> field.

	**NOTE**: By adding this key-value pair, only those who click on this link will have the app forced open regardless. For links created on the TUNE domain, attach your `invoke_url` key with URL encoded URI scheme value (e.g. `invoke_url=branchsters%3A%2F%2F`) and set your app-level URI redirect mode to 'Aggressive'.

#### Redirect

The <notranslate>**Redirect**</notranslate> tab allows you to override your default redirects - as set in <notranslate>**Link Settings**</notranslate> - and direct users to specific locations if the app is not installs.

- <notranslate>**Default Redirect**</notranslate> - Set at the account level within Link Settings. Typically set to the relevant mobile stores

- <notranslate>**Web URL**</notranslate> - Send users to a specific web page if they don’t have to the app to avoid any unexpected flow to the app store

- <notranslate>**Deepview**</notranslate> - Send users to a specific deepview you may have created under the <notranslate>**Web to App > Deepview**</notranslate> section. Copy the key and paste it into the text box. Useful if you want to present the user with a preview of the content before taking them directly to the app store. Should not be set for Desktop option.

!!! info "Force Open the App"
	If you want to always force the app to open, even if it risks showing an error message when the app is not installed, make sure the <notranslate>**URI Scheme Deep Link Mode**</notranslate> in your <notranslate>**Link Settings**</notranslate> is set to `Aggressive`.

	**NOTE**: By changing this setting, Branch will force open the app for all users. Available for links created on both the Branch and TUNE domain.

#### Analytics Tags

!!! tip "Set Analytics tags"
	It's easier to slice your data in our analytics platform if you properly assign analytics parameters to your link. <notranslate>_Channels_</notranslate> generally correspond to ad networks, and <notranslate>_Campaigns_</notranslate> correspond to marketing initiatives that you're launching. For example: <notranslate>_Channel_</notranslate>: "YouTube", <notranslate>_Campaign_</notranslate>: "Summer 2017 Shoe Discounts."

## Validating Your Ad Link

Once you've created your Ad link, we will automatically validate it's settings to make sure your link works as you expect.

If we recognize an issue with your ad link, you will see an error message with what needs to be fixed before sharing your link.

![image](/_assets/img/pages/links/ad-link-validation.png)

Click on the error message to go back and fix the offending setting.

Once no issues exist, you should only see green checks next to your links settings.

## Sharing Your Ad Link

We provide you with a Branch link for both clicks and impressions.  Simply copy and paste the links in the tracking section of your campaign tool or email to your Ad Partner's account manager.

![image](/_assets/img/pages/links/ad-link-share.png)

You can also text yourself (or someone else) the link by providing a phone number and clicking <notranslate>**Send**</notranslate>.
