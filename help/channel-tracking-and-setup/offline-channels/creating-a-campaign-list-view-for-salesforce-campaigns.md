---
unique-page-id: 18874718
description: Creating a Campaign List View for [!DNL Salesforce Campaigns] - Marketo Measure - Product Documentation
title: Creating a Campaign List View for [!DNL Salesforce] Campaigns
exl-id: 8c673ea3-ac24-4b3d-b67d-76888179c07a
---
# Creating a Campaign List View for [!DNL Salesforce] Campaigns {#creating-a-campaign-list-view-for-salesforce-campaigns}

Learn how to create a List View for those campaigns that you want to sync with Buyer Touchpoints.

The Campaign list view that can be created allows you to have a 'go-to' location to see and manage the 'Type' and 'Enable Buyer Touchpoints' fields to ensure that each of your [!DNL Salesforce] campaigns that inform your offline marketing channels are setup properly.

1. Head to [!UICONTROL Campaigns] tab in [!DNL Salesforce] and create a new list view
1. Name the view 'Campaigns to sync with Marketo Measure'
1. We want this list to only show those campaigns that we want to sync with [!DNL Marketo] Measure so we need a couple filters:

   * **Type** [EQUALS] 'All the Campaign Types that we have mapped to your offline channels'. Refer to your Implementation Plan or the Offline Channels tab in Marketo Measure ([experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} -> My Account -> Settings -> Offline Channels). You can select the Types you want (those that are mapped to an offline marketing channel) via the magnifying glass icon.

      * Choose 3 Types max for each filter. There is a limit of characters you can have in a filter field. Start with 3 Types per filter and add additional rows of ‘Type’ filters if necessary.
   * **Created Date** [GREATER OR EQUAL] your Marketo Measure start date. You can find your start date in the ROI dashboard within the Marketo Measure App. Just select 'Since Creation Date' in the date range of the dash and it will show your start date.
   * **&#42;[!UICONTROL Record Type]&#42;** - In order to make edits in the List View, you need to add a filter for Record Type. Each campaign record you may need to edit needs to be the same Record Type.


1. Edit your Selected fields to show in the list view. The complete setup of the list view should look like the example below:

   This view allows you see your campaigns and edit the ‘Type’ and 'Enable Buyer Touchpoints' fields if necessary. As you create new campaigns that should be synced with Marketo Measure, they will surface in this view and you can manage all of the settings for those campaigns right from within the list.

   In order to make inline edits from the List View you need to make sure the following is also true within your [!DNL Salesforce] setup:

   * Setup >[!UICONTROL User Interface] >[!UICONTROL Enable Inline Editing]
   * Also need enable enhanced lists checked (right under the box for inline editing):
   * Make sure to have permissions to the fields.

>[!MORELIKETHIS]
>
>[Troubleshooting common issues with List View Inline Editing](http://help.salesforce.com/articleView?id=000003911&language=en_US&type=1){target="_blank"}
