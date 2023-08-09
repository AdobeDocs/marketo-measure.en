---
unique-page-id: 18874736
description: Remove [!DNL Marketo Measure] Tracking Parameters from the Landing Page URL in Google Analytics - [!DNL Marketo Measure] - Product Documentation
title: Remove [!DNL Marketo Measure] Tracking Parameters from the Landing Page URL in Google Analytics
exl-id: ec81ba4a-bb10-49fd-b62e-5a1bc9e1a023
feature: Tracking
---
# Remove [!DNL Marketo Measure] Tracking Parameters from the Landing Page URL in Google Analytics {#remove-marketo-measure-tracking-parameters-from-the-landing-page-url-in-google-analytics}

Sometimes when viewing landing pages in [!DNL Google Analytics], you'll want to remove tracking parameters from the URLs. Otherwise, they'll split into individual rows.

Luckily, this is an easy fix.

1. In [!DNL Google Analytics], go to [!UICONTROL Admin] >[!UICONTROL View Settings] >[!UICONTROL Exclude URL Query Parameters].
1. Type "_bt,_bk,_bm,_bn,_bg" in the box (minus the quotes).
1. Scroll down and click **[!UICONTROL Save]**.

   Keep in mind that [!DNL Google Analytics] does not reprocess data. Therefore this change will only be reflected moving forward, and your past data will still show with the bt, bk, and bm parameters.
