---
unique-page-id: 35586069
description: Ensuring Consent for GDPR in Marketo Measure Js - Marketo Measure - Product Documentation
title: Ensuring Consent for GDPR in Marketo Measure Js
exl-id: 9afc5e4d-cf97-4c49-b9ee-ee1cc99c1f90
feature: Tracking
---
# Ensuring Consent for GDPR in Marketo Measure Js {#ensuring-consent-for-gdpr-in-marketo-measure-js}

The General Data Protection Regulation (GDPR) is a European Union legislation that went into effect on May 25, 2018.

## Overview {#overview}

The aim of the GDPR is to strengthen the rights of data subjects within the European Union (EU) and European Economic Area (EEA) regarding how their personal data is used and protected. "Personal data" refers to any information that relates to an identified or identifiable natural person. The GDPR applies to any organization inside or outside the EU who is marketing goods or services to, and/or tracking the behaviors of, data subjects within the EU and EEA. If you do business with data subjects in Europe that involves the processing of their personal data, this legislation applies to you. Penalties for non-compliance are significant, with large fines for those in breach of the regulation; the maximum fine for a single breach is &euro;20 million or 4% of annual worldwide turnover, whichever is greater.

By default, [!DNL bizible.js] collects users' analytics data unless it's configured to wait for consent. When [!DNL bizible.js] is configured to wait for user consent, it will not create any cookies or send any analytics data until after consent is reached.

## How to Wait for Consent {#how-to-wait-for-consent}

There are two ways to set [!DNL bizible.js] to wait for consent.

Option 1 - Replace the default [!DNL bizible.js] script tag with:

`<script id="bizible-settings" type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" data-consent-button-id="ConsentButtonId"></script>`

**If you use [!DNL Google Tag Manager] to install script**, keep in mind GTM removes data- attributes, so use the following script instead:

`<span id="bizible-settings" data-consent-button-id="ConsentButtonId"></span>`
`<script type="text/javascript" src=https://cdn.bizible.com/scripts/bizible.js async=""></script>`

>[!NOTE]
>
>In this case, [!DNL bizible.js] attaches an on-click event to HTML element with id "ConsentButtonId".

When this HTML element is clicked, [!DNL bizible.js] creates a cookie to remember that user's consent has been received and start collecting analytics data as usual.

**-or-**

Option 2 - Replace the default [!DNL bizible.js] script tag with:

`<script id="bizible-settings" type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" data-requires-user-consent="true"></script>`

This tells [!DNL bizible.js] to not track until consent is reached, which can be done with the following JS API:

*window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) { this._queue.push({ type: o, data: p }); } };*

*Bizible. Push('Consent', true);*

**If you use [!DNL Google Tag Manager] to install script**, keep in mind GTM removes data- attributes, so use the following script instead:

`<span id="bizible-settings" data-requires-user-consent="true"></span>`
`<script type="text/javascript" src=https://cdn.bizible.com/scripts/bizible.js async=""></script>`

>[!NOTE]
>
>bizible.js will create a cookie to remember that user's consent has been received and start collecting analytics data as usual only after the JS API is called.

In contrast, customers can also use this API to withdraw user's consent:

`window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) { this._queue.push({ type: o, data: p }); } };`

`Bizible.Push('Consent', false);`

When this code executes, it deletes all cookies that [!DNL bizible.js] previously created and resumes the collection of analytics data only if the user reconsents.
