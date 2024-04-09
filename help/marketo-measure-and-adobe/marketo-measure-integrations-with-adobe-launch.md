---
description: '[!DNL Marketo Measure] Integrations with Adobe Launch - [!DNL Marketo Measure]'
title: '[!DNL Marketo Measure] Integrations with Adobe Launch'
exl-id: 316ee8a8-b2d3-42e9-9ee5-c9b1d91c2769
feature: Integration
---
# [!DNL Marketo Measure] Integrations with Adobe Launch {#marketo-measure-integrations-with-adobe-launch}

The Adobe Launch extension is designed for existing [!DNL Marketo Measure] users that already use Adobe Launch on their website. The extension serves as a tag management solution that you can use to configure and dynamically load scripts on your pages based on certain events and conditions.

When installed and configured in Adobe Launch, the [!DNL Marketo Measure] extension loads bizible.js script on the pages where Adobe Launch script is present. This allows marketers to add bizible.js through the Adobe Launch configuration, as opposed to explicitly modifying the web page to add the bizible.js script tag.

## Configure the Adobe Launch Extension {#configure-the-adobe-launch-extension}

>[!PREREQUISITES]
>
>Check out the following links to learn more about Adobe Launch and its extensions:
>
>* [[!DNL Marketo Measure] Extension](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email/bizible.html#catalog){target="_blank"}
>* [Adobe Launch Overview](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/overview.html){target="_blank"}
>* [Adobe Launch Extension Overview](https://experienceleague.adobe.com/docs/experience-platform/tags/extension-dev/overview.html){target="_blank"}

1. Create a property following the steps [in this article](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html#go-to-the-data-collection-interface){target="_blank"}. 

1. Click the property that you created.

   ![](assets/marketo-measure-integrations-with-adobe-launch-1.png) 
 
1. Click **[!UICONTROL Extensions]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-2.png)
 
1. Click the **[!UICONTROL Catalog]** tab and search for "[!UICONTROL Bizible]."

   ![](assets/marketo-measure-integrations-with-adobe-launch-3.png)

1. In the [!UICONTROL Bizible Analytics] tile, click **[!UICONTROL Install]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-4.png)

1. In the Bizible AccountId field, type in the URL of your website (for example, `adobe.com`).

   ![](assets/marketo-measure-integrations-with-adobe-launch-5.png)

1. Click **[!UICONTROL Save]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-6.png)

1. Click **[!UICONTROL Rules]**, then select **[!UICONTROL Create New Rule]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-7.png)

1. Click the **[!UICONTROL Add]** button under [!UICONTROL Events]. 

   ![](assets/marketo-measure-integrations-with-adobe-launch-8.png)

1. In the Extension drop-down, select **[!UICONTROL Core]**. Then in the Event Type drop-down, select **[!UICONTROL Library Loaded (Page Top)]**. If you don't give your event a name, a default one is applied. Click **[!UICONTROL Keep Changes]** when done.

   ![](assets/marketo-measure-integrations-with-adobe-launch-9.png)

1. Click the **[!UICONTROL Add]** button under Actions.

   ![](assets/marketo-measure-integrations-with-adobe-launch-10.png)

1. In Extension drop-down, select **[!UICONTROL Bizible Analytics]**. Then in the Action Type drop-down, select **[!UICONTROL Initialize]**. If you don't give your action a name, a default one is applied. Click **[!UICONTROL Keep Changes]** when done.

   ![](assets/marketo-measure-integrations-with-adobe-launch-11.png)

1. Click **[!UICONTROL Save]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-12.png)

