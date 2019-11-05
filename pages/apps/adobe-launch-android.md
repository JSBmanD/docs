Add the power of Branch deep linking and attribute to your Adobe Marketing Cloud app. With Branch's linking platform, mobile developers and marketers can grow their mobile business with world class deep linking and attribution.

!!! warning "Google Play Services version 17+"
    A major Google Play Services change made in June 2019 has caused Branch's Android SDK (and various other cross-platform SDKs, e.g. Unity) to stop collecting Android AID.

    To ensure Branch deep linking and attribution continue to work, you must follow Google's update instructions [here](https://developers.google.com/android/guides/releases#june_17_2019).

    If you are running Google Play Services versions below 17, no update is necessary.

## Features
1. All events tracked with the Adobe SDK will automatically be sent to Branch without any extra work
2. All core Branch functionality is accessible

## Requirements
- Android API level 16 or higher
- Adobe Core Platform

!!! warning "Branch SDK not Required"
    As the Adobe Branch extension is a wrapper that auto includes a sub-dependency for the Branch SDK, you do not need to - nor do we recommend to - implement the Branch SDK separately in your app.

## Example

An example app can be found in the AdobeBranchExtension-Android repository, in the `AdobeBranchExample`
project.

- [AdobeBranchExample Project](https://github.com/BranchMetrics/AdobeBranchExtension-Android/tree/master/AdobeBranchExample)
- [AdobeBranchExtension-Android Repository](https://github.com/BranchMetrics/AdobeBranchExtension-Android)

## Installation & Usage

Here's a brief outline of how to use the AdobeBranchExtension in your app:

1. You'll need to configure your app and get a Branch API key in the [Branch Metrics dashboard](https://branch.dashboard.branch.io/account-settings/app). You can read more about configuring your dashboard in the Branch docs here.

2. For application integration, you'll need to follow the instructions as described in the Branch docs here:
    - [Integrate Branch](/apps/android/)

3. For deep linking, you will need to add the Branch domains, app URI scheme and your Branch key to the manifest file for you app for deep linking.
    - [Configure your application with Branch key and for URI schemes](/apps/android/#configure-app)

4. In the Adobe dashboard, activate Branch and add your Branch key to your app's configuration.
    - Activate Branch:

    ![image](/_assets/img/pages/apps/adobe-launch-install.png)

5. Add the AdobeBranchExtension to your app's build.gradle.
    `implementation 'io.branch.sdk.android:adobebranchextension:1.+'`

6. Register the Branch `AdobeBranchExtension` with `MobileCore` in `configureWithAppID`:
```
    private static final String MY_ADOBE_APP_ID = "launch-{adobe app guid}-development";

    ...
    // Initialize the AdobeBranch SDK
    AdobeBranch.getAutoInstance(this);

    // Initialize the Adobe SDK
    MobileCore.setApplication(this);
    MobileCore.start(new AdobeCallback () {
        @Override
        public void call(Object o) {
            MobileCore.configureWithAppID(MY_ADOBE_APP_ID);
        }
    });

```
7. Intitialize Branch session and register BranchReferralInitListener in your launcher activity. You can see some [best practices on deep link routing in this doc](/deep-linking/routing/)
```
    AdobeBranch.initSession(new Branch.BranchReferralInitListener() {
            @Override
            public void onInitFinished(JSONObject referringParams, BranchError error) {
                try {
                    // Retrieve deep link params and route to content appropriately 
                    if (referringParams.has("+clicked_branch_link") && referringParams.getBoolean("+clicked_branch_link")) {
                            // Handle your Branch deep link routing in the callback
                        }
                    }
                } catch (JSONException e) {
                    // referringParams property doesn't exist
                } catch (NumberFormatException e) {
                    // internal error; id is not a number.
                }
            }
    }, getIntent().getData(), this);
```
## Implementing Branch Features

Once you've added the AdobeBranchExtension and Branch, you can always use Branch features directly. You can learn about using the Branch features here, in the Branch documentation for [Android.](/apps/android/)


### Automatic: Track Action and State
When you track actions and state in Adobe Launch, the action and state messages are sent to Branch too and shown on the
Branch dashboards. This allows you to track the effectiveness of deep link campaigns and viral sharing in your app's actions.

Here's an example of tracking app state via Adobe Launch:

    private void doPurchase(View view) {
        Long timestamp = System.currentTimeMillis()/1000;

        Map<String, Object> eventData = new HashMap<>();
        eventData.put(AdobeBranch.KEY_AFFILIATION, "Branch Metrics Company Store");
        eventData.put(AdobeBranch.KEY_COUPON, "SATURDAY NIGHT SPECIAL");
        eventData.put(AdobeBranch.KEY_CURRENCY, "USD");
        eventData.put(AdobeBranch.KEY_DESCRIPTION, model.getDescription());
        eventData.put(AdobeBranch.KEY_REVENUE, model.getPrice());
        eventData.put(AdobeBranch.KEY_SHIPPING, 0.99);
        eventData.put(AdobeBranch.KEY_TAX, (model.getPrice() * 0.077));
        eventData.put(AdobeBranch.KEY_TRANSACTION_ID, UUID.randomUUID().toString());

        eventData.put("category", "Arts & Entertainment");
        eventData.put("product_id", model.getId());
        eventData.put("sku", "sku-be-doo");
        eventData.put("timestamp", timestamp.toString());

        eventData.put("custom1", "Custom Data 1");
        eventData.put("custom2", "Custom Data 2");

        Event newEvent = new Event.Builder("PURCHASE",
                "com.adobe.eventType.generic.track",
                "com.adobe.eventSource.requestContent")
                .setEventData(eventData).build();

        // dispatch the analytics event
        MobileCore.dispatchEvent(newEvent, this);
    }

Note that all Adobe Events are processed by default. To optionally track events with custom names you can register a whitelist as follows:
```
List<AdobeBranch.EventTypeSource> apiWhitelist = new ArrayList<>();
apiWhitelist.add(new AdobeBranch.EventTypeSource("com.adobe.eventType.generic.track", "com.adobe.eventSource.requestContent"));
apiWhitelist.add(new AdobeBranch.EventTypeSource("io.branch.eventType.generic.track", "io.branch.eventSource.requestContent"));

AdobeBranch.registerAdobeBranchEvents(apiWhitelist);
```

Additional Whitelist Configuration Implementation Notes:

- Whitelist Configuration must happen after Adobe Initialization has completed.
- An empty whitelist will not listen for any events.
- A null whitelist (default) will listen for all Adobe events.
- A non-empty whitelist will listen for only those events that are in the list.

## License

AdobeBranchExtension is available under the MIT license. See the LICENSE file for more info.

## Developer Resources

- [Branch Dashboard](https://dashboard.branch.io/)
- [Adobe Mobile SDK V5](https://launch.gitbook.io/marketing-mobile-sdk-v5-by-adobe-documentation/release-notes)
- [Adobe Branch Mobile Extension UI Plugin](https://github.com/BranchMetrics/adobe-branch-mobile-plugin)
- [Adobe Mobile SDK V5 Docs](https://launch.gitbook.io/marketing-mobile-sdk-v5-by-adobe-documentation/build-your-own-extension)
