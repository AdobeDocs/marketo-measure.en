---
unique-page-id: 18874519
description: Adding [!DNL Marketo Measure] Script to Lightbox Forms - [!DNL Marketo Measure]
title: Adding [!DNL Marketo Measure] Script to Lightbox Forms
exl-id: fa9ce480-fc4f-4abd-8555-dbb74849747e
feature: Tracking
---
# Adding [!DNL Marketo Measure] Script to Lightbox Forms {#adding-marketo-measure-script-to-lightbox-forms}

Learn how to properly add the [!DNL Marketo Measure] JavaScript to a form within a lightbox.

A lightbox opens a form in front of your content when the visitor performs a specific action (that is, clicking a particular portion of the page, spending a certain time on the page, and so on). Typically we ask to have the [!DNL Marketo Measure] JavaScript placed in the head of the landing page, but for forms within a lightbox there's one extra step needed.

Since a form within a lightbox is basically a form within an iFrame, the script is placed within that iFrame.

First, locate the iFrame the [!UICONTROL lightbox] form lives in.

![](assets/1.png)

Next, place the [!DNL Marketo Measure] JavaScript within the iFrame.

![](assets/2.png)

Finally, when the JavaScript is added, validate form submissions are being tracked by following these directions:

1. Copy the URL of the landing page containing the [!UICONTROL lightbox] form.
1. Open an Incognito browser and paste the URL.
1. Submit the form using a unique email address.
1. Confirm that the test was tracked by checking your CRM for the unique email address used, ensure that Touchpoint data is populating.
