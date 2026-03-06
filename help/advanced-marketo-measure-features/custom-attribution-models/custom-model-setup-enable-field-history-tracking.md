---
unique-page-id: 18874777
description: Custom Model Setup - Enable Field History Tracking - [!DNL Marketo Measure]
title: Custom Model Setup - Enable Field History Tracking
exl-id: 70328e67-051b-4864-891b-b251e49859c2
feature: Custom Models
---
# Custom Model Setup: Enable Field History Tracking {#custom-model-setup-enable-field-history-tracking}

## Why and When to Enable Field History Tracking {#why-and-when-to-enable-field-history-tracking}

If you decide to include a custom field as a stage in your custom attribution model, field history tracking **must be enabled** for this field. Enabling field history tracking will allow [!DNL Salesforce] to track any time the custom field is edited by creating a record in the History Tracking table. [!DNL Marketo Measure] can download that table and use this information to measure the time and day that a "transition" occurred. Without field history tracking, [!DNL Marketo Measure] is unable to track changes related to this field.

If only [!UICONTROL Lead Status] or Opportunity Stages are used in the custom model, there is no need to turn on Field History tracking because it will tracked automatically as a stage transition.

To enable field history tracking, follow the instructions below.

## Enable Field History Tracking {#enable-field-history-tracking}

>[!NOTE]
>
>You will need to be a System Administrator in order to make these changes to the fields on the Lead/Contact/Opportunity object.

1. Go to the Object where the custom field lives and click the **[!UICONTROL Set History Tracking]** button.

   ![](assets/1.png)

1. Select the fields you wish to track changes on.

   ![](assets/2.png)

[!DNL Marketo Measure] can only re-import a record if it sees that the record has recently been modified. Formula fields technically do not modify a record when it changes since it does the calculation in the background. We have seen issues where a rule is skipped because [!DNL Marketo Measure] did not see the record change, so it is advised to **not use formula fields in rule definitions**. The solution is to create a text field and use a workflow to populate that field with the proper value or calculation any time the record is edited or fits the criteria. This requires that all records get edited so the workflow can work retroactively on old records.
