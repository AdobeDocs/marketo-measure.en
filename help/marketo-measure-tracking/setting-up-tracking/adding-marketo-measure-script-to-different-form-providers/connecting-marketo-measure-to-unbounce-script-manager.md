---
unique-page-id: 18874743
description: Connecting Marketo Measure to Unbounce Script Manager - Marketo Measure - Product Documentation
title: Connecting Marketo Measure to Unbounce Script Manager
exl-id: c3212bc3-1d8f-4da5-bb2d-11ffd2fb4e98
---
# Connecting Marketo Measure to Unbounce Script Manager {#connecting-marketo-measure-to-unbounce-script-manager}

Marketo Measure integrates directly with Unbounce, allowing you to track the digital marketing source of your landing page conversions directly in Salesforce. To make the connection, simply add the Marketo Measure script to your Unbounce Script Manager. Here's how.

1. Log-in to your [!DNL Unbounce] account.
1. Click **[!UICONTROL Settings]** > **[!UICONTROL Script Manager]** > **[!UICONTROL Add Script]**.
1. In the popup, select Custom Script and name it "Marketo Measure Marketing Analytics." Click **[!UICONTROL Add Script Details]**.
1. Select placement in the Head. Include the script on Main Landing Page and Form Confirmation Dialog. Paste the [!DNL Marketo Measure] script below into the box.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Click **[!UICONTROL Save]**.

The Marketo Measure integration works on Unbounce landing pages as long as they are hosted on your domain (e.g., landing.mysite.com) not those using the unbounce.com domain.
