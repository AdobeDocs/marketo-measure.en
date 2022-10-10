---
unique-page-id: 18874614
description: Leads with Buyer Touchpoints Report - [!DNL Marketo Measure] - Product Documentation
title: Leads with Buyer Touchpoints Report
exl-id: 0376abb0-5eed-41bb-ab4f-3c204ab437df
---
# Leads with Buyer Touchpoints Report {#leads-with-buyer-touchpoints-report}

>[!NOTE]
>
>You may see instructions specifying "[!DNL Marketo Measure]" in our documentation, but still see "[!DNL Bizible]" in your CRM. We are working to have that updated and the rebranding will be reflected in your CRM soon.

Out of the box you have many reporting capabilities at your fingertips when it comes to [!DNL Marketo Measure], but there are some additional report types we recommend building. Learn about creating an inclusive Leads with Buyer Touchpoints report type below.

1. Navigate to your Setup option within [!DNL Salesforce]. From there, expand the "Create" grouping and select **[!UICONTROL Report Types]**.

   ![](assets/1.jpg)

1. Select **[!UICONTROL New Custom Report Type]**.

   ![](assets/2.jpg)

1. Set the primary object as "Leads" and within the "Report Type Label" input "Leads with Buyer Touchpoints - Inclusive." Store the report within the "Leads" category and change the deployment status to **[!UICONTROL Deployed]**. Then select **[!UICONTROL Next]**.

   ![](assets/3.jpg)

1. For the object relationships, select the **[!DNL Marketo Measure] Persons** object as the secondary object. Select the A to B relationship as, "Each 'A' record must have at least one related 'B' record." From there, you will relate the "Buyer Touchpoint" object and select the same relationship between the B and C objects.

   ![](assets/4.jpg)

1. Save and start building some reports!
