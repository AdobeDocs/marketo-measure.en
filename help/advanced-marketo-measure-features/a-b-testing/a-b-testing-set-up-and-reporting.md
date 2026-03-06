---
unique-page-id: 18874773
description: A/B Testing Set Up and Reporting - [!DNL Marketo Measure]
title: A/B Testing Set Up and Reporting
exl-id: 9a3f0731-5909-4fbf-a35a-9608ff561061
feature: A/B Testing
---
# A/B Testing Set Up and Reporting {#a-b-testing-set-up-and-reporting}

The [!DNL Marketo Measure] A/B Test integration allows you to track the revenue impact of your [Optimizely](https://www.optimizely.com/){target="_blank"} and VWO site experiments. This article provides instructions on how to add [!DNL Marketo Measure] A/B Test sections to the Lead, [!UICONTROL Contact], Case, and [!UICONTROL Opportunity] page layouts. Also covered is general reporting practices and recommendations for running [!DNL Marketo Measure] A/B report types.

## Set Up {#set-up}

Add the [!DNL Marketo Measure] A/B Test sections on Lead, Contact, Case, and Opportunity. [!DNL Marketo Measure] A/B Test integration allows you to track the revenue impact of your [Optimizely](https://www.optimizely.com/){target="_blank"} and [VWO](https://vwo.com/){target="_blank"} site experiments.

1. Verify you are using package [!DNL Marketo Measure] v3.9 or later. You can do this by going to [!UICONTROL Salesforce] >[!UICONTROL Set Up] > [!UICONTROL Installed packages].
1. Edit the Lead page layout and add the **[!DNL Marketo Measure] A/B Tests** Related List to the page.

   ![](assets/1.png)

1. Click the [!UICONTROL Wrench] button. Remove the stock "Id" field from the list of Selected fields. Add **[!UICONTROL Experiment]**, **[!UICONTROL Variation]**, and **[!UICONTROL DateReported]** fields. Change "[!UICONTROL Sort by]" to **[!UICONTROL Date Reported]**, and select **[!UICONTROL Descending]** in the drop-down.

   ![](assets/2.png)

1. Under [!UICONTROL Buttons], uncheck **[!UICONTROL New]**.

   ![](assets/3.png)

1. Contact your [!DNL Marketo Measure] rep or [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} to enable the feature.

## Reporting {#reporting}

Customers have access to a couple of [!DNL Marketo Measure] A/B report types that allow you to report on A/B Test in relation to Leads, Contacts, and Opportunities:

* [!DNL Marketo Measure] A/BTests
* [!DNL Marketo Measure] A/BTests with Contact
* [!DNL Marketo Measure] A/BTests with Lead
* [!DNL Marketo Measure] A/BTests with Opportunity

![](assets/4.png)

A/B report types are used to report on which Lead or Contact or Opportunity has been exposed to an A/B test. These reports also show you the amount of revenue tied to an Opportunity that was exposed to an A/B test.

It's important to note that Optimizely/VWO is a content variation platform and not a marketing channel. Therefore, these [!DNL Marketo Measure] A/B report types are used differently than Buyer Touchpoint reports. Buyer touchpoint reports types are used to understand which marketing channel (paid advertising, web direct, social) drove a Lead or Contact to a specific page. However, [!DNL Marketo Measure] A/B report types cannot be used to report on how a variation influenced a Lead or Opportunity. Since an A/B test variation is not a channel, details about the variation do not appear on the Buyer touchpoint.

Here are some recommended fields to use when reporting on an A/B test to help increase clarity and insight:

* Lead converted
* Experiment
* Experiment ID
* Variation
* Variation ID
* Date Reported

## [!DNL Salesforce] Example Reports {#salesforce-example-reports}

**[!DNL Marketo Measure] A/B Test with Lead**

![](assets/5.png)

**[!DNL Marketo Measure] A/B Test with Opportunity**

![](assets/6.png)
