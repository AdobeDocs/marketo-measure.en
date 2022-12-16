---
unique-page-id: 18874554
description: Touchpoint Generation and Mapping - [!DNL Marketo Measure] - Product Documentation
title: Touchpoint Generation and Mapping
exl-id: bb4988f5-4fbc-43b7-9544-da541b8e1d32
---
# Touchpoint Generation and Mapping {#touchpoint-generation-and-mapping}

[!DNL Marketo Measure] attribution stories hinge on two processes:

* Touchpoint generation, which creates touchpoints that represent a person's interactions with your marketing and sales efforts
* Touchpoint mapping, which credits touchpoints to the appropriate channel and subchannel

In order for you to get the most out of [!DNL Marketo Measure], you should work with your [!DNL Marketo Measure] rep to customize both processes to suit your organization's needs.

Touchpoint Generation Methods

The touchpoint generation process answers the question, "How is [!DNL Marketo Measure] going to know that this occurred?" Depending on your feature set and the types of interactions your prospective customers can have, there are up to three ways [!DNL Marketo Measure] can pick up on an interaction and create a touchpoint to represent it.

| **Type of Interaction** | **Example** | **Touchpoint Generation Method** |
|---|---|---|
| Online, on your site(s) | Form fill | [!DNL Marketo Measure] JavaScript |
| Offline; Online not on your site(s) | Tradeshows; Content syndication partner delivers a list of Lead who engaged with your content | CRM Campaign membership synced to [!DNL Marketo Measure], either by setting the Campaign Sync Type directly in the campaign or by setting rules on the Campaigns page in [!DNL Marketo Measure] |
| Sales activity | Outbound call by SDR | CRM Activity (Task or Event) record synced to [!DNL Marketo Measure], through logic on the [!UICONTROL Activities] page in [!DNL Marketo Measure] |

Touchpoint Mapping Methods

The touchpoint mapping process answers the question, "Once this touchpoint's been created, how is [!DNL Marketo Measure] going to know what channel and subchannel it belongs to?" Each method of touchpoint generation has its own method of touchpoint mapping.

| **Type of Interaction** | **Generation Method** | **Mapping Method** |
|---|---|---|
| Online, on your site(s) | [!DNL Marketo Measure] JavaScript | Through the [!DNL Online Channels] page in [!DNL Marketo Measure], by referencing UTM values, landing page, and referring page information |
| Offline; Online, not on your site(s) | CRM Campaign membership sync | Through the [!UICONTROL Offline Channels] page in [!DNL Marketo Measure], by referencing Campaign Type |
| Sales activity | CRM Activity sync | Through the [!UICONTROL Online Channels] page in [!DNL Marketo Measure], by referencing the Campaign Name assigned on the [!UICONTROL Activities] page |

>[!MORELIKETHIS]
>
>* [Mapping Online Touchpoints to [!DNL Marketo Measure] Channels/Subchannels](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md)
>* [Syncing CRM Campaigns from within SFDC](/help/channel-tracking-and-setup/offline-channels/syncing-offline-campaigns.md)
>* [Syncing CRM Campaigns from within [!DNL Marketo Measure]](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md)
>* [Mapping CRM Campaigns to [!DNL Marketo Measure] Channels/Subchannels](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md)
>* [Creating Touchpoints from Sales Activities](/help/advanced-marketo-measure-features/activities-attribution/salesforce-activities-attribution.md)
>* [Activities FAQ and Mapping Activities Touchpoints to Channels/Subchannels](/help/advanced-marketo-measure-features/activities-attribution/activities-attribution-faq.md)

