---
unique-page-id: 18874755
description: Adding Marketo Measure to Marketo Landing Pages - Marketo Measure - Product Documentation
title: Adding Marketo Measure to Marketo Landing Pages
exl-id: 3771d4d2-8723-452a-b23d-cea3b11ab9ee
---
# Adding Marketo Measure to Marketo Landing Pages {#adding-marketo-measure-to-marketo-landing-pages}

Learn how to add tracking to Marketo Landing Pages as they require additional handling. Marketo Measure JavaScript needs to be in place on both the Landing Page and the Marketo form itself. To do this you will need to load the Marketo Measure JavaScript into Marketo as explained in the following directions.

>[!NOTE]
>
>If you are deploying the JavaScript through a tag management provider such as Google Tag Manager, you do not need to manually add Marketo Measure JS to Marketo.

## How to add Marketo Measure Script to Marketo Landing Pages {#how-to-add-marketo-measure-script-to-marketo-landing-pages}

1. Log-in to your Marketo account.
1. Select your landing page and click **Edit Draft**.
1. Drag in the HTML element.
1. Enter the Marketo Measure JavaScript into the head section:

    `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Example in screenshot below

1. Click **Save**.

   ![](assets/adding-bizible-to-marketo-landing-pages-1.png)

## Additional Notes {#additional-notes}

* You might already have other tracking code snippets in place, such as a Google Analytics code. There is no problem with this, just be sure to separate them with a semicolon `;` and a single space. An example of what this would look like is:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="someothercode" src="someotherfile.js" ></script>`

* It is likely that you have multiple Landing Page templates in use, be sure to add the code to all templates that have forms on them.

* Sometimes when you edit the template for landing pages, you need to re-approve the pages the landing page is used by. This article explains [how to mass approve](https://docs.marketo.com/display/DOCS/Approve+Multiple+Landing+Pages+at+Once).
