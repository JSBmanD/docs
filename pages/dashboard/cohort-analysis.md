## Overview

Cohort analysis is a powerful tool that helps you to not only understand the full ROI of your campaigns, but help you guide future investment decisions and consumer targeting.

The Cohorts Analytics report allows you to analyze your cross-channel, cross-platform Branch data by either acquisition date (app install only) or re-engagement date (web and app sessions) to see how those users performed over time.

![image](/_assets/img/pages/dashboard/cohort-analysis/image_0.png)

As a tool used to separate growth metrics from engagement metrics, cohort analysis allows you to evaluate user behavior over time including key metrics such as retention and lifetime value (LTV).

This report is available within the following Channels (if said channel is part of your contract):

* Web to App

* Ads

* Email

## Data Requirements

In order for the Cohort Analytics report to provide insights, you must be measuring events using the Branch SDK and/or the Branch Web SDK (based on your product usage).

If you want to include cost data in the analysis, you must have the following partner integrations enabled: Facebook, Google, Apple Search Ads or Snap. Cost data is not currently supported for other partner integrations.

## Acquisition vs Re-engagement Cohorts

When creating your cohort for analysis, you can choose to base the cohort on either acquisition (install) activity or re-engagement activities.

An install cohort allows you to evaluate the long term behavior – i.e. interaction with your app as measured by in-app events – of your users based on their install cohort.

A re-engagement cohort allows you to evaluate the long term behavior – i.e. interaction with your web or app properties as measured by in-app events and/or web interactions – of your users based on their re-engagement cohort.

A re-engagement can be any event that creates a web or app session after a period of inactivity, such as web session starts or opens.

### Re-engagement Inactivity Period

Since re-engagements can only occur after a period of inactivity, any event used for performance analysis can only be part of one re-engagement cohort. A session-qualifying event only counts as a re-engagement if it occurs after a period of inactivity. However, a user can be in multiple re-engagement cohorts if they are re-engaged multiple times.

The default re-engagement inactivity window is 7 days.  You can modify this window under <notranslate>**Channels & Links**</notranslate> > <notranslate>**Link Settings**</notranslate> > <notranslate>**Attribution Windows**</notranslate>.

![image](/_assets/img/pages/dashboard/cohort-analysis/image_1.png)

## Building Your Cohort

To create a cohort, click on the <notranslate>**Create New Cohort**</notranslate> button and provide the following information:

* <notranslate>**Cohort Name**</notranslate>

* <notranslate>**Cohort Type**</notranslate>

    * Acquisition (install)

    * Re-engagement (any session across web and app)

* <notranslate>**Cohort Date Range**</notranslate>

    * When the install or re-engagement event occurred

* <notranslate>**Include Cost Data**</notranslate>

    * Only available within the Ads Channel

* <notranslate>**Measurement**</notranslate>

    * Show

    * Compare by

    * Where

    * Equals

![image](/_assets/img/pages/dashboard/cohort-analysis/image_2.png)

### Cohort Measurement Options

When creating a new cohort, the following measurement options are available to you.

#### Show

Show measures include important KPIs and metrics which you can use to hone in on user activity.

| Measure           | Description                                                                                                           |
|-------------------|-----------------------------------------------------------------------------------------------------------------------|
| <notranslate>**Add Payment Info**</notranslate> | Add Payment Info events                                                                                               |
| <notranslate>**Add to Cart**</notranslate>       | Add to Cart events                                                                                                    |
| <notranslate>**Add to Wishlist**</notranslate>   | Add to Wishlist events                                                                                                |
| <notranslate>**ARPPU**</notranslate>              | Average revenue per paying user; Ads Channel only                                                                            |
| <notranslate>**ARPU**</notranslate>              | Average revenue per user; Ads Channel only                                                                            |
| <notranslate>**Cost**</notranslate>              | Total cost; Ads Channel only                                                                                          |
| <notranslate>**eCPA**</notranslate>              | Effective cost per purchase; Ads Channel only                                                                         |
| <notranslate>**eCPI**</notranslate>              | Effective cost per install. The total cost of the campaign divided by the number of installs driven; Ads Channel only |
| <notranslate>**Gross Profit**</notranslate>      | Amount; Ads Channel only                                                                                              |
| <notranslate>**Initiate Purchase**</notranslate> | Initiate Purchase events                                                                                              |
| <notranslate>**Opens**</notranslate>             | Open events                                                                                                           |
| <notranslate>**Purchase**</notranslate>          | Purchase events
| <notranslate>**Retention**</notranslate>           | The ability of a product or service to retain its existing customers, with retention rates measuring the ratio of customers who are devoted and “stay” (those who keep using and supporting your app) to the total number of customers who installed your app.                                                                                                       |
| <notranslate>**Revenue**</notranslate>           | Revenue for commerce events                                                                                           |
| <notranslate>**ROAS**</notranslate>              | Return on Ad Spend. Revenue as a percentage of cost (will need this to compare for cohorts); Ads Channel only         |
| <notranslate>**ROI**</notranslate>               | Return on investment. Profit as a percentage of cost; Ads Channel only                                                |
| <notranslate>**Spend Credits**</notranslate>     | Spend Credits events                                                                                                  |
| <notranslate>**Users**</notranslate>             | The total number of unique users for each compare by in your cohort. Accessible in Table View only.                   |
| <notranslate>**View Cart**</notranslate>         | View Cart events                                                                                                      |

#### Compare by & (where/and/equals) Filters

Compare by and (where/and/equals) filters can be applied to any cohorting event - install or re-engagement - as well as any downstream event.

| Name                           | Description                                                                                                                                     |
|--------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| <notranslate>**ad name**</notranslate>                        | The name of the ad used in your campaign.                                                                                                       |
| <notranslate>**ad partner**</notranslate>                     | The name of the ad partner attributed to the install/re-engagement event.                                                                       |
| <notranslate>**ad set name**</notranslate>                    | The name of the ad set used in your ad.                                                                                                         |
| <notranslate>**attributed**</notranslate>                     | Whether or not the install/re-engagement event was attributed; values ‘true’ or ‘false’.                                                        |
| <notranslate>**campaign**</notranslate>                       | The name of the campaign associated with the install/re-engagement event.                                                                       |
| <notranslate>**channel**</notranslate>                        | The name of the channel associated with the install/re-engagement event                                                                         |
| <notranslate>**country**</notranslate>                        | The country code associated with the install/re-engagement event.                                                                               |
| <notranslate>**creative name**</notranslate>                  | The name of the creative used in your ad.                                                                                                       |
| <notranslate>**date**</notranslate>                           | The date of the event associated with the install/re-engagement event.                                                                          |
| <notranslate>**environment**</notranslate>                    | The overall environment - app OR web - associated with the install/re-engagement event.                                                         |
| <notranslate>**environment (conversion event)**</notranslate> | The overall environment - app OR web - associated with the downstream event.                                                                    |
| <notranslate>**feature**</notranslate>                        | The name of the Branch feature from which the install/re-engagement event. stems; paid advertising (Universal Ads), journeys or email provider. |
| <notranslate>**has app**</notranslate>                        | Whether or not the user already had the app was installed before the re-engagement event; values ‘true’ or ‘false’.                             |
| <notranslate>**has clicked ad**</notranslate>                 | Whether or not the user clicked on an ad using a Branch link; values ‘true’ or ‘false’.                                                         |
| <notranslate>**has clicked email**</notranslate>              | Whether or not the user clicked on an email using a Branch link; values ‘true’ or ‘false’.                                                      |
| <notranslate>**journey name**</notranslate>                   | The name you gave the Journey associated with the install/re-engagement event.                                                                  |
| <notranslate>**keyword**</notranslate>                        | They keyword used in your ad.                                                                                                                   |
| <notranslate>**last attributed touch type**</notranslate>     | Whether the last attributed touch was a click or an impression                                                                                  |
| <notranslate>**name**</notranslate>                           | The name of the app or web event associated with the install/re-engagement event.                                                               |
| <notranslate>**os**</notranslate>                             | The operating system of the device associated with the install/re-engagement event.                                                             |
| <notranslate>**os (conversion event**</notranslate>)          | The operating system of the device associated with the downstream event.                                                                        |
| <notranslate>**platform**</notranslate>                       | The platform - Android, iOS, Web, Desktop - associated with the install/re-engagement event.                                                    |
| <notranslate>**platform (conversion event)**</notranslate>    | The platform - Android, iOS, Web, Desktop - associated with the downstream event.                                                               |
| <notranslate>**referring domain**</notranslate>               | The name of the Branch referring domain associated with the install/re-engagement event.                                                        |
| <notranslate>**secondary publisher**</notranslate>            | The secondary publisher specified for the last attributed touch, passed by the ad network.                                                      |
| <notranslate>**stage**</notranslate>                          | The name of the stage associated with the install/re-engagement event                                                                           |
| <notranslate>**tags**</notranslate>                           | The tags associated with the install/re-engagement event                                                                                        |
| <notranslate>**view name**</notranslate>                      | The name of the Journey campaign associated with the install/re-engagement event.                                                               |
| <notranslate>**web format**</notranslate>                     | Whether the touch that referred the install or re-engagement event occurred on AMP web or regular web                                           |

## Using Visualizations Options

Once you’ve created a cohort, you can view the resulting analytics. All created cohorts include the following visualization functionality:

* <notranslate>**Unique Counts**</notranslate> - When <notranslate>"Unique"</notranslate> is checked, these are unique to a user. For example: if 1 user clicks 100 times, it will count as 1. There is no concept of "unique revenue"; "revenue" is always the sum of all purchase events.

* <notranslate>**Time Interval and Granularity**</notranslate>

* <notranslate>**Incremental vs Cumulative**</notranslate> - Incremental shows only data that occurred that day, giving visibility into how performance changes over time. Cumulative shows data that occurred that day plus all previous days, giving visibility into overall performance over time.

* <notranslate>**Apply Cost Data**</notranslate> - shows the cost per event for each compare by in your cohort.

* <notranslate>**Total vs Per User Counts**</notranslate> - Total shows the total number for that day. Per user shows the total number for that day over the total number of users for each compare by in your cohort.

* <notranslate>**Table vs Time Series View**</notranslate>

* <notranslate>**Download CSV**</notranslate>

* <notranslate>**Share Page State**</notranslate>

* Saved Views

    * Rename

    * Delete

* Reset Page State

![image](/_assets/img/pages/dashboard/cohort-analysis/cohort-report-functionality.gif)

## Appendix: What is Cohort Analysis?

Cohort analysis is the study of behaviors of groups over time. What behaviors and what groups you ask? "Behaviors" can be any actions you find relevant or that you are interested in. “Groups” are aggregations of data points or users that share a commonality and hence form a cohort.

So let’s apply this to a very basic real world example. You’re interested in knowing the average income over the first five years for college graduates during 2008 and 2009. If you were to look at a graph that charts this information you would view something akin to this:

![image](/_assets/img/pages/dashboard/cohort-analysis/image_4.png)

When you look at the income on an actual-basis, the average student income would be graphed for the year that it occurred—using the date time of the event in the analysis. The report above displays the data based on when the event happened. Using this type of linear analysis, it is difficult to compare one group to the other in order to determine any relationship between year of graduation and income because the timing is not static and the graduating classes are at different points in their careers for each year of comparison.

So let us take a look at this example using cohort analysis. As each graduating group of students is a cohort (they all graduated in the same year), we can evaluate the average income for each cohort using their graduation year as the initial event (t0) and graph their income relative to each year subsequent to their graduation (t0 +1, t0 +2, t0 +3, etc.).

![image](/_assets/img/pages/dashboard/cohort-analysis/image_5.png)

By using cohort analysis, you are able to evaluate unique cohorts with one another for an "apples to apples" comparison that is not possible when using linear analyses. Here, you can see that both graduating classes do increase their average income per year, but that by the third year out, the 2009 grads make more on average than their 2008 counterparts.
