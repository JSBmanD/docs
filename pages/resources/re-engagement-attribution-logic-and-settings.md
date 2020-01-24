---
title: Re-engagement Attribution Logic & Settings
---
## Overview

We think about event attribution and re-engagement as different but linked concepts. When we connect an install or event to a click or impression, we refer to this as attribution. Accordingly, we have various attribution windows that define the allowable length of time between a click or impression to install or event. If an install or event occurs outside of the set attribution window, then attribution is not performed. When we attribute an event, we update the corresponding ad click or impression as having been used for attribution.

For more information, please read [Branch Attribution Logic and Settings](https://docs.branch.io/resources/branch-attribution-logic-and-settings/).

## Re-engagement Determination

Similar to the function of the attribution windows referenced above, the re-engagement window defines the allowable length of time between two events (non-install events) that a user must be inactive in order to define the later event as a re-engagement. This determination can be used in re-engagement cohort analysis and postbacks, but not in dashboard activity analytics.

Denoting an event is re-engagement occurs in addition to the attribution of the event itself; i.e. the event is first attributed using the attribution windows above and then marked as re-engagement when applicable using the re-engagement inactivity window.

![image](/images/pages/resources/matching/reengagement-inactivity.png)

## Re-Engagement Inactivity Window Settings

By default, Branch sets the re-engagement inactivity window to 7 days. This means any attributed non-install event occurring 7 days (or more) after the most recent activity will be marked as re-engagement. Once a user completes an event that is attributed as re-engagement, all subsequent events will continue to be attributed as re-engagement until another 7 days of inactivity have passed.

To modify your app-level re-engagement inactivity window:

1. In the left-hand nav, click on <notranslate>**Link Settings**</notranslate>.
2. On the <notranslate>**Link Settings**</notranslate> page, click on the <notranslate>**Attribution Windows**</notranslate> tab.
3. Scroll down to the <notranslate>**Re-engagement Inactivity**</notranslate> setting and edit the value to any value between 0.001 and 90 days.

![image](/images/pages/resources/matching/re-engagement-attribution.png)

## Partner Settings for Acquisition Only Campaigns

While the app-level re-engagement inactivity window is a global setting that applies to any partner you work with to market your app and can be used in re-engagement cohort analysis and postbacks, there is also a related partner-level setting.

When this setting is enabled, we will only attribute events for this partner based on the touch (click or impression) that drove the install. This is useful for ad partners that are only used for acquisition campaigns and essentially disables "re-engagement" attribution.  Other attribution windows (for example, click to conversion) still apply to the install touch.

Unlike the app-level setting, this impacts all analytics and postbacks, and can be configured on a per partner basis.

!!! warning "Enabling Install Touch Setting"
	Currently this setting is not available in your Branch dashboard.  If you are interested in having this setting available in your account, please contact [Support](mailto:support@branch.io).

1. In the left-hand nav, click on <notranslate>**Ads**</notranslate> and then on <notranslate>**Partner Management**</notranslate>.
2. Search for and select the partner you wish to enable install touch for.
3. On the partner's <notranslate>**Attribution Windows**</notranslate> tab, toggle <notranslate>**Use ad partner attribution settings**</notranslate> on.
4. At the bottom of the attribution window settings table, tick the box next to <notranslate>**Only attribute based on touch**</notranslate>.
5. Click <notranslate>**Save**</notranslate>.

![image](/images/pages/resources/matching/install-touch-setting.png)

## Viewing Re-Engagement in Reporting

While re-engagement activity is not viewable in the Ads Activity report, you can use the Cohort report to easily evaluate the long term behavior – i.e. interaction with your web or app properties as measured by in-app events and/or web interactions – of your users based on their re-engagement cohort.

To view a re-engagement cohort:

1. In the left-hand nav, click on <notranslate>**Ads**</notranslate>, click on <notranslate>**Analytics**</notranslate> and then click the <notranslate>**Cohorts**</notranslate> tab.
2. Click <notranslate>**Create New Cohort**</notranslate> and select <notranslate>**Re-engagement**</notranslate> as the <notranslate>**Cohort Type**</notranslate>.
3. Finish your report selections and click <notranslate>**Save**</notranslate>.

![image](/images/pages/resources/matching/reengagement-cohort.png)

## Tips for TUNE-Migrated Clients

If you transitioned from TUNE to Branch, there are a few things to keep in mind regarding re-engagement attribution functionality in Branch.

*   The default Re-engagement inactivity window in Branch is set to a default of 7 days, whereas the re-engagement inactivity window did not exist in TUNE and was effectively set to 0. This means, you will notice less events marked as re-engagement due to the longer period of time required to pass between events.  You can modify this setting by changing the Re-engagement inactivity window in your Branch account as mentioned above.
*   The TUNE `is_reengagement` parameter is mapped to Branch’s `reengagement_activity.attributed` parameter and is available via:
    *   **Re-engagement Cohorts report as described above**
    *   **Postbacks** using the Branch macro <#if (reengagement_activity.attributed)?? && reengagement_activity.attributed>1<#else>0</#if>
    *   **Exports** using the Branch field `reengagement_activity.attributed`
*   TUNE Install Partner reporting and postbacks are reproducible in Branch via:
    *   **Acquisition Cohorts report** shows downstream events tied to the install cohort you are viewing and is filterable by ad partner.
    *   **Postbacks **using the Branch macro  ${(install_activity.touch_data.tilde_advertising_partner_name)!} which identifies the install partner for all downstream events
    *   **Exports** using the Branch field `install_activity.touch_data`
    *   **All analytics, postbacks, and exports** for an ad partner if you enable install touch attribution for that partner
