---
unique-page-id: 18874610
description: Dynamics Campaigns and Marketing Lists - [!DNL Marketo Measure]
title: Dynamics Campaigns and Marketing Lists
exl-id: 7b3d4032-5edf-489d-b86b-1e2a5755b258
feature: Microsoft Dynamics
---
# Dynamics Campaigns and Marketing Lists {#dynamics-campaigns-and-marketing-lists}

>[!NOTE]
>
>This article covers an outdated process. We encourage users to use the [new, improved in-app process](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md){target="_blank"}.

## Campaigns {#campaigns}

Dynamics Campaigns are good for tracking offline marketing activity and including them in the omni-channel journey. Campaigns have to relate to Leads or Contacts and can either roll up to the Campaign through either Campaign Responses or Marketing Lists.

## Campaign Responses {#campaign-responses}

When Leads or Contacts get added to a Campaign directly, they're entered as a Campaign Response record.

![](assets/1.png)

## Enable Touchpoints {#enable-touchpoints}

To include these records in the touchpoint journey, there are a few options for the types of Campaign Responses to sync. On the Campaign record, there should be a custom field from the installed solution labeled, "[!UICONTROL Enable Buyer Touchpoints]." If you do not see this, the field will need to be added via Form Editor.

![](assets/2.png)

You can select to include all records that have a Campaign Response in the Campaign, or only those with a Response of "Interested," or by default, you can not include the Campaign Responses at all. You can either leave the field blank or explicitly choose to exclude it.

[!DNL Marketo Measure] does not support custom Response values.

![](assets/3.png)

These are the stock response values for the Campaign Response:

![](assets/4.png)

Based off your selection, these records are now eligible for touchpoints in the Lead, Contact, or Opportunity journey. If they qualify, a "Dynamics Campaign" touchpoint will appear in the journey.

One reason that a Campaign Response might not show up is because a First Touch and/or Lead Creation Touch activity had already been recorded for the Lead/Contact and the "PostLC" feature is disabled or has hit its maximum number of touchpoints.

## Touchpoint Date {#touchpoint-date}

The Touchpoint Date for a Campaign is usually on the date that the Campaign Response was added to the Campaign. It can be overridden if the custom field from the installed solution labeled, "Buyer Touchpoint Date," is populated. If you do not see this, the field will need to be added via Form Editor.

One common example using this field is for events where a list of badge scans from an event is added to the CRM days after the event occurred, so the user can actually change the Buyer Touchpoint Date back to when the event occurred.

![](assets/5.png)

## Marketing Lists {#marketing-lists}

Marketing Lists are another way to include Leads or Contacts into a marketing journey. Marketing Lists are unique for a group of Leads or Contacts, meaning that the user has to select whether their list is a set of Leads or a set of Contacts.

[!DNL Marketo Measure] only supports Static Marketing Lists. We do not support Dynamic Marketing Lists because our processing requires that we check on a record's Modified Date but because a Dynamic List is frequently changing, there is no Modified Date for [!DNL Marketo Measure] to check against. This would require a constant download of the full data set throughout the day.

![](assets/6.png)

The screenshot above is a Marketing List for Leads. Marketing Lists are associated to Campaigns and can be associated to multiple Campaigns. Unless you only ever create one Marketing List for one Campaign, [!DNL Marketo Measure] does not recommend that customers use Marketing Lists to track their Campaigns. It is unlikely that the same exact list of Leads/Contacts would be eligible for touchpoints across multiple Campaigns.

## Enable Touchpoints {#enable-touchpoints-1}

To enable a Marketing List for touchpoints, there is a separate setting on the Campaign record labeled, "[!UICONTROL Sync Marketing Lists]," which is a simple yes/no switch. If you do not see this, the field will need to be added via Form Editor. While on the Campaign record, you can see which Marketing Lists are related to the Campaign so you know how many Lists you are enabling.

![](assets/7.png)

## Touchpoint Date {#touchpoint-date-1}

The Touchpoint Date for a Marketing List is typically the ListMember created date, so the date that the Lead or Contact was added to the Marketing List. It can be overridden if the custom field from the installed solution labeled, "Buyer Touchpoint Date," is populated. If you do not see this, the field will need to be added via Form Editor.

![](assets/8.png)

## Channel Mapping {#channel-mapping}

Dynamics Campaigns are bucketed in your custom Marketing Channels using the Campaign Type field. These can be changed in your Dynamics Customizations menu.

The values in the Campaign Type menu are pulled into the [!DNL Marketo Measure] Application. **[!UICONTROL My Account]** > **[!UICONTROL Settings]** > **[!UICONTROL Offline Channels]**.

For each Campaign Type, it can be mapped to a Channel and Subchannel combination so that each touchpoint that derives from the Campaign will have the correct mapped Channel and Subchannel.

![](assets/9.png)

![](assets/10.png)

## Campaign Sync Date {#campaign-sync-date}

This is not available for Dynamics customers

## FAQ {#faq}

**Can we enable touchpoints on Marketing Lists or only campaigns in Dynamics?**

You can enable a Marketing List but it needs to be related to a Campaign because the option to sync a Marketing List lives on the Campaign.

**Can we use Campaign Responses AND Marketing Lists on a Campaign?**

Yes.
