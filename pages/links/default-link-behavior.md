---
title: Default Link Behavior Configuration
---
- ### Configure default behavior

    - Set the default behavior for your deep links on [Link Settings](https://dashboard.branch.io/link-settings)

    - These values are typically overridden by [Custom link behavior](/links/integrate/#custom-link-behavior) for each deep link

    - ##### iOS

        - Use these settings to control the default behavior of your deep links on iOS

            ![image](/images/pages/dashboard/ios.png)

        - The Apple App Prefix is found within the [Apple Developer Portal](https://developer.apple.com/account/ios/identifier/bundle) for your app

        [block:callout]
        {
          "type": "warning",
          "title": "App Store Redirect on < iOS 12.3",
          "body": "
          For any user running on an iOS version below 12.3, a popup first appears prompting the user to open in the App Store when being redirected to the app store. The user must click <notranslate>**OK**</notranslate> to be fully routed to the App Store to download your app.  This popup cannot be removed from the user flow as it's inherent to iOS.

          ![image](/images/pages/links/app-store-redirect.png)"
        }
        [/block]

    - ##### Android

        - Use these settings to control the default behavior of your deep links on Android

        - Play Store is for published apps, if your app cannot be located or is a local/dev build, please use the Custom URL option

            ![image](/images/pages/dashboard/android.png)

        - Generate a SHA256 Cert Fingerprint
            - Navigate to your `keystore file` (used to build the debug and production version of your APK file before it gets deployed)
            - Run `keytool -list -v -keystore my-release-key.keystore` to generate a fingerprint

            - Example fingerprint `AA:C9:D9:A5:E9:76:3E:51:1B:FB:35:00:06:9B:56:AC:FB:A6:28:CE:F3:D6:65:38:18:E3:9C:63:94:FB:D2:C1` to add to your [Branch Dashboard](https://dashboard.branch.io/link-settings)

    - ##### Desktop

        [block:callout]
{
  "type": "info",
  "title": "We now support deep linking to Desktop apps via URI schemes",
  "body": "Our beta Mac OS Desktop SDK is available for testing, so please contact your Branch Account Manager or integrations@branch.io for more information."
}
[/block]

        - Use these settings to control the default behavior of your deep links on Desktop browsers

            ![image](/images/pages/dashboard/desktop.png)

        - For Desktop apps
            - Enter your Desktop URI Scheme (e.g. `your_desktop_uri_scheme://`)
            - Include `$desktop_deeplink_path` key-value pair to your link (e.g. `"$desktop_deeplink_path": "track/5D8o9tGf3Dfjz7CgMxcoeI"`)
            - If the app is not installed when the link is clicked, we will fall back to the Desktop or Default URL, in that order
            - This feature is still in the early stages of development; so usage without a Desktop SDK will not be able to attribute or pass data through an install.

    - ##### Fallback
        - Use these settings to control the default behavior of your deep links on any other platform

            ![image](/images/pages/dashboard/fallback.png)

    - ##### Link domain
        - Choose a `link domain` which will be used for all your links
        - The `link domain` is the website which hosts your deep links
        - The `link domain` is not a deep link
            - Deep links have an `alias` behind them to uniquely identify the link data inside them
                - e.g. https://example.app.link/VZsTctoINF
                - e.g. https://example.app.link/custom-alias

            ![image](/images/pages/dashboard/link-domain.png)

    - ##### Social media

        - Set the default image preview for your deep links when shared on social media
        - These values are typically overridden by [Custom link behavior](/links/integrate/#custom-link-behavior) which differentiate your deep links between one another

            ![image](/images/pages/dashboard/social-media.png)

    - ##### Save
        - Make sure you commit any changes

            ![image](/images/pages/dashboard/save.png)
