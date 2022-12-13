---
description: Best Practices for Offline Channels - [!DNL Marketo Measure] - Product Documentation
title: Best Practices for Offline Channels
exl-id: 71c50614-8d5b-469f-bc02-3cc489464a4e
---
# Best Practices for Offline Channels {#best-practices-for-offline-channels}

## Overview {#overview}

To have accurate [!DNL Marketo Measure] reporting, your Marketing Channels must be correctly setup. The '[!UICONTROL Marketing Channel]' field displays the highest-level group of marketing tactics that a touchpoint can belong to (e.g., Events, Webinars, Content Syndication, etc).

There are two aspects to setting up your marketing channels: online and offline. This document will be focused on the [!DNL Marketo Measure] best practice recommendations for setting up and maintaining your Offline Channels and how they are synced with [!DNL Marketo Measure] via CRM Campaigns.

Offline Channels have two key aspects:

1. Offline Channel Mapping which is the framework that tells [!DNL Marketo Measure] which Channel and Subchannel the Offline touchpoint belong to
1. Offline Campaign Sync which is the creation of the Offline touchpoints

Offline touchpoints are created from a CRM Campaign and meant to track any marketing interaction that can't be tracked digitally via the [!DNL Marketo Measure] JavaScript that is implemented on the pages of your website. When a CRM Campaign is synced with [!DNL Marketo Measure], touchpoints are created for the defined Campaign Members within the Campaign.

The 'Marketing Channel' value for these touchpoints is based on the 'Type' field on the Campaign. The mapping of 'CRM Campaign Type' to 'Marketing Channel' and 'Subchannel' is managed within the 'Offline Channels' tab of your [!DNL Marketo Measure] Account Settings. Ensuring that your Offline Channel mapping is accurate and up to date will guarantee that your offline touchpoint data is being attributed to the correct Marketing Channels and Subchannels within your [!DNL Marketo Measure] Reporting.

## Best Practice | Offline Channel Mapping {#best-practice-offline-channel-mapping}

Whether you're mapping your Offline Channels for the first time or just reviewing them to check for accuracy, keep the following best practices in mind.

* Create a deliberate framework for you Offline Channels
   * Take some time to think about the organization of your marketing campaigns and how they fit into the [!DNL Marketo Measure] framework. Determine which Channels and Sub Channels should be represented in your Offline Channels as well as what CRM Campaign Types differentiate those channels from one another
* Work to utilize your current CRM Campaign 'Type' values first
   * Offline Channels are defined by CRM Campaign 'Type', however, custom CRM Campaign 'Type' value may need to be created to accommodate ideal Offline Channel and Subchannel values. Ideal custom CRM Campaign 'Type' values should carry the naming convention shown below:
      * CHANNEL - SUBCHANNEL
      * Example: Event - Tradeshow
      * This ensures mapping to the Subchannel level is as easy and clean as possible
* One Subchannel only can be mapped to one CRM Campaign 'Type'
   * Multiple CRM Campaign 'Types' can be mapped to a single Channel, but only one CRM Campaign 'Type' can be mapped to each Subchannel within each Channel
* Only OFFLINE CRM Campaign 'Types' should be mapped to Offline Channels as only Offline Campaigns are to be synced with [!DNL Marketo Measure] to create touchpoints:
   * ONLINE CRM Campaign 'Types' should be mapped to a [!UICONTROL Marketing Channel] = "NULL". This value is recommended as it acts as a 'red flag' that denotes your Offline Channels have been reviewed and any CRM Campaign 'Type' that is mapped to "NULL" is an ONLINE 'Type' and should not be synced with [!DNL Marketo Measure]. Touchpoints related to Online CRM Campaign 'Types' would be already be tracked via [!DNL Marketo Measure] Online functionality and channels. Syncing these Campaigns runs the risk of "duplicate" touchpoints/double counting

## Best Practice | Offline Campaign Sync {#best-practice-offline-campaign-sync}

* Make sure the 'Type' field is accurate on each CRM Campaign
   * 'Type' determines Marketing Channel and Subchannel for any touchpoints sourced from the Campaign once synced
* Whether using the CRM-based Campaign Sync method (Enable Buyer Touchpoints) or the [!DNL Marketo Measure] App-based sync method (Custom Campaign Sync within the '[!UICONTROL Campaigns]' tab of your [!UICONTROL Marketo Measure] Account Settings), offline touchpoints should only be created if the Campaign Member had an actual offline engagement with the Campaign and your brand:
   * For Offline Channels like Events or Webinars: "registrations" are typically tracked via form submissions on your website and [!DNL Marketo Measure] Online functionality. Therefore, the Campaign Members with a Status of "Registered" should not receive an Offline touchpoint from the Campaign to avoid double counting. Offline touchpoints should be representative of the "attendance" to the Event or Webinar only.
   * Some Offline Channels like Content Syndication are usually more straightforward in that every Campaign Member has the same 'responded' status that represents they did indeed respond to the campaign, in this case, download content on a third-party site and therefore should receive an offline touchpoint
* When using the Custom Campaign Sync method in the [!DNL Marketo Measure] App, be sure the 'Touchpoint Date' field is based on the date field from either the Campaign or Campaign Member that is most indicative of when the touchpoint interaction actually occurred
* Leverage the 'Bulk Update Touchpoint Date' button if you need to override the 'Touchpoint Date' for any of the offline touchpoints sourced from a CRM Campaign. 'Touchpoint Date' needs to be as accurate as possible to ensure the touchpoint holds the most accurate possible 'Touchpoint Position' and thus, the proper amount of attribution credit

## Best Practice for Maintenance {#best-practice-for-maintenance}

Once initially setup, your Offline Channel setup will continue to create offline touchpoints accordingly. As a best practice, we recommend that you review your Offline setup at least twice a year. This will guarantee clean and accurate Buyer touchpoint data.

Additionally, if you make any changes to your Campaign management or processes, you'll need to make sure you're updating your [!DNL Marketo Measure] Offline Channel mapping and/or sync process.

Changes that might trigger your team to make updates to the Offline Channel setup in [!DNL Marketo Measure] might include:

* CRM Campaign 'Type(s)' created or edited
* Campaign Member 'Status' created or edited
* If using the CRM Campaign Sync method via the 'Enable Buyer Touchpoints' field, make sure this field is reviewed and updated for every CRM Campaign that is created. If this field is neglected, there will not be any related offline touchpoint data
* If you come across any offline touchpoints from a CRM Campaign that look to be online touchpoints (Marketing Channel = NULL), make sure the related CRM Campaign is reviewed and the sync disabled

If your team has recently experienced any of the above, [!DNL Marketo Measure] recommends that you review your Offline Channel mapping and Offline Campaigns to make the appropriate changes and ensure they are synced properly.

>[!MORELIKETHIS]
>
>* [Offline Channel Setup](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md)
>* [Custom Campaign Sync - App Sync](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md)
>* [Syncing Offline Campaigns - CRM Sync](/help/channel-tracking-and-setup/offline-channels/syncing-offline-campaigns.md)
>* [Offline Campaign & Campaign Members - CRM Sync](/help/channel-tracking-and-setup/offline-channels/campaigns-and-campaign-members.md)
>* [Campaign Sync Dates - CRM Sync](/help/channel-tracking-and-setup/offline-channels/campaign-sync-dates.md)
>* [Configurations for Multiple Campaign Record Types](/help/channel-tracking-and-setup/offline-channels/configurations-for-multiple-campaign-record-types.md)
>* [Creating a Campaign List View](/help/channel-tracking-and-setup/offline-channels/creating-a-campaign-list-view-for-salesforce-campaigns.md)
>* [Syncing Historical Data](/help/channel-tracking-and-setup/offline-channels/syncing-historical-data.md)
