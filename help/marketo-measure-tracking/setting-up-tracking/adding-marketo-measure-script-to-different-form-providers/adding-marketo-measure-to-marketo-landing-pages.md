---
unique-page-id: 18874755
description: Adding [!DNL Marketo Measure] to [!DNL Marketo] Landing Pages - [!DNL Marketo Measure] - Product Documentation
title: Adding [!DNL Marketo Measure] to Marketo Landing Pages
exl-id: 3771d4d2-8723-452a-b23d-cea3b11ab9ee
---
# Adding [!DNL Marketo Measure] to Marketo Landing Pages {#adding-marketo-measure-to-marketo-landing-pages}

Learn how to add tracking to [!DNL Marketo Engage] Landing Pages as they require additional handling. [!DNL Marketo Measure] JavaScript needs to be in place on both the Landing Page and the [!DNL Marketo Engage] form itself. To do this you will need to load the [!DNL Marketo Measure] JavaScript into [!DNL Marketo Engage] as explained in the following directions.

>[!NOTE]
>
>If you are deploying the JavaScript through a tag management provider such as [!DNL Google Tag Manager], you do not need to manually add [!DNL Marketo Measure] JS to [!DNL Marketo Engage].

## How to add [!DNL Marketo Measure] Script to [!DNL Marketo Engage] Landing Pages {#how-to-add-marketo-measure-script-to-marketo-engage-landing-pages}

1. Log in to your [!DNL Marketo Engage] account.
1. Select your landing page and click **[!UICONTROL Edit Draft]**.
1. Drag in the HTML element.
1. Enter the [!DNL Marketo Measure] JavaScript into the [!UICONTROL head] section:

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Example in screenshot below

1. Click **[!UICONTROL Save]**.

   ![](assets/adding-bizible-to-marketo-landing-pages-1.png)

## Additional Notes {#additional-notes}

* You might already have other tracking code snippets in place, such as a [!DNL Google Analytics] code. There is no problem with this, just be sure to separate them with a semicolon `;` and a single space. An example of what this would look like is:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="someothercode" src="someotherfile.js" ></script>`

* It's likely that you have multiple Landing Page templates in use, be sure to add the code to all templates that have forms on them.

* Sometimes when you edit the template for landing pages, you need to re-approve the pages the landing page is used by. This article explains [how to mass approve](https://experienceleague.adobe.com/docs/marketo/using/product-docs/demand-generation/landing-pages/landing-page-actions/approve-multiple-landing-pages-at-once.html){target="_blank"}.
