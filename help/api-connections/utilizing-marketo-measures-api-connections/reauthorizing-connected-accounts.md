---
unique-page-id: 18874690
description: Reauthorizing Connected Accounts - [!DNL Marketo Measure]
title: Reauthorizing Connected Accounts
exl-id: 7abd1d67-5bed-45bb-844f-0ffd23c3d7f8
feature: APIs, Integration
---
# Reauthorizing Connected Accounts {#reauthorizing-connected-accounts}

When an account becomes disconnected from your [!DNL Marketo Measure] account, the platform's status will change to 'Authorization Required' and display a red key icon.

If your ad platform becomes disconnected, [!DNL Marketo Measure] will not be able to download cost data or, if you have autotagging enabled, append the [!DNL Marketo Measure] UTM parameters to any newly created ads. [!DNL Marketo Measure] will not be able to retroactively append the UTM parameters to any touchpoints created from the ad platform while the account was disconnected.

If your CRM platform becomes disconnected, [!DNL Marketo Measure] will not be able to update [!DNL Marketo Measure] data or push any new touchpoints into your org. Once the CRM connection has been re-established, [!DNL Marketo Measure] will push any data that was missed while the account was disconnected.

![](assets/1-1.png)

## Re-Authorizing Disconnected accounts {#re-authorizing-disconnected-accounts}

1. Go to [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} and log in.
1. Select **[!UICONTROL Settings]** under the [!UICONTROL My Account] tab in the top left corner.
1. Find the Integrations section on the left and click **[!UICONTROL Connections]**.
1. Select the Red Key symbol next to the account that needs to be reconnected.
1. A pop-up window will appear, prompting you to provide the login details for the account.
