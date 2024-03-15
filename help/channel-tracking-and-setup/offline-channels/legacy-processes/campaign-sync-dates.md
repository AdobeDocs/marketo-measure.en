---
unique-page-id: 18874684
description: Campaign Sync Dates - [!DNL Marketo Measure]
title: Campaign Sync Dates
exl-id: 66ce9948-9297-47ef-8b16-0ac45c5664fc
feature: Channels
---
# Campaign Sync Dates {#campaign-sync-dates}

Learn what the Campaign Sync Dates feature does, as well as offer some use cases for this feature.

>[!NOTE]
>
>This article covers an outdated process. We encourage users to use the [new, improved in-app process](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md){target="_blank"}.

**[!DNL Marketo Measure] Package Required: 6.9 or above**

This feature consists of two simple date fields on the [!DNL Salesforce] Campaign Object:

* Touchpoint Start Date
* Touchpoint End Date

Once Buyer Touchpoints are enabled on a particular campaign, Campaign Sync Dates will allow you to set Touchpoint Date parameters on the individual Campaign. So, if you were to add a Touchpoint End Date of March 1st, 2017 then [!DNL Marketo Measure] will only create Touchpoints on Campaign Members that were added to the Campaign before that date. [!DNL Marketo Measure] will not create Touchpoints for campaign members that were added after March 1st, 2017.

![](assets/1.gif)

Similarly, if you were to add a Touchpoint Start Date on a Campaign (let's say January 1st, 2017), then [!DNL Marketo Measure] will not create Touchpoints on Campaign Members that were added to the Campaign before January 1st, 2017. You don't need to add a Touchpoint Start Date if you add a Touchpoint End Date and vice-versa.

## Use cases {#use-cases}

**Back-filling Touchpoints**

There may be times when a marketing team may miss adding utm parameters to a particular marketing effort. Campaign Sync Dates will allow you to (if you use SFDC campaigns for online efforts) back-fill some missed data. Let's say that you are running an e-mail campaign that started May 1st, but your team didn't add utm parameters on that e-mail campaign until May 15th. If you are tracking e-mail conversions via a SFDC Campaign, you will be able to set a Touchpoint End Date of May 15th on that Campaign and enable Touchpoints for 'Responded' members of the Campaign. This action will tell [!DNL Marketo Measure] to create Touchpoints for all of those responses up to May 15th.

**Retroactive Campaign Membership Touchpoints**

If you are a new [!DNL Marketo Measure] customer, you may be interested in bringing some of the marketing data you've been tracking via SFDC Campaigns. However, if you were to enable Touchpoints to your online SFDC campaigns, then you could run into the issue of double counting attribution since [!DNL Marketo Measure] is automatically creating Touchpoints for your online marketing efforts. In an effort to avoid double counting data, you could use Campaign Touchpoint End Dates to set a limit on the Touchpoint dates created by [!DNL Marketo Measure] on the SFDC campaign. As an example, if you wanted to add retroactive conversions for a Social Campaign you've been tracking in SFDC, but you understand that you've added the [!DNL Marketo Measure] JavaScript (which is creating online Touchpoints) on July 1st, then you can edit the Social SFDC Campaign to contain a Touchpoint End Date equal to July 1st and enable Buyer Touchpoints for that Campaign.

There may be many other use cases for Touchpoint End Dates. If you need help figuring out a specific situation, don't hesitate to reach out to [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
