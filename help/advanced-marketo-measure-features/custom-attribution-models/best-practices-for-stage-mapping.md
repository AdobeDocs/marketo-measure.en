---
description: Best Practices for Stage Mapping - [!DNL Marketo Measure] - Product Documentation
title: Best Practices for Stage Mapping
exl-id: 1ed380a1-4a3a-4761-b70f-cdf2e290329d
feature: Tracking, Custom Models
---
# Best Practices for Stage Mapping {#best-practices-for-stage-mapping}

## Overview {#overview}

The Stage Mapping section of your [!DNL Marketo Measure] account outlines the stages that [!DNL Marketo Measure] automatically pulls from your CRM and any custom stages you have defined if using the Custom Attribution Model. The validity of your [!DNL Marketo Measure] data relies on these stages being ordered correctly so that [!DNL Marketo Measure] can accurately understand your funnel and the progression of records throughout said funnel.

In the Stage Mapping section of your [!DNL Marketo Measure] instance, you will see both active and inactive stages from your CRM. Order all of the stages to the best of your ability in alignment with how your funnel is today.

An additional feature that is managed in this section are Funnel Stages, which give you the ability to add stages to the funnel without applying attribution. Funnel Stages will be tracked as Touchpoints and will populate in the Touchpoint Positions field in your CRM. These Funnel Stages will also be represented within various journey boards in [!DNL Marketo Measure] Discover.

## Best Practices {#best-practices}

Whether you're evaluating your Stage Mapping for the first time or just reviewing your funnel order, it is important to keep the following best practices in mind.

* Order is everything!
   * Considering [!DNL Marketo Measure] pulls in both active and inactive stages from your CRM, confirm that any stage which could be used on a Lead/Contact or Opportunity are grouped together and ordered accordingly
* When defining a custom stage, make sure field history tracking is enabled for any field(s) used to define the stage
* Do not use a formula field to define a custom stage
   * A Boolean field is the best practice recommendation
* Note that the Lead or Contact stage section is divided into Lost, Open, and Converted; validate that the stages are in their appropriate stage section
   * Having a stage in the incorrect stage section can result in highly incorrect [!DNL Marketo Measure] data
* Note that the Opportunity stage section is divided into Lost, Open, and Won; validate that the stages are in their appropriate stage section
   * Having a stage in the incorrect stage section can result in highly incorrect [!DNL Marketo Measure] revenue or pipeline revenue data
* Avoid using duplicate stage names (our system will detect them and automatically remove one).

## Best Practices for Maintenance {#best-practices-for-maintenance}

Reviewing your Stage Mapping once a year will ensure that your Opportunity data in [!DNL Marketo Measure] is accurate and up to date.

Other reasons that might trigger a review of your Stage Mapping include...

* Turnover in your marketing team
* Any changes to your CRM stages
* Updates to your organization's funnel
* Seeing incorrect Revenue data in your [!DNL Marketo Measure] reporting

>[!MORELIKETHIS]
>
>[The Difference Between Funnel Stages and Custom Model Stages](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md#the-difference-between-funnel-stages-and-custom-model-stages)
