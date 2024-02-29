---
description: Best Practices for Segmentation - [!DNL Marketo Measure]
title: Best Practices for Segmentation
exl-id: 68281210-383b-4688-86e9-27fbdc1fabbb
feature: Segmentation
---
# Best Practices for Segmentation {#best-practices-for-segmentation}

## Overview {#overview}

[!DNL Marketo Measure] Segmentation allows you to define rules, which are essentially filters, based on your CRM fields to bucket them into individual segments. These Segments will then be available for use in your Discover dashboards as well as your [!DNL Salesforce] reporting.

Segmentation is crucial to the utilization of your [!DNL Marketo Measure] account, specially within you Discover boards. Because the [!DNL Marketo Measure] Discover boards are limited to a predetermined set of filters, segmentation gives you the ability to dissect your data in Discover much like you would in your [!DNL Salesforce] reporting.

When pushed to [!DNL Salesforce], Segment values are written to the "Segment" field and are within any Buyer touchpoint report type. This allows for uniform reporting across both platforms. The Segment can also be found on the 'Touchpoint Detail' of any touchpoint.

When pushed to [!UICONTROL Discover], Segments will appear as an available filter within the filter drop-down menu located on all boards.

## Best Practice {#best-practice}

Whether you're defining segmentation for the first time or just reviewing the segmentation that has been previously established, keep the following best practices in mind.

* Keep it simple!
* Align your segment name to the nomenclature of your organization, i.e., the category = filter name, segment = filter value
* Don't use formula fields in your rules
* Whenever possible, build the segmentation on both the Lead/Contact and Opportunity so that you can use it across the entire funnel
  * If you are a Marketo Measure Ultimate customer and have set your Default Dashboard Object as Contact, do not use the below two fields specific to Lead ([learn more here](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}). 
    * b2b.personStatus
    * b2b.isConverted
  * Not every Segment category will align throughout the entire funnel
    * A Segment category of 'Opportunity Type' won't relate to Leads for example, however a Segment related to 'Region' is likely a category that can be defined throughout the funnel
* Think about the ways you currently like to slice your data, whether it's in the CRM or a BI tool, consider building this as a Segment in [!DNL Marketo Measure] so you can have the same reporting in Discover

## Best Practice for Maintenance {#best-practice-for-maintenance}

Reviewing your segmentation at least twice a year will ensure that your segmentation is up to date. As a best practice, we recommend reviewing your rules within the '[!UICONTROL Segments]' tab of your [!DNL Marketo Measure] Account Settings, as well as pulling reports within [!DNL Salesforce] to review your Segments in action. These steps will help you and your team feel confident in your segmentation and subsequently your [!DNL Marketo Measure] reporting.

Other reasons to that might trigger a review your Segmentation include...

* Turnover in your marketing team
* Changes to fields that are used to define your segments
* Additions or changes to the Segments that have already been established

>[!MORELIKETHIS]
>
>[How to Set Up Custom Segmentation](/help/advanced-marketo-measure-features/segmentation/custom-segmentation.md)
