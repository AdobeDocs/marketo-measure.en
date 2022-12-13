---
description: Best Practices for Online Channels - [!DNL Marketo Measure] - Product Documentation
title: Best Practices for Online Channels
exl-id: 766cb01c-98b3-492d-bb35-e0a78b76333a
---
# Best Practices for Online Channels {#best-practices-for-online-channels}

## Overview {#overview}

To have accurate [!DNL Marketo Measure] reporting, your marketing channels must be correctly setup. The marketing channel field displays the highest-level group of marketing activities that a touchpoint can belong to (e.g., Paid Search, Direct, Social, etc).

There are two aspects to setting up your marketing channels: online and offline. This document will be focused on the [!DNL Marketo Measure] best practice recommendations for setting up and maintaining your Online Channels.

Online Channel rules are the guidelines for how [!DNL Marketo Measure] maps your digital touchpoints, i.e. any touchpoints that are tracked and created via the [!DNL Marketo Measure] JS on your site. If these rules are not comprehensive, or not ordered correctly, touchpoints can be attributed to the incorrect channel, therefore diminishing the accuracy of your reporting. Ensuring that your Online Channel rules are accurate and up to date will guarantee that your digital data is being attributed to the correct channel and subchannels in your [!DNL Marketo Measure] Reporting.

## Best Practice {#best-practice}

Whether you're setting up your rules for the first time or just reviewing them to check for accuracy, keep the following best practices in mind.

Take some time to think about the organization of your marketing campaigns and how they fit into the [!DNL Marketo Measure] framework. Determine which Channels and Subchannels should be represented in your Online Channels as well as what campaigns, UTM parameters, or referring websites differentiate those channels from one another.

Things to keep in mind:

* All digital channels and subchannels should be represented with at least one rule
   * If the channel does not drive people to your site, it is not an Online Channel
* It's okay to have multiple rules for one channel/subchannel
   * Multiple rules can be thought of as "casting a wider net" to ensure that each touchpoint is mapped correctly. Often parameters can be incorrectly added or missed completely, therefore having multiple rules to capture a channel/subchannel is a good idea to ensure mapping accuracy.
* [!DNL Marketo Measure] logic prioritizes touchpoint mapping in descending order starting with the top row of the spreadsheet and making its way down
   * [!DNL Marketo Measure] reads each rule (row), looking for the true and first fit. The touchpoint is then mapped to that channel/subchannel
   * Do not sort your sheet in alphabetical order as this will interfere with the logic rules.
* Maintain the bracketed rules, do not edit or add to the bracketed rules (example; [AdWords Paid Search] or [Facebook Paid] )
   * These are out of the box [!DNL Marketo Measure] rules that have built in logic, which are tied the [!DNL Marketo Measure] integrations. Give these rules top priority for that channel/subchannel section to ensure the [!DNL Marketo Measure] integrations are able to work as designed.
* Once the file is uploaded, you cannot change any of the rules for seven days
   * [!DNL Marketo Measure] utilizes this time to process and update the Touchpoints, therefore make sure to double check your rules before uploading.

## Best Practice for Maintenace {#best-practice-for-maintenace}

Once saved and processed, Online Channel rules continuously work to bucket your digital touchpoints. However certain changes or scenarios cause you want to review your Online Channel setup. [!DNL Marketo Measure] recommends that you review your Online Channel rules once every six months. This will ensure that your [!DNL Marketo Measure] data is aligned with your internal definitions of online channels/subchannels and your usage of UTMs.

Other items that might trigger your team to do Online Channel maintenance include....

* New digital channel/subchannel is launched
* UTM parameters are updated or changed
* Changes to your channel organization or naming conventions
* Turnover in your marketing team

If your team has experienced any of the above recently [!DNL Marketo Measure] recommends that you review your online channels rules and make the appropriate changes.

>[!MORELIKETHIS]
>
>* [Online Channel Setup](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md)
>* [UTM Parameters](/help/channel-tracking-and-setup/online-channels/utm-parameters.md)
>* [Marketing Channel and Subchannel](/help/channel-tracking-and-setup/online-channels/marketing-channels-and-subchannels.md)
>* [UTM Best Practices](/help/channel-tracking-and-setup/online-channels/best-practices-for-setting-up-utm-parameters.md)
