---
unique-page-id: 18874704
description: Activities Attribution FAQ - Marketo Measure - Product Documentation
title: Activities Attribution FAQ
exl-id: 6272024f-b6ae-4aa7-ba92-c9f183549614
---
# Activities Attribution FAQ {#activities-attribution-faq}

Marketo Measure's Activities functionality allows us to import all your Activity records and generate touchpoints for them, allowing these Activities to be receive attribution credit. The most common use case is to track Activities from the Sales team, as they will commonly create a record of phone calls or emails that are sent to prospects. Other unique things that can be tracked are content interactions like asset downloads or video views.

**How is this different from Offline Campaigns?**

The biggest difference is that Campaigns can only provide one touchpoint because Campaigns only allow one Campaign Member for each Lead or Contact. That means you can't track recurring events like outbound calls or demos or webinar attendees, unless you create individual Campaigns for each grouping. Activities will allow you to measure each and every event.

**Is there a difference between Task, Events, and Activities?**

The Activities object acts as the umbrella, or parent, over the Task and Event objects. Activities essentially cover both Tasks and Events. Tasks are typically used to record quick one-off items such as a phone call or an email. Events are typically used for things that might have a start or end date, like meetings or conferences.

**If I have a Lead or Contact with the same recurring Task like an email or call, will I see Buyer Touchpoints for all of those?**

Yes. There will be a 1:1 relationship between your synced Activities and Touchpoints created.

**How do I know which records will result in Touchpoints being created?**

A good suggestion is to set up your filters using the Activity object in your CRM first. Based off the filter rules, that will give you a good idea as to how many records fall under that criteria, then you can refine it as needed. This isn???t required, but a helpful way for users to understand how many Activities Touchpoints will be created once the Activities rules have been set up.

**What is the Marketo Measure Campaign Name?**

Since these Activities will result in a Touchpoint, Marketo Measure needs to know which Channel and Subchannel they belong to. For each rule, you???ll be required to provide a Marketo Measure Campaign Name. Once that???s created, you can use the Online Channels CSV to map that Marketo Measure Campaign Name to its appropriate Channel. The Marketo Measure Campaign Name will also appear on the Touchpoint itself within the Ad Campaign Name field.

**What other Touchpoint fields are populated?**

| **Touchpoint Field** |**Value** |
|---|---|
| Lead/Contact |All activities are related to a Lead or Contact |
| Campaign |Channel.Subchannel [Marketo Measure] |
| Touchpoint Source |CRM Activity |
| Medium |Activity.Type |
| Touchpoint Type |Activity.Type |
| Ad Campaign Name |Marketo Measure Campaign Name |
| Ad Content |Activity Subject |
| Ad Id |Activity External Id |
| Touchpoint Date |[custom - set in apps] |

**What if I need to create a different rule for each Sales Rep? Do I need to create different Marketo Measure Campaigns for each?**

No you do not. We introduced a concept of "Dynamic Campaign Names." This allows you to fill in part (or all) of the Marketo Measure Campaign Name using a "replacement parameter" that references a field from the Activity object. For example, if you have a Marketo Measure Campaign Name titled ???Outbound Call??? but you want the Sales Rep to be at the end, you take the CRM field name and call the Marketo Measure Campaign Name ???Outbound Call {AssignedTo}??? or ???Outbound Call {CreatedBy}."

**How do I set up Activities in the Marketo Measure app?**

Directions on how to configure Activites within the Marketo Measure app can be found in the Marketo Measure Activities support article.

**What do the different operators mean?**

* is equal to: exact match to the value (aka: social)
* contains: the text is in the middle (aka: &#42;social&#42;)
* starts with: the value starts with the text (aka: social&#42;)
* ends with: the value ends with the text (aka: &#42;social)
* matches any: multiple values can be added that are comma separated. If starts with, ends with, or contains operators need to be applied, used the wildcard (&#42;)
* greater than: used for numerical fields or date/time fields
* less than: used for numerical fields or date/time fields

**What Channel will these Activities go under?**

Once the Activity rule, and its corresponding Marketo Measure Campaign Name, are created you???ll use the Online Channels definitions to place those Campaigns under the correct Marketing Channel. Marketo Measure has the ability to define Channels using not only medium and source, but also campaign.

In the example above, to assign the ???Outbound Call {Assigned To}??? campaign to the BDR channel, you???ll want to insert a row in your Online Channels CSV for the BDR channel with a campaign definition of ???Outbound Call&#42;??? - the asterisk denotes a wildcard value, so all campaigns that start with ???Outbound Call??? will fall under the BDR channel, rather than having to create a separate row for each campaign name.

>[!MORELIKETHIS]
>
>[Marketo Measure University: Activities Attribution](https://universityonline.marketo.com/courses/additional-features-1/#/page/5be3747e5b62f440323a468a)
