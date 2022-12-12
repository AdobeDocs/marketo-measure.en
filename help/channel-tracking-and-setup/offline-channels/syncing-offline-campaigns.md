---
unique-page-id: 18874600
description: Syncing Offline Campaigns - [!DNL Marketo Measure] - Product Documentation
title: Syncing Offline Campaigns
exl-id: a6f9e217-ff6e-474d-9f14-c6f6238c9e84
---
# Syncing Offline Campaigns {#syncing-offline-campaigns}

It can be difficult to accurately track offline campaigns and understand how they compare to your digital marketing efforts. [!DNL Marketo Measure] enables you to track and attribute Touchpoints to your offline campaigns in [!DNL Salesforce], even in situations when a [!DNL Salesforce] campaign isn't created until a few weeks after the event.

## Before You Sync {#before-you-sync}

Here are some tips for an efficient syncing process:

* Offline campaigns refer to marketing interactions that do not occur online. These include marketing channels like events, webinars, and tradeshows. Only include offline marketing campaigns.
* If you want to include campaigns that tracked online activity prior to when you installed [!DNL Marketo Measure], be sure to set the Touchpoint End Date as the date our JavaScript was deployed on your site.
* It is helpful to keep the [!DNL Marketo Measure] app open on the Offline Channels page so that it is easy to identify the different Campaign Types, along with what Marketing Channel the Touchpoints will be bucketed into.
* Double check everything before you hit the "[!UICONTROL Save]" button!

## Bulk Update Touchpoint Date {#bulk-update-touchpoint-date}

In Salesforce, the Created Date field on the Campaign Member Object notes the date the Campaign Member was added to the campaign. In order for the syncing process to go smoothly, make sure the Buyer Touchpoint Date Field has the same date as the date on the Salesforce Campaign Member Object. This step is performed using the "[!UICONTROL Bulk Update Touchpoint Date button]," _before_ you select the [!UICONTROL picklist] option in the Enable Buyer Touchpoints field.

Why is this important? Imagine for a moment that your company sponsored a booth at a conference in January. At the conference, 100 individuals showed interest in your product and provided their contact information to receive email updates. Three weeks later, you finally created a campaign in [!DNL Salesforce] to track the outcome of the conference.

Your upload date would be three weeks later than the conference date. To fix this difference, the [!UICONTROL Bulk Update Touchpoint Date] button can be used to set the appropriate date. The button is pictured in the image below.

![](assets/1-3.png)

In this case, it would backfill the upload date by three weeks. This step should be done prior to setting the "[!UICONTROL Enable Buyer Touchpoints]" field.

In summary, if you use the [!UICONTROL Bulk Update Touchpoint Date] button and change the Touchpoint date to the date of the event, [!DNL Marketo Measure] will generate Touchpoints for the actual date of the event--not the date of the upload.

You can also update the dates for all campaign members on an existing campaign. When doing this, be sure the date of the Touchpoint is the date of the member's interaction. Simply click on the Bulk Update Buyer Touchpoint Date, filter the list of campaign members as appropriate, and in the "[!UICONTROL Select Date]" option above the list of campaign members, add the the same date as the date the event took place.

>[!CAUTION]
>
>Make sure you update the Touchpoint date _before_ you enable Touchpoints for all campaign members.

![](assets/2-3.png)

## How to Create a Campaign and Sync Buyer Touchpoints {#how-to-create-a-campaign-and-sync-buyer-touchpoints}

To create a Campaign in [!DNL Salesforce], navigate to the [!UICONTROL Campaigns] tab and select '[!UICONTROL New]' as shown in the image below. Depending on your [!DNL Salesforce] setup, you might need to add Campaigns to the top bar by clicking the plus (+) icon.

![](assets/3-3.png)

When you are creating this campaign, click the "[!UICONTROL Enable Buyer Touchpoints]" field and select one of the following options from the picklist:

![](assets/4-3.png)

* **Include all campaign members**
   * This option enables [!DNL Marketo Measure] to attribute a Touchpoint to each campaign member.

* **Include "Responded" campaign members.**
   * This option applies Touchpoints to campaign members who have a "Responded" status.

* **Exclude all campaign members.**
   * This option does not attribute Touchpoints to any members in the campaign and acts as a flag that the campaign was deliberately excluded from [!DNL Marketo Measure]. If you ever sync a campaign with Buyer Touchpoints on accident, you can change the status to "Exclude all campaign members," and the Touchpoints will be removed.

Once one of these selections is chosen, [!DNL Marketo Measure] will assign each campaign member a Touchpoint if applicable. The Lead or Contact that is added to the campaign _must_ have an email address associated to their record in order for [!DNL Marketo Measure] to create a touchpoint. Without an email address, [!DNL Marketo Measure] will not assign a touchpoint to the campaign member.

>[!MORELIKETHIS]
>
>[[!DNL Marketo Measure] University: Mapping Offline Channels](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c630eca34d9f0367662b77f)
>
>[[!DNL Marketo Measure] University: Campaign Object Fields](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c63007334d9f0367662b758)
