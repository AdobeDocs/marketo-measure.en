---
unique-page-id: 18874769
description: "[!DNL Marketo Measure] Insights Configuration - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Insights Configuration"
exl-id: f6fe296b-d22a-43f2-b124-5d4b2f74d67a
feature: Reporting
TQID: https://experienceleague.adobe.com/5i-eUsazdk6Ahr91VhW31gynWc42FF-TMOs-3PDIZs0
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
    internal-label: Insights
---
# [!DNL Marketo Measure] Insights Configuration {#marketo-measure-insights-configuration}

The [!DNL Marketo Measure] Insights Canvas App should be added to the Lead Page Layout but it requires additional setup in the Connected Apps section of your [!DNL Salesforce] Setup. Follow these instructions to ensure that the Canvas App has the appropriate permissions.

1. Navigate to [!DNL Salesforce] Setup and click **[!UICONTROL Connected Apps]** under the [!UICONTROL Manage Apps] tab.

1. Select the [!DNL Marketo Measure Insights] from the list that populates.

1. Under the [!UICONTROL OAuth] policies section, change the Permitted Users setting to "Admin approved users are pre-authorized." A pop-up appears, click **[!UICONTROL OK]** and then **[!UICONTROL Save]**.

   ![](assets/1-1.png)

1. Once the page is saved, you are able to click the **[!UICONTROL Manage Profiles]** button.

   ![](assets/2-1.png)

1. Select all the profiles that should have access to [!DNL Marketo Measure] Insights and click **[!UICONTROL Save]**.
