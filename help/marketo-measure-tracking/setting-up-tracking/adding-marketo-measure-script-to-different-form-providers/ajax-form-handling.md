---
unique-page-id: 18874745
description: AJAX Form Handling - [!DNL Marketo Measure]
title: AJAX Form Handling
exl-id: 042e42ff-d8d9-4380-b878-aba4934bc4a0
feature: Tracking
---
# AJAX Form Handling {#ajax-form-handling}

To manually report customer conversions to [!DNL Marketo Measure], there is a simple API that you can use. Both of these JavaScript APIs are automatically available on your site, if you have tracking code on it. No need to do anything special to access them.

## Scenario 1 - HTML form with an AJAX submit {#scenario-html-form-with-an-ajax-submit}

When using forms containing AJAX (or another mechanism) to submit conversion dates from the client to our servers, [!DNL Marketo Measure] may not be aware of the customer conversion through any of the standard paths that we monitor. In this scenario, we can use a simple API (provided below).

If you handle your own form submissions, you can explicitly call [!DNL Marketo Measure] from the JavaScript. [!DNL Marketo Measure] collects all the relevant information from the form and post it asynchronously to our servers.

**Below is a code sample using JQuery (assuming the ID on the form is "formId"):**

```jquery
///////////////////////////////////////////////////////////////////////  
// Preamble for all API usage.  
window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };  
  
// Give Marketo Measure the JQuery Selector for the form and we'll collect the data automatically.  
Bizible.Push('Form',$('#*formId*'));
```

**Below is a code sample not using JQuery (assuming the ID on the form is "formId"):**

```jquery
///////////////////////////////////////////////////////////////////////  
// Preamble for all API usage.  
window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };  
  
// Give Marketo Measure the Form ID and we'll collect the data automatically.
Bizible.Push('Form','MyFormID');
```

## Scenario 2 - Lead information collected in a non-HTML form {#scenario-lead-information-collected-in-a-non-html-form}

If information from a converted lead is collected using JavaScript or simple text fields with no html form, this solution works for you. Shared below is the API to use in this scenario:

```jquery
///////////////////////////////////////////////////////////////////////  
// Preamble for all API usage.  
window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };  
  
// If your site is using Ajax, or you are running a secure site, it is best to send us the data directly.  
Bizible.Push('User', {
eMail: 'user@gmail.com' // required  
});  
```

In this code, the [!UICONTROL email] field is required. [!DNL Marketo Measure] posts this data asynchronously to our servers.

## Scenario 3 - Report user information from the thank-you page {#scenario-report-user-information-from-the-thank-you-page}

Sometimes, it is more convenient to report the lead information to [!DNL Marketo Measure] from the thank-you page, after the form is submitted. The simplest way to report this information is to add a hidden element to the page that holds information from the form submission, and [!DNL Bizible.js] will read this information when the "Thank you" page has loaded.

**For example:**

```html
<div id="bizible.reportUser" style="display:none"  
data-email="user@gmail.com">  
```

It doesn't matter whether the hidden element is a div, script, or any other tag type. [!DNL Marketo Measure] looks for the id="bizible.reportUser" to read the information.
