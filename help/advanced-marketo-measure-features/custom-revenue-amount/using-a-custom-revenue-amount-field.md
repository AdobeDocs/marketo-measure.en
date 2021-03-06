---
unique-page-id: 18874793
description: Using a Custom Revenue Amount Field - Marketo Measure - Product Documentation
title: Using a Custom Revenue Amount Field
exl-id: 517ea4f9-aa83-48d0-8ce7-003f4a907430
---
# Using a Custom Revenue Amount Field {#using-a-custom-revenue-amount-field}

By default, Buyer Attribution Touchpoints will pull the Opportunity Amount from one of two fields:

* Amount (SFDC Default)
* Marketo Measure Opportunity Amount (Custom)

If you are using a custom Amount field on your Opportunities, we will need to configure a workflow in order to calculate the Buyer Touchpoint Revenue. This takes some more advanced knowledge of Salesforce, so it may require assistance from your SFDC Admin.

Starting off, we will need the following information:

* API Name of your Amount field

From here, we will start creating the workflow.

1. Navigate to Setup > Create > Workflow & Approvals > Workflow Rules.

   ![](assets/1.jpg)

1. Select **New Rule**, set the object as “Opportunity” and click **Next**.

   ![](assets/2.jpg)

   ![](assets/3.jpg)

1. Configure the workflow. Set the Rule Name as “Update Marketo Measure Opportunity Amount." Set the Evaluation Criteria to “Created, and every time it’s edited.” For the Rule Criteria, select your custom Amount field and select the Operator as “Not Equal To” and leave the “Value” field blank.

   ![](assets/4.jpg)

1. Add a workflow action. Set this picklist to “New Field Update.”

   ![](assets/5.jpg)

1. Here you will fill out field information. In the “Name” field, we recommend using this naming: “Marketo Measure Opp Amount." The “Unique Name” will automatically populate based off the “Name” field. In the “Field to Update” picklist select “Marketo Measure Opportunity Amount." After selecting the field, select the "Re-Evaulate Workflow Rules after Field Change" box. In the “Specify New Field Value,” select “Use a formula to set the new value." In the empty box, drop the API name of your custom Amount field. Click **Save**.

   ![](assets/6.png)

1. You will be brought back to a roll-up page for your workflow, be sure to “Activate” and you’ll be good to go. To activate, click **Edit** next to your new workflow and then click **Activate**.

   Once you’ve completed these steps, the opportunities will need to be updated in order to trigger the workflow to have the new value from the custom opportunity field.

   This can be accomplished by running your opportunities through Data Loader within SFDC. Please find details on using Data Loader in [this article](/help/advanced-marketo-measure-features/custom-revenue-amount/using-data-loader-to-update-marketo-measure-custom-amount-field.md).

If there are any questions along the way, please don’t hesitate to reach out to your Customer Success Manager or [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
