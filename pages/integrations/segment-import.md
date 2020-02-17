---
title: Segment (import)
---
## Overview

Sending events from Segment to Branch will allow you to attribute downstream conversions like purchases across web and app to Branch link clicks. Events imported from Segment to Branch will be available wherever you can normally use events within Branch, including dashboard visualizations, Data Feeds, Universal Ads postbacks, Journeys targeting, Liveview and more.

This guide walks through the server-side integration for data import from Segment to Branch. For data export from Branch to Segment, go [here](/integrations/segment).

### What events does Branch import?

Branch will import events that are not auto-tracked with the Branch SDKs. This includes commerce, content, user lifecycle, and custom events, and excludes events like clicks and installs. See the full list of supported events and associated mappings [here](#supported-events). Branch will only import events that can be [tied to a user](#identifiers).

## Setup

1. [Contact Branch](https://support.branch.io){:target="\_blank"} to configure Branch to receive events from Segment. Please note that a subscription to [Data Feeds](https://branch.io/data-feeds/){:target="\_blank"} is required to enable data import from Segment to Branch.
1. Navigate to the [Data Integrations page](https://dashboard.branch.io/data-import-export/data-feeds/integrations){:target="\_blank"} of the Branch dashboard.
    1. Select <notranslate>**Segment**</notranslate> from the menu on the left.
    1. Select the platforms you would like to import events from and click <notranslate>**Save**</notranslate>.

    ![image](/_assets/img/pages/integrations/segment/segment-import.png)

1. Navigate to your your Segment UI’s Destinations page.
    1. Click on <notranslate>**Add Destination**</notranslate>.
    1. Search for Branch within the Destinations Catalog and confirm the Source you’d like to connect to.
    1. Enter your Branch Key. This can be found in the [Account Settings > App](https://dashboard.branch.io/account-settings/app){:target="\_blank"} section of the Branch dashboard.
    1. Enter your Branch Secret. This can be found in the [Account Settings > App](https://dashboard.branch.io/account-settings/app){:target="\_blank"} section of the Branch dashboard.

For server-side event import, **you can ignore the SDK integration instructions**.

!!! warning "Avoid duplicate data"
    To avoid duplicate data, you should either [track conversion events directly with Branch](/apps/v2event) or track events with Segment and then enable import to Branch, not both. Branch will warn you if you try to import events to Branch that you are already tracking.


### Track

The Branch integration supports some of the events tracked with Segment’s [Track](https://segment.com/docs/spec/track/){:target="\_blank"} method. The track API call is how you record any actions your users perform, along with any properties that describe the action.

Each action is known as an event. Each event has a name, like Registered, and properties, for example a Registered event might have properties like plan or accountType. Here’s the payload of a typical track call with most common fields removed:

```
{
  "type": "track",
  "event": "Registered",
  "properties": {
    "plan": "Pro Annual",
    "accountType" : "Facebook"
  }
}
```

And here’s the corresponding Javascript event that would generate the above payload:

```javascript
analytics.track("Registered", {
  plan: "Pro Annual",
  accountType: "Facebook"
});
```

See Segment's [Track documentation](https://segment.com/docs/spec/track/){:target="\_blank"} for more details and examples.

#### Supported events

Branch will only import events from Segment that are not already auto-tracked with the Branch  SDK. This means that events like click and install cannot be imported. The following outlines how Segment events are mapped to Branch events, and which will be imported to Branch:

| Segment Event | Branch Event | Branch Event Category | Imported |
| --- | --- | --- | --- |
| <notranslate>Product Added</notranslate> | <notranslate>Add To Cart</notranslate> | Commerce Event | **Yes** |
| <notranslate>Product Added to Wishlist</notranslate> | <notranslate>Add To Wishlist</notranslate> | Commerce Event | **Yes** |
| <notranslate>Cart Viewed</notranslate> | <notranslate>View Cart</notranslate> | Commerce Event | **Yes** |
| <notranslate>Payment Info Entered</notranslate> | <notranslate>Add</notranslate> Payment Info</notranslate> | Commerce Event | **Yes** |
| <notranslate>Checkout Started</notranslate> | <notranslate>Initiate Purchase</notranslate> | Commerce Event | **Yes** |
| <notranslate>Order Completed</notranslate> | <notranslate>Purchase</notranslate> | Commerce Event | **Yes** |
| *use the Branch event name* | <notranslate>Spend Credits</notranslate> | Commerce Event | **Yes** |
| <notranslate>Products Searched</notranslate> | <notranslate>Search</notranslate> | Content Event | **Yes** |
| <notranslate>Product Viewed</notranslate> | <notranslate>View Item</notranslate> | Content Event | **Yes** |
| <notranslate>Product List Viewed</notranslate> | <notranslate>View Items</notranslate> | Content Event | **Yes** |
| <notranslate>Product Reviewed</notranslate> | <notranslate>Rate</notranslate> | Content Event | **Yes** |
| <notranslate>Product Shared</notranslate> | <notranslate>Share</notranslate> | Content Event | **Yes** |
| *use the Branch event name* | <notranslate>Complete Registration</notranslate> | Lifecycle Event | **Yes** |
| *use the Branch event name* | <notranslate>Complete Tutorial</notranslate> | Lifecycle Event | **Yes** |
| *use the Branch event name* | <notranslate>Achieve Level</notranslate> | Lifecycle Event | **Yes** |
| *use the Branch event name* | <notranslate>Unlock Achievement</notranslate> | Lifecycle Event | **Yes** |
| *any event name* | <notranslate>Custom</notranslate> | Custom Event | **Yes** |
| <notranslate>Deep Link Clicked</notranslate> | <notranslate>Click</notranslate> | - | No |
| <notranslate>Install Attributed</notranslate> | <notranslate>Install</notranslate> | - | No |
| <notranslate>Deep Link Opened</notranslate> | <notranslate>Reinstall</notranslate> | - | No |
| <notranslate>Deep Link Opened</notranslate> | <notranslate>Open</notranslate> | - | No |
| - | <notranslate>SMS Sent</notranslate> | - | No |
| - | <notranslate>Pageview</notranslate> | - | No |
| - | <notranslate>Web Session Start</notranslate> | - | No |
| - | <notranslate>Branch CTA View</notranslate> | - | No |
| - | <notranslate>Impression</notranslate> | - | No |
| - | <notranslate>Web to App Auto Redirect</notranslate> | - | No |
| <notranslate>Application Installed</notranslate> | - | - | No |
| <notranslate>Application Opened</notranslate> | - | - | No |
| <notranslate>Application Updated</notranslate> | - | - | No |
| <notranslate>Application Backgrounded</notranslate> | - | - | No |
| <notranslate>Application Crashed</notranslate> | - | - | No |
| <notranslate>Application Uninstalled</notranslate> | - | - | No |
| <notranslate>Push Notification Received</notranslate> | - | - | No |
| <notranslate>Push Notification Tapped</notranslate> | - | - | No |
| <notranslate>Push Notification Bounced</notranslate> | - | - | No |


#### Identifiers for app events

Identifiers are required for events to be imported to Branch. You must include:

* context.device.advertisingId AND context.device.type OR
* context.device.id AND context.device.type OR

Branch maps Segment's identifiers to the following:

| Segment field | Branch field |
| --- | --- |
| `userId` | `developer_identity` |
| `context.device.advertisingId` | `idfa` or `aaid` |
| `context.device.id` | `idfv` or `android_id` |
| `context.device.type` | `os` |

If using User ID with Segment, Branch will automatically map this to [developer identity](/apps/ios/#track-users). Check out Segment's [User ID docs](https://segment.com/docs/spec/identify#user-id){:target="\_blank"} for more details.

At this time, Branch does not map Segment's anonymous ID to any field, and [will not attribute logged out web events](#attribution-for-logged-out-users-on-web) received from the server-to-server integration. Anonymous ID [can still be attached to events](#attaching-anonymous-id-to-events).

#### Identifiers for web events

In order to attribute accurately on web it is important to collect the Branch SDK's browser fingerprint and pass it to the Segment track function. Branch uses this along with the `userAgent` collected by the Segment SDK to identify the user's persona, platform, os and other parameters. Collecting the browser fingerprint can be done with the following code snippet:

```javascript
const loadBranchAndGetFingerprint = new Promise(function(resolve, reject) {
  branch.init('BRANCH_KEY', {}, function(err, data) {
  branch.getBrowserFingerprintId(function(err, fingerprint) {  // fetch the browser fingerprint from the SDK
    if (!!err) {
      reject(err);
      return;
    }
    resolve({...data, fingerprint});
  });
  });
});
```

You can then pass it into the payload of the Segment track event:

```javascript
loadBranchAndGetFingerprint.then(function(data) {
    const { fingerprint } = data;
    // Load the Segment SDK and initialize with key here

    // Segment track request
    analytics.track('Order Completed', {
        browser_fingerprint_id: fingerprint // add the browser fingerprint to the Segment track event
        //... Other event details ...
    })
});
```

#### Validating the integration

Once you have import turned on in both Segment and Branch, events should come through. You will see a green dot on the import card if Branch has seen events:

![image](/_assets/img/pages/integrations/segment/segment-import-status.png)

To see more information on the events that are coming in, you can look at events with <notranslate>**origin**</notranslate> `SEGMENT` in [Liveview](https://dashboard.branch.io/liveview/events){:target="\_blank"}:

![image](/_assets/img/pages/integrations/segment/segment-import-liveview.png)

Branch imports events from Segment as [commerce, user lifecycle, content, or custom events](#supported-events).

#### Using imported events

Events imported from Segment to Branch will be available wherever you can normally use events within Branch. This includes dashboard visualizations, Data Feeds (including Data Integrations, Query API, Webhooks, and Daily Export API), Universal Ads postbacks, Journeys targeting, Liveview and more.

## Advanced

### Attaching anonymous ID to events

Events imported from Segment with anonymous ID attached will retain that value on the event, and will be available in the custom_data field if exported back out from Branch. To attach anonymous ID to events auto-tracked by Branch (installs, opens, etc.), follow the instructions [here](/integrations/segment/#pass-segment-anonymous-id).

### Attribution for logged out users on web

Branch uses a custom, in-house identifier for logged out users on web. If you enable the server to server integration from Segment to Branch, you will not be able to attribute logged out web events to a campaign run with Branch out-of-the-box. To close this gap, you can either: (1) track web events with the Branch web SDK, while only ingesting app events from Segment; OR (2) [add client-side javascript to attach Branch browser fingerprints to all web events tracked via Segment](#### Identifiers for web events)
