---
description: Marketo Measure Integrations with Adobe Launch - Marketo Measure - Product Documentation
title: Marketo Measure Integrations with Adobe Launch
hide: yes
hidefromtoc: yes
---
# Marketo Measure Integrations with Adobe Launch {#marketo-measure-integrations-with-adobe-launch}

The Adobe Launch extension is designed for existing Marketo Measure users that already leverage Adobe Launch on their website. The extension serves as a tag management solution that you can use to configure and dynamically load scripts on your pages based on certain events and conditions.

When installed and configured in Adobe Launch, the Marketo Measure extension will load bizible.js script on the pages where Adobe Launch script is present. This allows marketers to add bizible.js through the Adobe Launch configuration, as opposed to explicitly modifying the web page to add the bizible.js script tag.

## Configure the Adobe Launch Extension {#configure-the-adobe-launch-extension}

>[!PREREQUISITES]
>
>Check out the following links to learn more about Adobe Launch and its extensions.
>
>* [Marketo Measure Extension](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email/bizible.html?lang=en#catalog){target="_blank"}
>* link
>* link

Adobe Launch Overview: https://experienceleague.adobe.com/docs/launch-learn/implementing-in-websites-with-launch/index.html?lang=en#prerequisites

Adobe Launch Extension overview: https://experienceleague.adobe.com/docs/launch/using/extension-dev/overview.html?lang=en#extension-configuration

1. Create a property following the steps [in this article](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html?lang=en#go-to-the-data-collection-interface){target="_blank"}. 

1. Click on the property you just created.

   ![](assets/marketo-measure-integrations-with-adobe-launch-1.png) 
 
1. Click **Extensions**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-2.png)
 
1. Click the Catalog tab and search for "Bizible."

   ![](assets/marketo-measure-integrations-with-adobe-launch-3.png)

1. In the Bizible Analytics tile, click **Install**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-4.png)

1. In the Bizible AccountId field, type in the URL of your website.

   ![](assets/marketo-measure-integrations-with-adobe-launch-5.png)

   >[!NOTE]
   >
   >This field is not the "Account ID" in the Business_Prod.Business table. All web activities from the given URL will be mapped to the Marketo Measure tenant.

1. Click **Save**.

   PIC

1. Click **Rules**, then select **Create New Rule**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-7.png)

1. Add an Event to trigger a rule. Selecting "Library Loaded (Page Top)" will ensure the rule is triggered once the Launch library is loaded. 

   PIC

1. Add an Action by selecting "Bizible Analytics" under Extensions, then "Initialize" under Action Type. This will load bizible.js every time Launch is loaded. 

   PIC

1. Click **Save**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-10.png)
