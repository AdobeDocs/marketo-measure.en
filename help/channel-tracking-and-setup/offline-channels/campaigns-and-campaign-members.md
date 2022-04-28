---
unique-page-id: 18874578
description: Campaigns and Campaign Members - Marketo Measure - Product Documentation
title: Campaigns and Campaign Members
exl-id: e4e2b154-39ac-4295-a541-7fa6112672e3
---
# Campaigns and Campaign Members {#campaigns-and-campaign-members}

Salesforce Campaigns are intended to track lists of Leads and Contacts that are associated to a marketing program, or activity. This has commonly been webinars, or registrations, or booth visits, for example. Marketers can select whether or not a Campaign should get credited in a touchpoint journey.

## Enabling Touchpoints {#enabling-touchpoints}

The Marketo Measure Salesforce Package will include a field labeled “Enable Buyer Touchpoints” on the Campaign object. Once the field has been added to the page layout, it’ll appear similar to this:

![](assets/1.png)

The options available in the picklist are:

![](assets/2.png)

* Include all Campaign Members - Every single Lead or Contact that is added to the campaign will receive a Touchpoint associated to that campaign.
* Include only “Responded” campaign Members - Only Leads or Contacts that have a Campaign Member Status of “Responded” will receive a Touchpoint associated to that campaign.
* Exclude all Campaign Members - None of the Leads or Contacts will receive a Touchpoint associated to that campaign.

Please note that campaign members must have an email address associated to their record in order for Marketo Measure to create a touchpoint. Without an email address, Marketo Measure will not assign a touchpoint to the campaign member.

## Campaign Sync Dates {#campaign-sync-dates}

With the installation of the package, Marketo Measure will also include 2 date fields on the Campaign object: Touchpoint Start Date and Touchpoint End Date.

These dates tell Marketo Measure when we should start or stop including Campaign Members from the Campaign into the touchpoint journey. You can either set one date, or both, or none at all.

## Use Case for Touchpoint Start Date {#use-case-for-touchpoint-start-date}

Start date can be used in the case that an existing Campaign is used for tracking Leads and Contacts, but the user only wants to start measuring once new systems or processes have been in place, so they decide to set a start date once Marketo Measure should start tracking those Campaign Members.

## Use Case for Touchpoint End Date {#use-case-for-touchpoint-end-date}

If before using Marketo Measure, you used a Marketing Automation platform that tracked Leads' digital interactions (IE form submissions), and then uploaded those Leads into a Saleforce Campaign, you can leverage the Touchpoint End Date field. You'd set the Touchpoint End Date as your start date with Marketo Measure and enable Buyer Touchpoints, then each of these Leads' digital interaction would be created as a Touchpoint. The reason you'll set the Touchpoint End Date to be your Start Date with Marketo Measure is because, moving forward, we will be tracking these digital interactions through our javascript.

![](assets/3.png)

## Campaign Members {#campaign-members}

Campaign Members are nested under Campaigns, and are related to a Lead or Contact. A Lead or a Contact can only be added once to a Campaign, which can be problematic depending on the use case of the Campaign. When a Campaign is synced, the campaign membership is used as a marketing activity that is put into the touchpoint journey and treated like a form fill.

## Buyer Touchpoint Status {#buyer-touchpoint-status}

If enabled, Marketo Measure will push a status value onto the Campaign Member across 4 different fields that’s included in the installed package: Touchpoint Status (Lead), Touchpoint Status (Contact), Touchpoint Status (Opportunity), and Touchpoint Status Date. This helps customers audit whether or not a touchpoint has been created as a Buyer Touchpoint or Buyer Attribution Touchpoint, depending on the object that it’s related to. The Touchpoint Status Date is simply the last date that the status was updated on the Campaign Member.

![](assets/4.png)

## Buyer Touchpoint Date {#buyer-touchpoint-date}

With the installation of the package, Marketo Measure also includes a field on the Campaign Member labeled “Buyer Touchpoint Date.” This allows the user to override the date that Marketo Measure would use for the Touchpoint Date on the Touchpoint record.

This could be necessary if a list was uploaded days/weeks/months after an event actually occurred. There are ways to update all records at once, which is explained below.

![](assets/5.png)

To know if you need to use the Buyer Touchpoint Date or not, here are how the dates are determined by Marketo Measure depending on the Sync Type that is selected for the Campaign.

If the Sync Type is set to “Include all Campaign Members,” the priority of setting the Touchpoint Date is from top to bottom:

* Buyer Touchpoint Date
* Campaign Member Created Date

If the Sync Type is set to “Include only ‘Responded’ Campaign Members,” the priority of setting the Touchpoint Date is from top to bottom:

* Buyer Touchpoint Date
* First Responded Date
    * The First Responded Date is automatically set as soon as the Status is changed to “Responded” and is a standard Salesforce field that cannot be changed

* Campaign Member Created Date

## Bulk Update Touchpoint Date {#bulk-update-touchpoint-date}

The Bulk Update Touchpoint Date is included in the installed Marketo Measure Salesforce package and button will need to be added to the page layout.

![](assets/6.png)

If a large number of Campaign Member records needs to be updated, you can use the Bulk Update Touchpoint Date button to mass edit.

If there are unique use cases that this interface doesn’t cover, you can also use the [Data Loader](https://dataloader.io/) to export the records, make the change, and upload the records back in.

Start by searching for the records and filtering the ones that you want to set a Buyer Touchpoint Date for.

>[!CAUTION]
>
>There is one search that does not work, which is displayed in the example below. The UI does not support searching for null Buyer Touchpoint Dates (the below search would not work):

![](assets/7.png)

If you don’t need to use the search and just apply the dates to every Campaign Member record, use the “Include All Records” checkbox (see screenshot below), which will check all records on all pages.

Select the date and time from the calendar picker. If you want to select the current date and time, click the date/time that is shown next to the calendar picker.

Once your date and time is set, click the **Update Selected Records** button to apply the changes.

![](assets/8.png)

## Campaign Costs {#campaign-costs}

Learn all about Campaign Costs [in this article](/help/marketing-spend/spend-management/crm-campaign-costs.md).

## Campaign Member Removal {#campaign-member-removal}

The way that Marketo Measure keeps up with any deleted records in Salesforce, whether they’re deleted Leads or Accounts or Opportunities is to see those records in the API and track that an entry is marked as “IsDeleted.” Unfortunately with Campaign Members, Salesforce introduced a different way of deleting these Campaign Members from a Campaign and they’re actually just marked as “removed” as opposed to “deleted” so the issue is that touchpoints were still living in Salesforce that were related to deleted Campaign Members.

To get around this issue, Marketo Measure created a Marketo Measure History object and a trigger to track whenever Campaign Members are removed and then delete the corresponding touchpoint. **You will need Marketo Measure Marketing Analytics package V6.15 or higher** to use this feature.

>[!CAUTION]
>
>Keep in mind that this trigger does not track any campaign members that were removed in the past, so this only works moving forward. If you need to remove a large number of past campaign members' touchpoints, contact [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

>[!MORELIKETHIS]
>
>[Marketo Measure University: Campaign Object Fields](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c63007334d9f0367662b758)
>
>[Marketo Measure University: Mapping Offline Channels](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c630eca34d9f0367662b77f)
