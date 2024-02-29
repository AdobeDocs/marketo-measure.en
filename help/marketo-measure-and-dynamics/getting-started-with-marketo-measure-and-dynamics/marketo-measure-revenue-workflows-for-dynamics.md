---
unique-page-id: 37356132
description: "[!DNL Marketo Measure] Revenue Workflows for Dynamics - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Revenue Workflows for Dynamics"
exl-id: 0e64201a-bc65-4a6d-9192-09c14c810c4a
feature: Microsoft Dynamics
---
# [!DNL Marketo Measure] Revenue Workflows for Dynamics {#marketo-measure-revenue-workflows-for-dynamics}

## Part 1: Estimated Revenue vs Actual Revenue {#part-estimated-revenue-vs-actual-revenue}

[!DNL Marketo Measure] points to one standard revenue field out of the box (Actual Revenue) but Dynamics has two standard revenue fields: Actual Revenue and Estimated Revenue. To have pipeline revenue available in the Discover Dashboard, a custom field and a workflow are needed to capture the correct amount from either the Estimated Revenue or the Actual Revenue field depending on whether the Opportunity is Open or Closed (Won).

Step 1: Create custom opportunity amount field in Dynamics

>[!NOTE]
>
>All Dynamics revenue fields have a base field and a regular field. Disregard the base field.

Step 2: Create a workflow that updates both the custom opportunity amount field created in step 1 and the [!DNL Marketo Measure] Opportunity Amount field.

>[!NOTE]
>
>We cannot point to the [!DNL Marketo Measure] Opportunity Amount (bizible2_bizible_opportunity_amount) field in Discover with Dynamics accounts. Dynamics customers must create a custom opportunity amount field for [!DNL Marketo Measure] to point to in Discover. Once complete, the customer needs to create a workflow that updates **both** the [!DNL Marketo Measure] Opportunity Amount (bizible2_bizible_opportunity_amount) **and** the custom opportunity amount field. The [!DNL Marketo Measure] Opportunity Amount field comes with the package but a custom field must be created.

Amount Workflow Instructions:

**WORKFLOW #1**: Opportunity – Update [!DNL Marketo Measure] Opportunity Amount Field & Custom Field = Estimated Revenue

This workflow runs on open opportunities each time Estimated Revenue changes and will update the [!DNL Marketo Measure] Opportunity Amount field and your custom field to equal the Estimated Revenue field. The workflow should be set to run "Real Time," but may also be run "on demand" to update open Opportunities.

Provide your [!DNL Marketo Measure] point of contact with the name of the custom opportunity amount field. They will update the [!DNL Marketo Measure] App Opportunity Settings to include the name of the custom opportunity amount field. This will tell Discover which field to use in reporting.

**WORKFLOW #2**: Opportunity – Update [!DNL Marketo Measure] Opportunity Amount Field & Custom Field = Actual Revenue

This workflow runs in real time. It initiates when a user closes an Opportunity and will update the [!DNL Marketo Measure] Opportunity Amount field and your custom field with the Actual Revenue added to the Opportunity Close form before the Opportunity locks down as closed.

## Part 2: Estimated Close Date vs. Actual Close Date {#part-estimated-close-date-vs-actual-close-date}

Out of the box, pipeline revenue data will not be available in the dashboard because, by default, Dynamics has two stock close date fields: Estimated Close Date and Actual Close Date. [!DNL Marketo Measure] can only point to one close date field in the dashboard and we are currently pointing to the Actual Close Date.

If open opportunities have no data in the Actual Close Date field, we are not seeing any data in the dashboard for open opportunities. That being said, a workflow is needed based on opportunity stage to support both date fields.

1. Create Custom Close Date Field on the Opportunity Object (i.e. [!DNL Marketo Measure] Custom Close Date).
1. Create a Workflow to update the [!DNL Marketo Measure] Custom Close Date field with the date from either the Estimated Close Date or the Actual Close Date, depending on the whether the opportunity is open or closed (workflow should be saved to run in real time, but will need to be ran "on demand" at least once to update all current open opps).
1. Test the workflow and confirm it works.
1. Customer to provide the Custom Close Date API name to [!DNL Marketo Measure].
1. [!DNL Marketo Measure] to update the [!DNL Marketo Measure] app settings to point to the [!DNL Marketo Measure] Custom Close Date field in the Dashboard.

   Upon completion of the above steps, we will need to run workflows to update both the Custom [!DNL Marketo Measure] Opp Amount field and the [!DNL Marketo Measure] Custom Close Date field on your historical opportunities to reflect the correct data. This will likely change the modified on/by fields so you will want to check with your team to see if that presents any issues.

To update the closed opportunities...

1. Isolate opportunities that have closed since your [!DNL Marketo Measure] start date up til the workflow is active. This is the group of historical opportunities that you will need to update via workflow.
1. Export all records to Excel.
1. Open Excel file, enable content.
1. Copy Actual Close Date data to [!DNL Marketo Measure] Custom Close Date.
1. Copy Actual Revenue data to [!DNL Marketo Measure] Custom Opportunity Amount **and** [!DNL Marketo Measure] Opportunity Amount (there are two fields.)
1. Save file.
1. Import file. Dynamics will recognize this as a file with existing records to update.
1. Check for failures on import file.

>[!NOTE]
>
>The workflows outlined in this document are just one way to go about updating the fields so [!DNL Marketo Measure] can show the correct data in Discover. If you have another way of accomplishing the same task, you can go for it. Basically what we need from them is some sort of workflow(s) that accomplish the following:
>
> * If Opp = Open, update custom close date field, custom opp amount field, and [!DNL Marketo Measure] opp amount field to equal Estimated Close Date and Estimated Revenue, respectively.
> * If Opp = Closed Won, update custom close date field, custom opp amount field, and [!DNL Marketo Measure] opp amount field to equal Actual Close Date and Actual Revenue, respectively.
