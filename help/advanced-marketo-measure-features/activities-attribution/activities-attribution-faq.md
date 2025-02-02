---
unique-page-id: 18874704
description: Activities Attribution FAQ - [!DNL Marketo Measure]
title: Activities Attribution FAQ
exl-id: 6272024f-b6ae-4aa7-ba92-c9f183549614
feature: Attribution
---
# Activities Attribution FAQ {#activities-attribution-faq}

[!DNL Marketo Measure] Activities imports all your Activity records and generates touchpoints for them, allowing these Activities to be receive attribution credit. The most common use case is to track Activities from the Sales team, as they commonly create a record of phone calls or emails that are sent to prospects. Other unique things that can be tracked are content interactions like asset downloads or video views.

>[!AVAILABILITY]
>
>This feature is enabled for Tier 2 customers only. To request a higher account tier, contact the Adobe Account Team (your account manager).

**How is this different from Offline Campaigns?**

The biggest difference is that Campaigns can only provide one touchpoint because Campaigns only allow one Campaign Member for each Lead or Contact. That means you can't track recurring events like outbound calls or demos or webinar attendees, unless you create individual Campaigns for each grouping. Activities allow you to measure every event.

**Is there a difference between Task, Events, and Activities?**

The Activities object acts as the umbrella, or parent, over the Task and Event objects. Activities essentially cover both Tasks and Events. Tasks are typically used to record quick one-off items such as a phone call or an email. Events are typically used for things that might have a start or end date, like meetings or conferences.

**If I have a Lead or Contact with the same recurring Task, will I see Buyer Touchpoints for all of those?**

Yes. There is a 1:1 relationship between your synced Activities and Touchpoints created.

**How do I know which records result in Touchpoints being created?**

A good suggestion is to set up your filters using the Activity object in your CRM first. Based off the filter rules, this gives you a good idea as to how many records fall under that criteria, then you can refine it as needed. This is not required, but a helpful way for users to understand how many Activities Touchpoints will be created once the Activities rules have been set up.

**What is the [!DNL Marketo Measure] Campaign Name?**

Since these Activities result in a Touchpoint, [!DNL Marketo Measure] must know which Channel and Subchannel they belong to. For each rule, you are required to provide a [!DNL Marketo Measure] Campaign Name. After that is created, use the Online Channels CSV to map that [!DNL Marketo Measure] Campaign Name to its appropriate Channel. The [!DNL Marketo Measure] Campaign Name also appears on the Touchpoint itself within the [!UICONTROL Ad Campaign Name] field.

**What other Touchpoint fields are populated?**

| **Touchpoint Field** | **Value** |
|---|---|
| Lead/Contact | All activities are related to a Lead or Contact |
| Campaign | Channel.Subchannel [[!DNL Marketo Measure]] |
| Touchpoint Source | CRM Activity |
| Medium | Activity.Type |
| Touchpoint Type | Activity.Type |
| Ad Campaign Name | [!DNL Marketo Measure] Campaign Name |
| Ad Content | Activity Subject |
| Ad Id | Activity External Id |
| Touchpoint Date | [custom - set in apps] |

**What if I need to create a different rule for each Sales Rep? Do I need to create different [!DNL Marketo Measure] Campaign for each?**

No you do not. "Dynamic Campaign Names" allows you to fill in part (or all) of the [!DNL Marketo Measure] Campaign Name using a "replacement parameter" that references a field from the Activity object. For example, if you have a [!DNL Marketo Measure] Campaign Name titled "Outbound Call" but you want the Sales Rep to be at the end, take the CRM field name and call the [!DNL Marketo Measure] Campaign Name "Outbound Call {AssignedTo}" or "Outbound Call {CreatedBy}."

**How do I set up Activities in the [!DNL Marketo Measure] app?**

Directions on how to configure Activities within the [!UICONTROL Marketo] Measure app can be found in the [!DNL Marketo Measure] Activities support article.

**What do the different operators mean?**

* is equal to: exact match to the value (aka: social)
* contains: the text is in the middle (aka: &#42;social&#42;)
* starts with: the value starts with the text (aka: social&#42;)
* ends with: the value ends with the text (aka: &#42;social)
* matches any: multiple values can be added that are comma-separated. If [!UICONTROL starts with], [!UICONTROL ends with], or contains operators must be applied, use the wildcard (&#42;)
* greater than: used for numerical fields or date/time fields
* less than: used for numerical fields or date/time fields

**What Channel do these Activities go under?**

When the Activity rule and its corresponding [!DNL Marketo Measure] Campaign Name are created, use the Online Channels definitions to place those Campaigns under the correct Marketing Channel. [!DNL Marketo Measure] can define Channels using not only medium and source, but also campaign.

In the example above, to assign the "Outbound Call {Assigned To}" campaign to the BDR channel, insert a row in your Online Channels CSV for the BDR channel with a campaign definition of "Outbound Call&#42;" - the asterisk denotes a wildcard value, so all campaigns that start with "Outbound Call" will fall under the BDR channel, rather than having to create a separate row for each campaign name.
