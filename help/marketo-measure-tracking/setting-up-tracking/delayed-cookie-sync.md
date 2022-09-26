---
unique-page-id: 30082018
description: Delayed Cookie Sync - [!DNL Marketo Measure] - Product Documentation
title: Delayed Cookie Sync
exl-id: 394053ed-5642-48e4-b83c-c483a58ebbd7
---
# Delayed Cookie Sync {#delayed-cookie-sync}

This modification to the default [!DNL Marketo Measure] Javascript serves to provide [!DNL bizible.js] API support, so you can configure the JS to temporarily store visitors' user activities, but not send the information to the [!DNL Marketo Measure] server until the user gives consent to do so.

## How-To {#how-to}

Replace the default [!DNL bizible.js] script tag with the following:

`<script id="bizible-settings" type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" data-consent-button-id="ConsentButtonId"></script>`

The data-consent-button-id="ConsentButtonId" attribute tells [!DNL bizible.js] to not send send analytical data until an HTML element with that id is clicked.

Alternatively, customers can set the [!UICONTROL data-consent-button-id] to be something non-existent (e.g., "foobar") and use the following API to tell [!DNL bizible.js] that the user has consented:

`window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`
`Bizible.Push("Consent", true });`

>[!NOTE]
>
>User consent is saved into the cookie, meaning that once the user has consented once there is no need to perform this call on any subsequent pages.

## Limitation {#limitation}

Because [!DNL bizible.js] temporarily saves unsent web activities in customers' first party cookies, and the size of first party cookies are limited, only three unsent requests can be saved at any given time.

If there are already three pending requests, any subsequent activities will be ignored; this is to preserve the first pageview, which contains valuable referrer information.
