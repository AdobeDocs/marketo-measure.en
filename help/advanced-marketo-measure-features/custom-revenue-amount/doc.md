---
description: Using a Custom Revenue Amount Field - [!DNL Marketo Measure] - Product Documentation
title: Using a Custom Revenue Amount Field
hide: yes
hidefromtoc: yes
feature: Custom Revenue Amount
---
# Using a Custom Revenue Amount Field {#using-a-custom-revenue-amount-field}

By default, Buyer Attribution Touchpoints will pull the Opportunity Amount from one of two fields:

* Amount (SFDC Default)
* [!DNL Marketo Measure] Opportunity Amount (Custom)

If you are using a custom Amount field on your Opportunities, we will need to configure a workflow in order to calculate the Buyer Touchpoint Revenue. This takes some more advanced knowledge of [!DNL Salesforce], so it may require assistance from your SFDC Admin.

Starting off, we will need the following information:

* API Name of your Amount field

From here, we'll start creating the workflow. 

## Create the Workflow in Salesforce Lightning {#create-the-workflow-in-salesforce-lightning}

The following steps are for Salesforce Lightning users. If you still use Salesforce Classic, those steps [are listed below](#create-the-workflow-in-salesforce-classic).

1. From Setup, type "Flows" into the Quick Find Box, and select **Flows** to start Flow Builder. From the right panel click the **New Flow** button.

   ![](assets/using-a-custom-revenue-amount-field-1.png) 
 
1. Select **Record-Triggered Flow** and click the **Create** button on the bottom right. 
 
   ![](assets/using-a-custom-revenue-amount-field-2.png) 

1. In the Configure Start window, select the Opportunity object. From the Configure Trigger section, select **A record is created or updated**.
 
   ![](assets/using-a-custom-revenue-amount-field-3.png) 

1. In the Set Entry Conditions section, under Condition Requirements, select **Custom Condition Logic Is Met**. 
   * From the search field, select your custom Amount field. 
   * Set the operator as **Is Null**, and the value as **False**. 
   * Set the evaluation criteria to **Every time a record is updated and meets the condition requirements**.

   ![](assets/using-a-custom-revenue-amount-field-4.png) 
 
1. Under the "Optimize the Flow for" section, select **Fast Field Updates**. Click **Done**. 

   ![](assets/using-a-custom-revenue-amount-field-5.png) 
 
1. To add the element, click the plus (+) icon and select **Update Triggering Record**.

   ![](assets/using-a-custom-revenue-amount-field-6.png) 
 
1. In the New Update Records window, enter the following: 

   * Enter a label&mdash;the API name will be generated automatically 
   * Under "How to Find Records to Update and Set Their Values," select **Use the opportunity record that triggered the flow**. 
   * In the "Set Filter Conditions" section, select **Always Update Record** as a Condition Requirement to Update Record.
   * In "Set Field Values for the Campaign Record," from field, select Marketo Measure Opportunity Amount and value your custom Amount field.
   * Click **Done**.

   ![](assets/using-a-custom-revenue-amount-field-7.png) 

1. Click **Save**. A pop-up will appear. Type "Flow Label" in the Save the Flow window (the Flow API Name will be generated automatically). Click **Save** again.
 
   ![](assets/using-a-custom-revenue-amount-field-8.png) 

1. Click the **Activate** button to activate the flow.

   ![](assets/using-a-custom-revenue-amount-field-9.png) 

## Create the Workflow in Salesforce Classic {#create-the-workflow-in-salesforce-classic}

The following steps are for Salesforce Classic users. If you have made the switch to Salesforce Lightning, those steps [can be found above](#create-the-workflow-in-salesforce-lightning).

1. Navigate to **[!UICONTROL Setup]** > **[!UICONTROL Create]** > **[!UICONTROL Workflow & Approvals]** > **[!UICONTROL Workflow Rules]**.

   ![](assets/1.jpg)

1. Select **[!UICONTROL New Rule]**, set the object as "Opportunity" and click **[!UICONTROL Next]**.

   ![](assets/2.jpg)

   ![](assets/3.jpg)

1. Configure the workflow. Set the Rule Name as "Update [!DNL Marketo Measure] Opportunity Amount." Set the Evaluation Criteria to "Created, and every time it's edited." For the Rule Criteria, select your custom Amount field and select the Operator [!UICONTROL as "Not Equal To"] and leave the "Value" field blank.

   ![](assets/4.jpg)

1. Add a workflow action. Set this picklist to "[!UICONTROL New Field Update]."
   ![](assets/5.jpg)

1. Here you'll fill out field information. In the "Name" field, we recommend using this naming: "[!DNL Marketo Measure] Opp Amount." The "Unique Name" will automatically populate based off the "Name" field. In the "Field to Update" picklist select "[!DNL Marketo Measure] Opportunity Amount." After selecting the field, select the "Re-Evaulate Workflow Rules after Field Change" box. In the "Specify New Field Value," select "Use a formula to set the new value." In the empty box, drop the API name of your custom Amount field. Click **[!UICONTROL Save]**.

   ![](assets/6.png)

1. You'll be brought back to a roll-up page for your workflow, be sure to "Activate" and you'll be good to go. To activate, click **Edit** next to your new workflow and then click **Activate**.

   Once you've completed these steps, the opportunities will need to be updated in order to trigger the workflow to have the new value from the [!UICONTROL custom opportunity] field.

   This can be accomplished by running your opportunities through Data Loader within SFDC. Please find details on using Data Loader in [this article](/help/advanced-marketo-measure-features/custom-revenue-amount/using-data-loader-to-update-marketo-measure-custom-amount-field.md).

If there are any questions along the way, please don't hesitate to reach out to the Adobe Account Team (your Account Manager) or [[!DNL Marketo] Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
