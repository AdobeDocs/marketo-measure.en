---
unique-page-id: 18874797
description: Adding Marketo Measure Script via Google Tag Manager - Marketo Measure - Product Documentation
title: Adding Marketo Measure Script via Google Tag Manager
exl-id: 539efb10-35cb-4146-8eea-728c3948a11e
---
# Adding Marketo Measure Script via Google Tag Manager {#adding-marketo-measure-script-via-google-tag-manager}

When installing the Marketo Measure javascript, we strongly recommend [hard-coding the script](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script.md) directly into your site. However, if that isn't possible, you can also use Google Tag Manager (GTM) to load the Marketo Measure JS. Please note that Marketo Measure JS loaded through GTM is susceptible to latency. Latency causes a delay in script load times which can result in missing around 3-5% of all form submissions.

If you decide to add our script via GTM, please set the Marketo Measure script to the highest priority in your firing order and ensure there are no synchronous scripts in front of the Marketo Measure tag in order to reduce any effects from GTM latency.

>[!NOTE]
>
>Please use this [support article by Google](https://support.google.com/tagmanager/answer/2772421?hl=en) to learn more.

## How to Add Marketo Measure JS via Google Tag Manager {#how-to-add-marketo-measure-js-via-google-tag-manager}

1. Open GTM and add the Marketo Measure script on your website container. Be sure to select **Custom HTML tag**.
1. Use the Marketo Measure script below and incorporate it in your container.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Click `+Add` a Firing Rule so that you can tell Google to load our snippet on *All Pages.*

1. Go to the Container Draft Overview section on the left. Click the button to create a new version of your container and publish the changes.
