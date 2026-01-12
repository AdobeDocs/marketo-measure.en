---
description: Report Type for Contacts Without Opportunities
title: Report Type for Contacts Without Opportunities
exl-id: 255048be-16ff-4964-85fd-cc07888a05af
feature: Reporting
---

# Report Type for Contacts Without Opportunities {#report-type-for-contacts-without-opportunities}

>[!NOTE]
>You may see instructions specifying "[!DNL Marketo Measure]" in the documentation, but still see "[!DNL Bizible]" in your CRM. We are working to have that updated and the rebranding will be reflected in your CRM soon.

In order to report on Contacts with Buyer Touchpoints that are not associated to an Opportunity, you need to create a custom report type.

1. Go to **[!UICONTROL Setup]** > **[!UICONTROL Create]** > **[!UICONTROL Report Types]**.

   ![Report Types page in Salesforce Setup](assets/1.jpg)

1. Select **[!UICONTROL New Custom Report Type]**.

   ![New Custom Report Type selection screen](assets/2.jpg)

1. Set the [!UICONTROL Primary Object] as "[!UICONTROL Contacts]." Name the Report Type Label as "Contacts with Buyer Touchpoints." Use the same naming for the Report Type Name. Within the description input, "Contacts with Buyer Touchpoints." Save the Report within the "[!UICONTROL Other]" and set the report to "[!UICONTROL Deployed]."

   ![Report type details with Contacts as primary object](assets/3.jpg)

1. From there, you will link the Contacts Object to the Buyer Touchpoints Object. Ensure that you choose the button "Each "A" record must have at least one related "B" record."

   ![Object relationship configuration linking Contacts to Buyer Touchpoints](assets/4.jpg)

1. Click **[!UICONTROL Save]** and you are done!
