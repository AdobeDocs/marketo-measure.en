---
unique-page-id: 18874783
description: Excluding [!DNL Marketo Measure] from Specific Forms - [!DNL Marketo Measure]
title: Excluding [!DNL Marketo Measure] from Specific Forms
exl-id: ce39a3b2-2ac6-4385-b6d1-3c36b51c03fa
feature: Tracking
TQID: 'https://experienceleague.adobe.com/RtGjsV86NEJPvUpFGnthwVGsQVpX0LqMQdC2xBSFwZc'
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: dcbeff6e-0253-5a4b-9ac2-1b67cc4a6286
    internal-label: Tracking
---
# Excluding [!DNL Marketo Measure] from Specific Forms {#excluding-marketo-measure-from-specific-forms}

By default, [!DNL Marketo Measure] attaches to all forms on your site. However, not all form submissions should necessarily be tracked or included in an attribution model. This is because not all form fills are considered to be "good." An example of this is an unsubscribe page/form. Furthermore, login forms are typically not tracked as it would dilute the attribution model.

## How to Add [!DNL Marketo Measure]-exclude Code:  {#how-to-add-marketo-measure-exclude-code}

To prevent [!DNL Marketo Measure] from tracking specific forms, simply add "[!DNL Bizible-Exclude]" as a 'class' on your form. The code is as follows:

`<form id="myForm" action="/Home/TestPage" method="POST" class="Bizible-Exclude">`
