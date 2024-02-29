---
unique-page-id: 18874749
description: Adding [!DNL Marketo Measure] Script to [!DNL Uberflip] Forms - [!DNL Marketo Measure]
title: Adding [!DNL Marketo Measure] Script to [!DNL Uberflip] Forms
exl-id: fb123e15-523d-4931-b4c1-705fe49be3d0
feature: Tracking
---
# Adding [!DNL Marketo Measure] Script to [!DNL Uberflip] Forms {#adding-marketo-measure-script-to-uberflip-forms}

If you are currently using [!DNL Uberflip] to manage your content, it's important that you take these necessary steps to make sure that [!DNL Marketo Measure] is tracking those form submissions. Your Success Manager at [!DNL Uberflip] should also be able to assist you with this.

1. Add this script to [!DNL Uberflip]'s [!UICONTROL Custom Code>HTML] section.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Ensure this [!DNL Marketo Measure] preamble code fires on both page load and AJAX page change. Do this within the [!UICONTROL Custom Code>JS] section

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   you will add this preamble to both the [!DNL Hubs.onLoad] and the [!DNL Hubs.onPageChange] AJAX Javascript event hooks per below. (Note: You may have other codes in these event hooks as well. Just make sure you include the preamble too.)

   `Hubs.onLoad = function () {`

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   `}`

   `Hubs.onPageChange = function () {`

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   `}`

1. Create and define a function that will push data to Bizible upon a Form CTA submit. This goes into the [!UICONTROL Custom Code>Javascript] section. (Note: this function only requires the ctaData parameter Uberflip provides, but you can include the other parameters ctaId and ctaName in case the user wants to customize their code to pass this data as well).

   `function bizibleFormCode(ctaId, ctaData, ctaName) {`
   `var email = ctaData["email"];`
   `if(email){`
   `Bizible.Push('User', {`
   `eMail: email, // required`
   `}); }`

   `}`

1. When a Form CTA is submitted, make sure your [!DNL Marketo Measure] function is executed per below. This is done within the [!UICONTROL Custom Code>JS] section. (Note: You might have other code within the Hubs.onCtaFormSubmitSuccess javascript event hook, just make sure you include this function call as well).

   `Hubs.onCtaFormSubmitSuccess = function (ctaId, ctaData, ctaName) {`
   `bizibleFormCode(ctaId, ctaData, ctaName);`\
   `}`
