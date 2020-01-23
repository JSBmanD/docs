### Create an ad link

Once you've enabled an integration it's time to create a tracking link.

1. First, select an ad format. For App Install or App Engagement campaigns you'll want to select the <notranslate>**App Only**</notranslate> format. For Search or Display campaigns where the user should go to web if they don't have the app, then you should select <notranslate>**Cross-Platform Search**</notranslate> or <notranslate>**Cross-Platform Display**</notranslate>. <notranslate>**Product Links**</notranslate> are for shopping or dynamic remarketing campaigns.

    ![image](/_assets/img/pages/deep-linked-ads/branch-universal-ads/create-link.png)

1. At this point you need to name your link. Select something that will make it easy to find if you need it later. Your Ad Format and Ad Partner should be selected already, but feel free to choose one if they aren't. It's important that you select the right Ad Partner for analytics later on. Click <notranslate>**Configure Options**</notranslate> to continue.

    ![image](/_assets/img/pages/deep-linked-ads/branch-universal-ads/create-link-name.png)

1. In the Deep Linking tab of the link creator make sure to add the following key-value pairs, based on which platform the link is going to be used for. If these values are not added to the link, myTarget will block your links.

	Key | Value
	--- | ---
	`$uri_redirect_mode` | 0
	`$always_deeplink` | false

	![image](/_assets/img/pages/deep-linked-ads/aura-ironsource/aura-ironsource-link-data.png)


1. This is your chance to add deep link data and analytics tags. Analytics tags are important for later segmentation, so click the <notranslate>**Analytics**</notranslate> sub tab to add a Channel and Campaign value.

    ![image](/_assets/img/pages/deep-linked-ads/branch-universal-ads/create-link-tags.png)

    !!! tip "Set Analytics tags"

        It's easier to slice your data in our analytics platform if you properly assign analytics parameters to your link. <notranslate>_Channels_</notranslate> generally correspond to ad networks, and <notranslate>_Campaigns_</notranslate> correspond to marketing initiatives that you're launching. For example: <notranslate>_Channel_</notranslate>: "YouTube", <notranslate>_Campaign_</notranslate>: "Summer 2017 Shoe Discounts."

1. Click <notranslate>**Create Link Now**</notranslate>, and you have your tracking link! Take this link and give it to your Ad Partner's Account Manager or paste it into the tracking section of your campaign yourself.

    ![image](/_assets/img/pages/deep-linked-ads/branch-universal-ads/create-link-completed.png)

	!!! tip "Server to server tracking links"
		If you just need a server to server tracking link just add `%24s2s=true` at the end of your link, so we know it's a server to server link.
