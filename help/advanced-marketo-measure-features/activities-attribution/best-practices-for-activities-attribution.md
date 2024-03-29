---
description: Best Practices for Activities Attribution - [!DNL Marketo Measure]
title: Best Practices for Activities Attribution
exl-id: 66fb9f47-3912-40a6-b112-3efca789f321
feature: Attribution
---
# Best Practices for Activities Attribution {#best-practices-for-activities-attribution}

## Overview {#overview}

The [!DNL Marketo Measure] Activities Attribution feature allows customers to create touchpoints from Activity records in your CRM. This method of creating touchpoints is flexible. It allows you to create rules based on 'Task' or 'Event' fields to inform [!DNL Marketo Measure] which Activity records it should produce touchpoints from, and therefore receive attribution credit.

The most common use case for this feature is to craft rules which incorporate Sales interactions into your Buyer touchpoint data. Activities Attribution makes it possible for you to align your Sales and Marketing data into one journey.

For many [!DNL Salesforce] instances, the Activity object can house various record types, so it is important that your Activity rules are specific and tailored to the records you are trying to translate into touchpoints. The following best practices help to ensure that you are creating meaningful and valuable touchpoints via your Activities attribution.

## Best Practice {#best-practice}

Whether you are defining Activity rules for the first time or just reviewing Activity rules that have been previously set up, keep the following best practices in mind.

* Start simple
   * Identify a few key types of Activities that you want to incorporate into your [!DNL Marketo Measure] data, then add more types as you become comfortable with how these touchpoints are being attributed
   * As mentioned, the primary use case of this feature is to create touchpoints that track the efficacy of your Sales Development team, specifically Outbound Phone Calls and Outbound Emails

>[!NOTE]
>
>It is **NOT** recommended to track Sales Activities that happen after the Opportunity is created, as tracking a Sales Executives process does not offer much insight. The goal is track Sales influence alongside Marketing influence, primarily in the development of a new Opportunity/pipeline generation

* Don't use formula fields to define your rules
* Create rules that are specific and precise
   * The threshold for the creation of an Activity touchpoint should be the same (or similar) to a form fill or campaign membership: Replies to an Outbound Email or Completed Phone Conversations
* Always validate new rules in [!DNL Salesforce] before saving and processing
   * Replicating the Activity rules in a "Tasks & Events" report type gives you a clear understanding of exactly how many touchpoints are from the rule
* Work with your Sales Opp team
   * Bringing in the team who works closest with your Activity records or sales enablement tool will ensure you are using the correct fields to define your rules

## Best Practice for Maintenance {#best-practice-for-maintenance}

Reviewing your Activity Attribution rules at least twice a year ensures that your Activity touchpoints are accurate and up to date. You want to make sure these rules are not creating unwanted touchpoints that are diluting your Buyer Attribution data. A review of how your rules are defined will help you and your team feel confident in your Activities Attribution and its role in your [!DNL Marketo Measure] data.

Other reasons to that might trigger a review your Activity rules include...

* Turnover in your marketing team
* Changes to fields that are used to define your activity records
* Changes or updates to your sales enablement tools

>[!MORELIKETHIS]
>
>* [Activities Attribution](/help/advanced-marketo-measure-features/activities-attribution/salesforce-activities-attribution.md)
>* [Sales Activities Attribution FAQ](/help/advanced-marketo-measure-features/activities-attribution/activities-attribution-faq.md)
