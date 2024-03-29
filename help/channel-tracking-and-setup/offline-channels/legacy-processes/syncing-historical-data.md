---
unique-page-id: 42762310
description: Syncing Historical Data - [!DNL Marketo Measure]
title: Syncing Historical Data
exl-id: 5a3c1a71-463a-4d75-98b9-fc225839512a
feature: Channels
---
# Syncing Historical Data {#syncing-historical-data}

[!DNL Marketo Measure] is a solution that provides the most granular, actionable data. We understand, however, that you might have existing data you'd like to have attribution for. It's possible to generate Touchpoints for historical data, but it's important to take a few factors into consideration before moving forward with this process.

>[!NOTE]
>
>This article covers an outdated process. We encourage users to use the [new, improved in-app process](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md){target="_blank"}.

## Factors to Consider {#factors-to-consider}

**Is the data already organized into campaigns?**

a. The data needs to be organized into Campaigns to be synced to [!DNL Marketo Measure] in order to have Touchpoints generated. If it's not currently organized into Campaigns, you will want to evaluate if it's worth the time and resources needed to segment the data into the appropriate campaigns.

b. The date the member was added to the campaign or marked as responded will be used for the Touchpoint date, so this needs to be accurate as well. [!DNL Marketo Measure] offers workarounds in both SFDC and MSD to update the dates, but this could be time-consuming depending on the volume.

**Do you have a fairly equal amount of data organized into campaigns for all Channels (paid search, events, organic, etc)?**

It's important to have a balanced picture of attribution in order to have accurate and "fair" reporting. For example, if you only have data for historic offline channel efforts like Events, the data will be inherently biased without historic online data to complement it.

**What level of granularity are you expecting?**

You will essentially know the Channel, Subchannel, and Campaign name only.

**What are your reporting goals in the future?**

This data is going to be limited, so it's important to consider how you plan on using it. It might not make the most sense to compare historical data to future data.

**How far back are you wanting to go?**

[!DNL Marketo Measure] strongly recommends not going past the previous year.

This is a topic we strongly encourage discussing with your [!DNL Marketo Measure] contact first. If you've considered the above and would like to proceed, general instructions (separate for [!DNL Salesforce] and [!DNL Microsoft Dynamics]) are below.

## Syncing Historic Campaigns in [!DNL Salesforce] {#syncing-historic-campaigns-in-salesforce}

**Online:**

To sync historical online data, the data must be organized into Salesforce Campaigns that you would then sync to [!DNL Marketo Measure] via [!DNL Salesforce] Campaign Sync rules in the [!DNL Marketo Measure] app. It's important to make sure touchpoints are not generated from any of these campaigns after the date your JavaScript went live. The reason for this is to avoid duplicate touchpoint. After the JavaScript is live, online efforts are being automatically tracked, so we don't want to also track them via an SFDC campaign. To avoid this problem, be sure to add a sense of time to the rule. Maybe something like "Campaign Member Created Date is less than [JavaScript go-live date]".

![](assets/syncing-historical-data-1.png)

The channel mapping component for historical online data can be a bit tricky. We want it to match your current online channel rules (from the online rule sheet) as closely as possible for clean reporting. Below is an example of ideal channel mapping.

>[!NOTE]
>
>This channel mapping is done in the [!UICONTROL Offline Channels] section of the [!DNL Marketo Measure] app since we are using SFDC campaigns.

| Salesforce Campaign Type | Channel | Subchannel |
|---|---|---|
| Paid Search - AdWords | Paid Search | AdWords |
| Paid Search - Bing | Paid Search | Bing |
| Paid Search - Yahoo | Paid Search | Yahoo |

Online data added in this way will inherently be less granular than online data [!DNL Marketo Measure] tracks via JavaScript. For example, fields such as Form URL, Landing Page, Referrer Page, etc will not be populated. Therefore, it is recommended to break out the campaigns into each source if possible. As seen in the example above, you'd need to have multiple Campaign Types for each source in order to have granularity in reporting.

It might not be possible or reasonable to have the number of SFDC Campaign Types to support granular channel mapping, so you may resort to just mapping to the Channel level and ignoring subchannels. If the Channel level is not known either, you could set up a proxy channel like "Historic Digital" so that you at least know it was an online touch.

If you need to mass edit the touchpoint date that will be pushed for these historical online efforts, use the [!DNL Marketo Measure] custom "[!UICONTROL Bulk Update Touchpoint Date]" button (this is available as a custom field on the Campaign Object in SFDC). If the Campaign has a short time span, perhaps it would be worthwhile to mass edit the Touchpoint date on a day by day interval, while it might make sense to mass update on a weekly basis if the Campaign has a longer time span. If you do use the Bulk Update Touchpoint Date functionality, make sure to update the Campaign Sync Rule to use the Buyer Touchpoint Date on the date field. Note that this could require getting creative with your Campaign Sync rules if this will only apply to a Campaign or two and not all.

**Offline:**

Historical data of offline marketing efforts (those that cannot be tracked via JavaScript) will also need to be organized into SFDC campaigns. SFDC campaigns are the way [!DNL Marketo Measure] tracks offline efforts regardless of if the activity is "historical" or "current/post-[!DNL Marketo Measure] implementation" so follow the same channel mapping decided on in the original Offline Channel Configuration training.

If necessary, use the "Bulk Update Touchpoint Date" button to mass edit the touchpoint date for campaign members. For example, if you are creating SFDC campaigns after the event occurred--you'd want to mass edit for the correct date. If you do use the Bulk Update Touchpoint Date functionality, make sure to update the Campaign Sync Rule to use the Buyer Touchpoint Date on the date field. Note that this could require getting creative with your Campaign Sync rules if this will only apply to a Campaign or two and not all.

## Syncing Historic Campaigns in [!DNL Dynamics] {#syncing-historic-campaigns-in-dynamics}

[!DNL Marketo Measure] is able to retroactively generate touchpoints for interactions that occurred in the past, as long as they're organized into Campaigns within [!DNL Dynamics].

This usually involves work in the CRM to account for historical dates. The handling will also be different for online efforts (tracked by JS) and offline efforts (not able to be tracked by JS).

Follow the instructions below for organizing historical data in [!DNL Dynamics] in a format that can be synced to [!DNL Marketo Measure].

**Online:**

Historic digital data needs to be organized into [!DNL Dynamics] campaigns in order to be backfilled. Ideally, this structure is already in place.

If the data is housed elsewhere (such as still living in Marketing Automation) it will need to be pushed into [!DNL Dynamics] and organized into the appropriate campaigns. Then you will need to account for the Touchpoint Date as you want it to reflect the date from the past, not the date you pushed it into [!DNL Dynamics]. To override this date, you can use the custom "Buyer Touchpoint Date" field to change the date. You will need to add this to the Marketing List Form.

![](assets/syncing-historical-data-2.png)

As a result, you can mass set the date for everyone in that Marketing List that will be used for the Touchpoint Date. To have more accurate historical dates, create multiple Marketing Lists for the same campaign--each with its own Touchpoint Date. If the Campaign has a short time span, perhaps it would be worthwhile to create a Marketing List for each day. If the Campaign has a longer time span, it might make sense to create a Marketing List on a weekly basis.

More information on Syncing Marketing Lists can be found here: [[!DNL Dynamics] Campaigns and Marketing Lists](/help/channel-tracking-and-setup/offline-channels/legacy-processes/dynamics-campaigns-and-marketing-lists.md)

>[!NOTE]
>
>If for any reason you have a campaign tracking online activity that is active past the JavaScript live date, be sure to set the "[!UICONTROL Touchpoint End Date]" field to the date the JS went live. This is to avoid having duplicate touchpoints for the same interaction.

Considerations: Online data added in this way will inherently be less granular than online data [!DNL Marketo Measure] tracks via JavaScript. For example, fields such as: Form URL, Landing Page, Referrer Page, etc., will not be populated. Therefore, it is recommended to break out the campaigns into each source if possible. Below is an example of ideal mapping.

| Dynamics Campaign Type | Channel | Subchannel |
|---|---|---|
| Paid Search - AdWords | Paid Search | AdWords |
| Paid Search - Bing | Paid Search | Bing |
| Paid Search - Yahoo | Paid Search | Yahoo |

If you don't have a way of identifying a source or it is not worth the time and effort, you can use one Campaign Type mapped to a channel called something like "Legacy Digital" or "Historic Website.

**Offline:**

To have touchpoints for offline marketing efforts from the past, the data must be organized into [!DNL Dynamics] campaigns and synced to [!DNL Marketo Measure]. The process is the same as for current offline channels (sync the campaign via Marketing Lists or Campaign Responses). Below is an example of channel mapping.

| Dynamics Campaign Type | Channel | Subchannel |
|---|---|---|
| Events - Sponsored Conferences | Events | Sponsored Conferences |
| Events - Partner Events | Events | Partner Events |
| Events - Hosted Events | Events | Hosted Events |
| Webinar - Partner Webinar | Webinar | Partner Webinar |

If this data is not already organized into Campaigns with the correct dates set, you can use the "Buyer Touchpoint Date" field to reflect the accurate date from the offline activity in the past.

