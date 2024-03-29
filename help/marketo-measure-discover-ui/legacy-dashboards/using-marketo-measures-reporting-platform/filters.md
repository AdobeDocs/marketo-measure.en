---
unique-page-id: 18874656
description: Filters - [!DNL Marketo Measure]
title: Filters
exl-id: 249266c8-9ff5-4895-979c-4f377423d031
feature: Reporting
---
# Filters {#filters}

Learn more about the different filters available to you in Discover and how you can use them.

>[!NOTE]
>
>The "matches a user attribute" and "matches (advanced)" Operators within your Discover filters are purely administrative and can be safely ignored.

**Account Id**

_Used in: Account Based Marketing_

Select or paste in a series of Account Ids from the CRM to filter the results. Account Ids provide more uniqueness than Account Name since names can be the same.

**Account Name**

_Used in: Account Based Marketing_

Select or paste in a series of Account Names from the CRM to filter the results. Strings can have duplicates, so it is possible to have multiple "[!DNL Marketo Measure]" accounts for example. If a single account is needed in this case, use the Account Id filter instead.

**Attribution Model**

_Used in: Overview, Marketing Spend, Ads ROI, Account Based Marketing, Web Traffic, CMO, Paid Media, Content Marketing, Passport_

Choose a single attribution model to apply to the board: First Touch, Lead Creation Touch, U-Shaped, W-Shaped, Full Path, or Custom Model. Full Path and Custom Model is not available across all tiers.

**Campaign**

_Used in: Overview, Growth, Ads ROI, Web Traffic, CMO, Paid Media, Content Marketing, Passport_

Filter the board by a single or multiple campaign names. Operators give the filter additional flexibility such as using the "contains" or "starts with" operators. If a Channel or Subchannel filter has been applied, the list of campaigns that appear will be a subset of the applied filters.

**Category 1-10**

_Used in: Overview, Growth, Ads ROI, CMO, Paid Media, Content Marketing, Velocity, Snapshot, Cohort Funnel, Passport_

Apply segment filters to the board, using the Categories and Segments that you've created in the [!DNL Marketo Measure] Settings. The list of Categories that you created will appear in the filters menu, so if no Categories have been set up, there will be no Category filters in the menu. Segment Categories are not available in all tiers, and the number of Categories available varies by tier as well.

**Channel**

_Used in: Overview, Growth, Marketing Spend, Ads ROI, Web Traffic, CMO, Paid Media, Content Marketing, Velocity, Passport_

Filter the board by a single or multiple channels. Operators give the filter additional flexibility such as using the "contains" or "starts with" operators. Once a channel is entered, the values shown in the Subchannel and Campaign filters will be from the applied subchannel filter.

**Cohort Stage**

_Used in: Cohort Funnel_

Select the stage that you want to view a cohort of. The stage that you select will appear at the top of the funnel, with all conversions flowing down from the top.

**Date**

_Used in: Overview, Growth, Marketing Spend, Ads ROI, Account Based Marketing, Web Traffic, CMO, Paid Media, Content Marketing, Velocity, Snapshot, Cohort Funnel, Passport_

Select a date range to filter the data in the boards, using flexible date operators such as "is in the range," "is in the year, " or "is before" for example. The exception is Snapshot, where you will select a single date to view a snapshot of the data.

**Date Type**

_Used in: Overview, Growth, Marketing Spend, Ads ROI, Account Based Marketing, Web Traffic, CMO, Paid Media, Content Marketing, Passport_

Choose the type of date you want to use, tied to the Date filter. The default date type varies by board. Touchpoint Date refers to the date that the marketing activity took place, Created Date is the date that the Lead or Contact or Opportunity was created in the CRM, and Close Date is the date that the Opportunity was closed.

**Dimension**

_Used in: Paid Media_

Dimension is similar to the Group By function, except that it is used on the Paid Media board in a slightly different way. Rather than stacking a chart, Dimension changes the lines from the Overview chart as well as the leading object in the tables.

![](assets/1.png)

By default, Dimension is set to Subchannel, and can be changed to:

* None: Displays everything in aggregate with no break down
* Channel: Lists the data by marketing channel
* Subchannel: Lists the data by marketing subchannel
* Campaign: Lists the data by campaign
* Account: Lists the data by account. Applies to [!DNL AdWords], [!DNL Bing], and [!DNL Facebook].
* Ad Group: Lists the data by ad group. Applies to [!DNL AdWords], [!DNL Bing], and [!DNL Facebook].
* Ad: Lists the data by ad. Applies to Doubleclick ads, so if Doubleclick is not used, no results will appear
* Advertiser: Lists the data by advertiser. Applies to the Doubleclick advertiser, so if Doubleclick is not used, no results will appear
* Creative: Lists the data by creative. Applies to [!DNL AdWords], [!DNL Bing], and [!DNL Facebook].
* Keyword: Lists the data by keyword. Applies to [!DNL AdWords], [!DNL Bing], and [!DNL Facebook].
* Placement: Lists the data by placement. Applies to Doubleclick placements, so if Doubleclick is not used, no results will appear
* Site: Lists the data by site. Applies to Doubleclick sites, so if Doubleclick is not used, no results will appear

**Group By**

_Used in: Overview, Growth, Marketing Spend, Account Based Marketing, Web Traffic, CMO_

Adjusts charts to change the dimension that is being stacked and grouped together. By default, Group By is set to Channel and can be changed to:

* None: Displays everything in aggregate with no break down
* Channel: Groups the data by marketing channel
* Subchannel: Groups the data by marketing subchannel
* Campaign: Groups the data by campaign
* Account: Groups the data by account. Applies to [!DNL AdWords], [!DNL Bing], and [!DNL Facebook].
* Ad Group: Groups the data by ad group. Applies to [!DNL AdWords], [!DNL Bing], and [!DNL Facebook].
* Ad: Groups the data by ad. Applies to Doubleclick ads, so if Doubleclick is not used, no results will appear
* Advertiser: Groups the data by advertiser. Applies to the Doubleclick advertiser, so if Doubleclick is not used, no results will appear
* Creative: Groups the data by creative. Applies to [!DNL AdWords], [!DNL Bing], and [!DNL Facebook].
* Keyword: Groups the data by keyword. Applies to [!DNL AdWords], [!DNL Bing], and [!DNL Facebook].
* Placement: Groups the data by placement. Applies to Doubleclick placements, so if Doubleclick is not used, no results will appear
* Site: Groups the data by site. Applies to Doubleclick sites, so if Doubleclick is not used, no results will appear

![](assets/2.png)

**Landing Page**

_Used in: Content Marketing_

Drill into the performance of a single landing page, or perhaps landing pages that contain a certain word such as "blog."

**Metric**

_Used in: Overview, Web Traffic, CMO, Paid Media, Content Marketing_

There are two different metric pickers that are used across different boards. The metric picker changes the measure on a chart, so that you can switch between viewing revenue or spend or impressions for example.

On the Overview and CMO boards, there is a shortened list of values related to ROI metrics:

* Revenue
* Spend
* Deals
* Pipeline Revenue
* Opportunities
* Contacts
* Leads

On the Web Traffic, Paid Media, and Content Marketing boards, there is a longer list of values related to both ROI and funnel metrics:

* Revenue
* Spend
* Deals
* Pipeline Revenue
* Opportunities
* Contacts
* Leads
* Clicks
* impressions
* Visits
* Unique Visits
* Page Views
* Forms

**Stage**

_Used in: Velocity_

By default, the Velocity board displays the times for all stages, but to drill in to a specific stage, use the Stage filter to select the stage.

**Subchannel**

_Used in: Overview, Growth, Marketing Spend, Ads ROI, Web Traffic, CMO, Paid Media, Content Marketing, Passport_

Filter the board by a single or multiple subchannels. Operators give the filter additional flexibility such as using the "contains" or "starts with" operators. If a Channel filter has been applied, the list of subchannels that appear will be a subset of the applied filters. Once a subchannel is entered, the values shown in the Campaign filters will be from the applied subchannel filter.

**URL**

_Used in: Web Traffic_

Drill into the traffic of a single URL, or perhaps URLs that contain a certain word such as "product."

**Won**

_Used in: Velocity_

By default, the Velocity board reports on only closed won opportunities, but adjust this filter to look at the velocity for either closed won or closed lost opportunities.
