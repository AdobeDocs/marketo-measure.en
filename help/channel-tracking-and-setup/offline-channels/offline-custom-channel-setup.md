---
unique-page-id: 18874598
description: Offline Custom Channel Setup - [!DNL Marketo Measure]
title: Offline Custom Channel Setup
exl-id: c5697714-1a79-40bd-8b7c-e10768f4ef67
feature: Channels
---
# Offline Custom Channel Setup {#offline-custom-channel-setup}

## Getting Started {#getting-started}

Compared to how [!DNL Marketo Measure] handles online channel rules, you will notice the offline channel rules do not require the use of a spreadsheet. However, there is still a sheet provided in the implementation plan because that can be helpful for thinking through the way you want to organize your offline channels.

The spreadsheet has three columns:

![](assets/1-2.png)

**[!UICONTROL Salesforce] Campaign Type** - add Campaign Types identified in [!DNL Salesforce] here

* For example this could be an email, webinar, conference, or any values you created for this field to which you would like to attribute Touchpoints.

**[!UICONTROL Channel]** - add your various marketing channels here

**[!UICONTROL Subchannel]** - add any corresponding subchannels here

## Offline Channel Logic {#offline-channel-logic}

[!DNL Marketo Measure] offline channel logic is determined by the Campaign object, specifically the [!DNL Salesforce] Campaign Type. Each offline effort must have a [!DNL Salesforce] Campaign Type, such as dinner or tradeshow, because [!DNL Marketo Measure] relies on this field to understand which Channel and SubChannel to map to.

The SFDC campaign types will appear in the Offline Channel's tab, listed under [!DNL Salesforce] Campaign Type. Note that [!DNL Marketo Measure] is only able to import SFDC Campaign Types for campaigns that have Buyer touchpoints associated to them.

![](assets/2-2.png)

This is where you can create the Channel/Subchannel mapping in the [!DNL Marketo Measure] app. This will likely involve creating new Channels and Subchannels in the [!DNL Marketo Measure] app, which is done in the Create Channels section of the app--shown in the image below. New Channels and Subchannels need to be created for [!DNL Marketo Measure] to understand where to push Touchpoints. You are able to decide how you would like campaign types to be mapped.

![](assets/3-2.png)

## Channel Mapping Example {#channel-mapping-example}

For example, imagine you attend two [!DNL Salesforce] conferences a year. Each conference however is very different and has a unique target audience. You want to know which of the two brings in more value. In your [!DNL Salesforce] environment, you may give the January event the Campaign Type "Conference," name your channel "[!DNL Salesforce]," and your subchannel "January Conference."

Now you want to do the same for the June conference. You figure since this is a conference also, it can be given the same Campaign Type, in this case, "Conference." The channel is the same, [!DNL Salesforce], and the subchannel for this second conference is "June Conference." This makes sense from an organizational perspective. However, it is very confusing to the [!DNL Marketo Measure] logic to read and apply these rules because both campaigns have the same Campaign Type. [!DNL Marketo Measure] script cannot map data from one type to two different subchannels. This means you would need to create a new Campaign Type for each subchannel, but the subchannels can have the same channel.

Below is an example of logic that [!DNL Marketo Measure] would not be able to read:

![](assets/4-2.png)

In the scenario above, you will want to create a unique Campaign Type because you can't map the same Campaign Type to two different subchannels. Instead, you would want to set up unique types like the following:

![](assets/5-2.png)

Any existing campaign types must be included in your channel map and "NULL" should be added as the channel.

Take time to go into [!DNL Salesforce] to determine the number and nature of your existing record types, which you want to include, and whether you need to create additional campaigns based on the information above. Once you have filled out all the necessary information, you are ready to upload.

Learn more about [syncing offline [!DNL Salesforce] Campaigns with [!DNL Marketo Measure]](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-offline-campaigns.md).

## Handling SFDC Campaigns for Online Marketing Efforts {#handling-sfdc-campaigns-for-online-marketing-efforts}

It's common for Marketing teams to create [!DNL Salesforce] campaigns to track various digital marketing efforts. There is no problem with this practice; however, it is important to treat these campaigns differently than true offline campaigns such as direct mail or conferences, for example. Campaigns that are related to digital events (interactions taking place on your website) should not be synced with [!DNL Marketo Measure]. Syncing these campaigns would result in duplication of Touchpoints because the [!DNL Marketo Measure] JavaScript is already tracking online efforts.

Another tip for handling campaigns for online activities is to map the [!DNL Salesforce] Campaign Type to NULL. To do this, first create a channel in the [!DNL Marketo Measure] app titled NULL as demonstrated in the image below. This is found in the [!DNL Marketo Measure] app under the **Create Channels** section. This will be helpful in case a campaign that should not be synced is synced accidentally. It is easy to find the campaign and correct the sync status by looking at everything bucketed under NULL.

![](assets/6-2.png)

## Entering Your Offline Channel Rules to the App {#entering-your-offline-channel-rules-to-the-app}

Once you've edited and updated the spreadsheet with your custom rules, the next step is to recreate this channel mapping in the [!DNL Marketo Measure] app--you won't actually upload a spreadsheet for offline channels. Rather, you will enter the information in the picklist boxes as displayed in the image below. This is found by clicking **[!UICONTROL Offline Channels]** under the **[!UICONTROL Channels]** section.

![](assets/7-2.png)

>[!TIP]
>
>Want to determine _when_ a [!DNL Salesforce] Campaign Type gets pulled down into [!DNL Marketo Measure] channel mapping? Go to **[!UICONTROL Setup]** > **[!UICONTROL Campaigns]** > **[!UICONTROL Fields]** > **[!UICONTROL Type]**. You can then see which values are in the picklist, and which are inactive. Inactive ones won't show up as a selectable type in our "[!UICONTROL Offline Channels]" section. Note, this process can take anywhere from a few minutes up to 48 hours.

Click **[!UICONTROL Save]** when you are finished and [!DNL Marketo Measure] will upload the changes and reprocess the data.

>[!MORELIKETHIS]
>
>* [[!DNL Marketo Measure] Tutorials: Mapping Offline Channels](https://experienceleague.adobe.com/en/docs/marketo-measure-learn/tutorials/onboarding/marketo-measure-salesforce/mapping-offline-channels){target="_blank"}
>
>* [[!DNL Marketo Measure] Tutorials: Syncing Offline Campaigns](https://experienceleague.adobe.com/en/docs/marketo-measure-learn/tutorials/onboarding/marketo-measure-salesforce/syncing-offline-campaigns){target="_blank"}
>
>* [Marketo Engage Programs Integration](/help/marketo-measure-and-marketo/marketo-measure-integrations-with-marketo/marketo-engage-programs-integration.md#channel-mapping){target="_blank"}
