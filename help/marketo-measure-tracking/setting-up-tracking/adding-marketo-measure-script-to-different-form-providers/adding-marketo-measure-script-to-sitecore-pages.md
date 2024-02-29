---
unique-page-id: 18874747
description: Adding [!DNL Marketo Measure] Script to Sitecore Pages - [!DNL Marketo Measure]
title: Adding [!DNL Marketo Measure] Script to Sitecore Pages
exl-id: 87ce1857-7532-45a7-8c39-255c6118b50a
feature: Tracking
---
# Adding [!DNL Marketo Measure] Script to Sitecore Pages {#adding-marketo-measure-script-to-sitecore-pages}

Content management systems can require additional steps beyond standard script implementation for [!DNL Marketo Measure] to recognize form submissions. The process below outlines how to add the [!DNL Marketo Measure] javascript to your [!DNL Sitecore] pages.

For sites with Sitecore pages:

1. Log-in Sitecore and navigate to your website. Locate the [!UICONTROL Configuration] folder that resides on the same level as your [!UICONTROL Home] item and [!UICONTROL Metadata] folder.
1. Click the **[!UICONTROL +]** next to the [!UICONTROL Configuration] folder.
1. Click the **[!UICONTROL +]** next to the [!UICONTROL Tools] folder.
1. Select the [!UICONTROL Javascript] item.
1. In the [!UICONTROL Content] tab, click the **[!UICONTROL Lock and Edit]** link to unlock the item for editing.
1. Find the [!UICONTROL 'JavaScript'] section. If it's not already expanded, click the **[!UICONTROL +]**.
1. Enter our script: `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js"async=""></script>`
1. Click **[!UICONTROL Save]** in the upper left corner.
