---
unique-page-id: 18874797
description: Adding [!DNL Marketo Measure] Script via [!DNL Google Tag Manager] - [!DNL Marketo Measure]
title: Adding [!DNL Marketo Measure] Script via [!DNL Google Tag Manager]
exl-id: 539efb10-35cb-4146-8eea-728c3948a11e
feature: Tracking
---
# Adding [!DNL Marketo Measure] Script via [!DNL Google Tag Manager] {#adding-marketo-measure-script-via-google-tag-manager}

When installing the [!DNL Marketo Measure] JavaScript, it is recommended that you [hard-coding the script](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script.md){target="_blank"} directly into the site. If that is not possible, you can also use [!DNL Google Tag Manager] (GTM) to load the [!DNL Marketo Measure] JS. Note that [!DNL Marketo Measure] JS loaded through GTM is susceptible to latency. Latency causes a delay in script load times which can result in missing around 3-5% of all form submissions.

If you decide to add our script via GTM, set the [!DNL Marketo Measure] script to the highest priority in your firing order and ensure that there are no synchronous scripts in front of the [!DNL Marketo Measure] tag to reduce any effects from GTM latency.

>[!NOTE]
>
>Use this [support article by Google](https://support.google.com/tagmanager/answer/2772421?hl=en){target="_blank"} to learn more.

## How to Add [!DNL Marketo Measure] JS via [!DNL Google Tag Manager] {#how-to-add-marketo-measure-js-via-google-tag-manager}

1. Open GTM and add the [!DNL Marketo Measure] script on your website container. Be sure to select **[!UICONTROL Custom HTML tag]**.

1. Use the [!DNL Marketo Measure] script below and incorporate it in your container.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Click **[!UICONTROL Add a Firing Rule]** so you can tell Google to load our snippet on *All Pages*.

1. Go to the Container Draft Overview section on the left. Click the button to create a version of your container and publish the changes.
