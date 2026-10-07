---
unique-page-id: 18874753
description: Adding [!DNL Marketo Measure] to Act-On Forms - [!DNL Marketo Measure]
title: Adding [!DNL Marketo Measure] to Act-On Forms
exl-id: 3d246e6a-ad3b-4683-b2b7-ab3f0f4c5ab2
feature: Tracking
TQID: 'https://experienceleague.adobe.com/BUdHiCxfaG7a8Tays-Oqg9ZJQjSZJMM4-ChPHuF0RCg'
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: dcbeff6e-0253-5a4b-9ac2-1b67cc4a6286
    internal-label: Tracking
---
# Adding [!DNL Marketo Measure] to Act-On Forms {#adding-marketo-measure-to-act-on-forms}

## Directions {#directions}

1. In the form you are editing, select the **[!UICONTROL Settings]** option in the right hand corner.
1. Look for an area labeled [!UICONTROL "External Web Analytics."] This will be where you drop the [!DNL Marketo Measure] tracking code snippet.

## [!DNL Marketo Measure] JavaScript {#marketo-measure-javascript}

`script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

>[!NOTE]
>
>There may already be other tracking code snippets in this area, such as a [!DNL Google Analytics] code. Be sure to separate them using a semicolon `;` and a single space, like so:
>
>`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>**; **<script async="true" type="someothercode" src="someotherfile.js" ></script>`
