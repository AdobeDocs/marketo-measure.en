---
description: Best Practices for API Connections - [!DNL Marketo Measure]
title: Best Practices for API Connections
exl-id: b8550e4e-a567-427f-b5d3-50232553a066
feature: APIs, Integration
---
# Best Practices for API Connections {#best-practices-for-api-connections}

## Overview {#overview}

[!DNL Marketo Measure] offers API connections with [!DNL Google AdWords], [!DNL Microsoft Bing Ads], [!DNL Facebook Ads], and LinkedIn. These API connections enable [!DNL Marketo Measure] to pull a variety of data from your ad platforms that can then be reported on in your Buyer Touchpoint data. A key feature to these API connections is their ability to pull spend data automatically, saving you and your team the time and effort it takes to manually upload data for ROI reporting. Setting up these API connections is not mandatory for [!DNL Marketo Measure] to track those channels, but they do provide valuable granular details that enhance your reporting.

The [!DNL Marketo Measure] API connections are an invaluable aspect of your account and our best practice recommendations will help you and your team utilize our connections to the fullest extent.

## Best Practice {#best-practice}

Regardless of the ad platform you are connecting, the following guidelines are important to keep in mind!

* Use an admin to connect
* You can connect multiple ads accounts for one platform
* Connect all possible ad accounts to automate your spend reporting as much as possible
* If available, always implement a tracking template. The template ensures that even if the ad account becomes disconnected, [!DNL Marketo Measure] is still able to pull in granular ad details

To optimize each [!DNL Marketo Measure] API, abide by the following best practices.

**[!DNL Facebook]**: Connect with auto-tagging

Prior to enabling auto-tagging, export your ad history to a csv. Enabling auto-tagging will reset the conversion history and social proof of all of the ads tagged by [!DNL Marketo Measure].

By following our best practice recommendation, the [!DNL Marketo Measure] [!DNL Facebook] API will be able to:

* Auto-tag all [!DNL Facebook] Ads with the necessary [!DNL Marketo Measure] parameter `_bf ={creative}`
* Download ad cost information across all active [!DNL Facebook] ads

>[!NOTE]
>
>There is no tracking template for [!DNL Facebook], the API relies on the auto-tagged (_bf) parameter to gather the ad details.

**AdWords**: Implement a tracking template at the account level and enable auto-tagging

[!DNL Marketo Measure] recommends using an Account-Level, Campaign-Level, or Ad Group-Level Tracking template, as it allows for the addition and subtraction of parameters for all ads without the risk of Ad History interruptions or deletion.

By following our best practice recommendation, the [!DNL Marketo Measure] AdWords API will be able to:

* Auto-tag all AdWords Ads with the [!DNL Marketo Measure] parameters of `_bk={keyword}, _bt={creative}, _bm={matchtype}, _bn={network}, _bg={adgroupID}`
* Download ad cost information across all active AdWords ads

**Bing**: Implement a tracking template at the account level and enable auto-tagging

There is no risk of losing ad history when setting up your [!DNL Bing] API connection, unlike some of our other API connections.

By following our best practice recommendation, the [!DNL Marketo Measure] Bing API will be able to:
* Auto-tag all Bing Ads with the following parameters of `_bt={adid}, utm_medium=cpc, utm_source=bing, utm_term={keyword}`
* Download ad cost information across all active Bing ads

**LinkedIn**: Connect with auto-tagging

Enabling auto-tagging recreates a Share and places it in a new Creative, the old Creative gets archived.

By following our best practice recommendation, the [!DNL Marketo Measure] LinkedIn API will be able to:

* Auto-tag all LinkedIn ads which are ad type Sponsored Content with the necessary [!DNL Marketo Measure] parameter _bl={creativeId}. This parameter pull in the creative ID allowing [!DNL Marketo Measure] to resolve the campaign and creative information.
* Download ad cost information across all active and supported [!DNL LinkedIn] ads

>[!NOTE]
>
>There is no tracking template for [!DNL LinkedIn], the API relies on the auto-tagged (_bl) parameter to gather all possible ad details.

## Best Practice for Maintenance {#best-practice-for-maintenance}

While following our best practices will protect you from losing data if disconnected, we still recommend that you review your connection on a regular basis, monthly if possible. This is a simple visual check of the [!UICONTROL Connections] section in your [!DNL Marketo Measure] app to make sure there are no red key icons present, signaling a disconnected account.

When an API connected account is disconnected, [!DNL Marketo Measure] is not able to pull spend data in or tag new ads. This is why we always recommend implementing a tracking template if possible. The template ensures that even if the ad account becomes disconnected, [!DNL Marketo Measure] is still able to tag the ads and pull in granular ad details. Once reconnected, the spend data will back fill and the disruption to your Paid Channel reporting is minimal.

Reasons for disconnection and reauthorization include...

* Change in password to the person account who is connected
* That person is no longer at the company
* Updates to the APIs

If your team has experienced any of the above scenarios, check your API connections in the [!DNL Marketo Measure] app to make sure they do not need to be reauthorized.

>[!MORELIKETHIS]
>
>* [Integrated Ad Platforms (APIs)](/help/api-connections/utilizing-marketo-measures-api-connections/integrated-ad-platforms.md)
>* [How Bid Management Tools Affect [!DNL Marketo Measure]](/help/api-connections/utilizing-marketo-measures-api-connections/how-bid-management-tools-affect-marketo-measure.md)
>* [[!DNL Marketo Measure] API Parameters Explained](/help/api-connections/utilizing-marketo-measures-api-connections/marketo-measure-parameters.md)
>* [Facebook API Overview](/help/api-connections/utilizing-marketo-measures-api-connections/facebook-api.md)
>* [[!DNL LinkedIn] Integration Overview](/help/api-connections/utilizing-marketo-measures-api-connections/linkedin-integration.md)
>* [AdWords Integration Overview](/help/api-connections/utilizing-marketo-measures-api-connections/understanding-marketo-measure-adwords-tagging.md)
>* [Reauthorizing Connected API Accounts](/help/api-connections/utilizing-marketo-measures-api-connections/reauthorizing-connected-accounts.md)
