---
unique-page-id: 18874773
description: A/B Testing Set Up and Reporting - Marketo Measure - Product Documentation
title: A/B Testing Set Up and Reporting
exl-id: 9a3f0731-5909-4fbf-a35a-9608ff561061
---
# A/B Testing Set Up and Reporting {#a-b-testing-set-up-and-reporting}

The Marketo Measure A/B Test integration allows you to track the revenue impact of your [Optimizely](https://optimizely.com/) and VWO site experiments. This article guides provides instructions on how to add Marketo Measure A/B Test sections to the Lead, Contact, Case, and Opportunity page layouts. We will also cover general reporting practices and recommendations for running Marketo Measure A/B report types.

## Set Up {#set-up}

Add the Marketo Measure A/B Test sections on Lead, Contact, Case, and Opportunity. Marketo Measure A/B Test integration allows you to track the revenue impact of your [Optimizely](https://optimizely.com/) and [VWO](https://vwo.com/) site experiments.

1. Verify you are using package Marketo Measure v3.9 or later. You can do this by going to Salesforce > Set Up > Installed packages.
1. Edit the Lead page layout and add the **Marketo Measure A/B Tests** Related List to the page.

   ![](assets/1.png)

1. Click the Wrench button. Remove the stock "Id" field from the list of Selected fields. Add **Experiment**, **Variation**, and **DateReported** fields. Change "Sort by" to **Date Reported**, and select **Descending** in the drop-down.

   ![](assets/2.png)

1. Under Buttons, uncheck **New**.

   ![](assets/3.png)

1. Contact your Marketo Measure rep or [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} to enable the feature.

## Reporting {#reporting}

Customers have access to a couple of Marketo Measure A/B report types that allow you to report on A/B Test in relation to Leads, Contacts, and Opportunities:

* Marketo Measure A/BTests
* Marketo Measure A/BTests with Contact
* Marketo Measure A/BTests with Lead
* Marketo Measure A/BTests with Opportunity

![](assets/4.png)

A/B report types are used to report on which Lead or Contact or Opportunity has been exposed to an A/B test. Additionally, these reports can show you the amount of revenue tied to an Opportunity that was exposed to an A/B test.

It's important to note that Optimizely/VWO is a content variation platform and not a marketing channel. Therefore, these Marketo Measure A/B report types are used differently than Buyer Touchpoint reports. Buyer touchpoint reports types are used to understand which marketing channel (e.g., paid advertising, web direct, social) drove a Lead or Contact to a specific page. However, Marketo Measure A/B report types cannot be used to report on how a variation influenced a Lead or Opportunity. Additionally, since an A/B test variation is not a channel, details about the variation will not appear on the Buyer touchpoint.

Here are some common fields we recommend using when reporting on A/B test to help increase clarity and insight:

* Lead converted
* Experiment
* Experiment ID
* Variation
* Variation ID
* Date Reported

## Salesforce Example Reports {#salesforce-example-reports}

**Marketo Measure A/B Test with Lead**

![](assets/5.png)

**Marketo Measure A/B Test with Opportunity**

![](assets/6.png)
