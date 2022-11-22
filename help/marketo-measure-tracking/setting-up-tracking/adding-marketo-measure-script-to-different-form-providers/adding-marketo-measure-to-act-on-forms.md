---
unique-page-id: 18874753
description: Adding [!DNL Marketo Measure] to Act-On Forms - [!DNL Marketo Measure] - Product Documentation
title: Adding [!DNL Marketo Measure] to Act-On Forms
exl-id: 3d246e6a-ad3b-4683-b2b7-ab3f0f4c5ab2
---
# Adding [!DNL Marketo Measure] to Act-On Forms {#adding-marketo-measure-to-act-on-forms}

## Directions {#directions}

1. In the form you're editing, select the **[!UICONTROL Settings]** option in the right hand corner.
1. Look for an area labeled [!UICONTROL "External Web Analytics."] This will be where you drop the [!DNL Marketo Measure] tracking code snippet.

## [!DNL Marketo Measure] JavaScript {#marketo-measure-javascript}

`script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

>[!NOTE]
>
>There may already be other tracking code snippets in this area, such as a [!DNL Google Analytics] code. Be sure to separate them using a semicolon `;` and a single space, like so:
>
>`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>**; **<script async="true" type="someothercode" src="someotherfile.js" ></script>`
