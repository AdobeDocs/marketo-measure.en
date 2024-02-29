---
description: Best Practices for Utilizing a Custom Revenue Amount - [!DNL Marketo Measure]
title: Best Practices for Utilizing a Custom Revenue Amount
exl-id: 553bd75a-512a-4733-a24b-8112eb420afc
feature: Custom Revenue Amount
---
# Best Practices for Utilizing a Custom Revenue Amount {#best-practices-for-utilizing-a-custom-revenue-amount}

## Overview {#overview}

The core functionality of [!DNL Marketo Measure] is the ability to assign revenue credit to marketing touchpoints throughout the buyer's journey. The key to accurate revenue attribution is the ability for [!DNL Marketo Measure] to reference the correct revenue amount on an Opportunity, which in turn, is distributed across the marketing touchpoints via the various attribution models.

Unless otherwise specified during implementation, your [!DNL Marketo Measure] instance will be set to reference the standard Opportunity Amount (SFDC Default) for revenue attribution. However, for many [!DNL Marketo Measure] accounts, this field does not reflect the accurate revenue amount for Opportunities. In these instances, [!DNL Marketo Measure] offers the ability to set up a Custom Revenue Amount for [!DNL Marketo Measure] to reference and distribute across the Attribution Touchpoints (BATs).

## Best Practice {#best-practice}

When setting up a Custom Revenue Amount, keep the following best practices in mind to ensure your [!DNL Marketo Measure] attribution data is accurate and consistent!

Things to keep in mind:

* Select the revenue field that is accurate and utilized for all Opportunities
   * ARR or Total Contract Value us recommended
* Do not use a formula field
* If you're using a Custom Revenue Amount for currency conversions, the [!UICONTROL Marketo Measure Multiple Currencies] functionality is the preferred method instead.
   * The [!DNL Marketo Measure] Multiple Currencies functionality references the conversion rates established in [!DNL Salesforce] to best ensure alignment between currency conversions. This allows you to continue utilizing the standard 'Amount' (SFDC Default), or any other custom Amount field that relates to the [!DNL Salesforce] conversion rates.
* If you update the Amount field you'd like [!DNL Marketo Measure] to reference, use Data Loader to update past Opportunities to ensure your revenue data is consistent and the proper field is populate via the workflow

## Best Practice for Maintenance {#best-practice-for-maintenance}

Reviewing your revenue amount setup yearly will ensure that your attribution data is accurate and aligned with the rest of your organization's revenue reporting.

If you're utilizing a Custom Revenue Amount, check your revenue setup as follows.

* In your [!DNL Marketo Measure] account, go to the '[!UICONTROL Opportunities]' section under CRM
* Identify the [!UICONTROL Custom Opportunity Amount] Field, here your [!UICONTROL custom revenue amount API] field should be listed
* Confirm that this is still the correct field
* Also have your [!DNL Salesforce] Admin confirm that the Custom Revenue Amount workflow in [!DNL Salesforce] is still running

Aside from a yearly review, certain organizational changes may signal the need to review your revenue amount setup...

* Turnover in your marketing team
* Changes to the Custom Revenue field
* Organization changes in how revenue is reported

>[!MORELIKETHIS]
>
>* [Using a Custom Revenue Amount Field](/help/advanced-marketo-measure-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md)
>* [Using Data Loader to Update Custom Amount Field](/help/advanced-marketo-measure-features/custom-revenue-amount/using-data-loader-to-update-marketo-measure-custom-amount-field.md)
>* [Overview of Multi-Currency](/help/advanced-marketo-measure-features/multi-currency/overview.md)
>* [Multi-Currency Settings](/help/advanced-marketo-measure-features/multi-currency/settings.md)
