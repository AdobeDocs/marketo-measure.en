---
description: Best Practices for Custom Model - [!DNL Marketo Measure] - Product Documentation
title: Best Practices for Custom Model
exl-id: 7c19bb6a-30fc-4cbd-a58e-f20751102afe
feature: Custom Models
---
# Best Practices for Custom Model {#best-practices-for-custom-model}

## Overview {#overview}

In addition to the [!DNL Marketo Measure] out of the box Attribution Models, Tier 2 customers and above have access to a Custom Attribution Model.

The [!DNL Marketo Measure] Custom Attribution model allows users to choose which milestone touchpoint positions and/or custom stages to include in the model. In addition, users can control the percentage of credit attributed to each stage within the model (users can define up to 6 additional custom stages), or they can use the attribution percentage values suggested by the [!DNL Marketo Measure] Machine Learning Model.

There are two key aspects of your Custom Attribution Model:

**Custom Stages** allow users to define their funnel as it relates to their business and processes. Custom Stages should represent "milestones" throughout the buyer's journey much like the [!DNL Marketo Measure] milestones (First Touch, Lead Creation Touch, Opportunity Creation Touch, and Closed Won Touch) do within the stock attribution models. It is crucial that your custom stages are properly defined and mapped within your account to ensure that [!DNL Marketo Measure] is properly tracking stage transitions. This is to identify which touchpoints should be associated with each stage and attribute credit appropriately. Custom Stage mapping is essentially an extension of standard 'Stage Mapping' and should follow the same practices.

>[!NOTE]
>
>Reference the Stage Mapping Best Practice resource for more details

**Custom Attribution Modeling** is defined once you select your Custom Stages funnel. Users can then control how much attribution credit should be assigned to each custom stage as well as the [!DNL Marketo Measure] milestone stages. Users can assign credit to each stage as they see fit, or reference the [!DNL Marketo Measure] Machine Learning Model which acts as a "suggestive model" based on historical data.

It is crucial that these two aspects of your Custom Model are defined correctly and precisely to ensure that [!DNL Marketo Measure] is producing an accurate Custom Attribution Model.

## Best Practice {#best-practice}

Whether you're setting up your Custom Model for the first time, or reviewing what has been previously established, it's important to keep the following best practices in mind.

* Start simple
   * Identify the key stages that you want to add to your Custom Model which are crucial to your [!DNL Marketo Measure] reporting. Typically these are stages which you are commonly measured against or which you are aiming to gain insight on
   * You can always add to your Custom Model over time
* Utilize the [!DNL Marketo Measure] Machine Learning Model
   * If you are struggling to decide the percentage attribution breakout, the [!DNL Marketo Measure] Machine Learning Model can help you to make informed decisions when setting you Custom Attribution Model.
   * When viewing the Machine Learning Model, the attribution percentages of each stage reflect the potential impact of your marketing efforts
      * A higher percentage means that marketing can directly influence the movement of the funnel at that point
      * A lower attribution percentage means that stages are less important for your team to monitor
* You must define your top of funnel stages based on either Lead or Contact stages, not across both
   * This means that you have to ensure that all persons will pass through that stage on the relative object
      * For example: If you define the MQL stage from the Lead object, all persons must go into your system as a Lead and be marked as an MQL on their Lead record in order for [!DNL Marketo Measure] to accurately reflect which touch was related to the Lead's transition to MQL. If this is not the case, and some people progress to Contact before becoming MQL as a Lead, [!DNL Marketo Measure] will not be able to accurately account for this in your Touchpoint data and we will have to assume that person has already MQL'd. [!DNL Marketo Measure] cannot account for stage hopping so we will infer that stages have been passed through even if they have not.
* Ensure field history tracking is enabled for all fields used to define custom stages that you incorporate
* Do not use a formula fields to define a custom stage
   * A Boolean field is best practice recommendation
* Do not incorporate Custom Stages into your Custom Model which coincide with a [!DNL Marketo Measure] Milestone Touchpoint Position (FT, LC, OC, Closed Won/Lost)
   * If you do, these positions will always occur simultaneously and can cause inflated attribution credit to parts of your funnel.
* Work with your Sales Opp team
   * Bringing in the team who works closest with stages and their meaning will ensure you're using the correct stages and that they're defined properly

## Best Practice for Maintenance {#best-practice-for-maintenance}

Reviewing your Custom Model at least twice a year will ensure that your custom attribution reporting is accurate and reliable.

If your Custom Model utilizes the Machine Learning Model, you should review its application within the Custom Model quarterly to ensure your Custom Model is as up to date as possible.

Other reasons to that might trigger a review of your Custom Model include...

* Turnover in your marketing team
* Any changes to your CRM stages
* Updates to your organizations funnel
* Seeing inaccurate revenue data in your [!DNL Marketo Measure] reporting when applying the Custom Model
* Seeing touchpoint positions populated that are no longer relevant to your organizations funnel

>[!MORELIKETHIS]
>
>* [Custom Attribution Model and Setup](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md)
>* [Enable Field History Tracking For Custom Model](/help/advanced-marketo-measure-features/custom-attribution-models/custom-model-setup-enable-field-history-tracking.md)
>* [Machine Learning Model](/help/advanced-marketo-measure-features/custom-attribution-models/machine-learning-model-faq.md)
