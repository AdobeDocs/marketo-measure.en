---
unique-page-id: 18874539
description: Creating Custom [!DNL Marketo Measure] Report Types - [!DNL Marketo Measure] - Product Documentation
title: Creating Custom [!DNL Marketo Measure] Report Types
exl-id: 1d72a04f-6a2d-4607-ad09-3b025125156a
---
# Creating Custom [!DNL Marketo Measure] Report Types {#creating-custom-marketo-measure-report-types}

>[!NOTE]
>
>You may see instructions specifying "[!DNL Marketo Measure]" in our documentation, but still see "[!DNL Bizible]" in your CRM. We are working to have that updated and the rebranding will be reflected in your CRM soon.

Learn how to create custom [!DNL Marketo Measure] [!DNL Salesforce] report types. There are three different report types we recommend creating: Leads with Buyer Touchpoints (Custom), [!DNL Marketo Measure] Person with Buyer Touchpoints (Custom), Opportunities with Buyer Attribution Touchpoint (Custom).

## Leads with Buyer Touchpoints (Custom) {#leads-with-buyer-touchpoints-custom}

1. Go to **[!UICONTROL Setup]** > **[!UICONTROL Build]** > **[!UICONTROL Report Types]** > **[!UICONTROL New Custom Report Types]**.

   ![](assets/1.png)

1. Define the Custom Report Type.

    * [!UICONTROL Report Type Focus] > [!UICONTROL [!UICONTROL Primary Object]]: Lead
    * Identification > [!UICONTROL Report Type Label]: Leads with Buyer Touchpoints (Custom)
    * [!UICONTROL Store in Category]: Other Reports
    * [!UICONTROL Deployment] > [!UICONTROL Deployment Status]: Deployed

   ![](assets/2.png)

1. Define the Object Relationships.

    * Relate the Lead object (A) to the [!DNL Marketo Measure] Person Object (B) and then to the Buyer Touchpoint Object (C)
    * Ensure that "[!UICONTROL Each A/B record must have at least one B/C]" record is selected
    * [!UICONTROL Save]

   ![](assets/3.png)

## [!DNL Marketo Measure] Person with Buyer Touchpoints (Custom) {#marketo-measure-person-with-buyer-touchpoints-custom}

1. Go to **[!UICONTROL Setup]** > **[!UICONTROL Build]** > **[!UICONTROL Report Types]** > **[!UICONTROL New Custom Report Types]**.

   ![](assets/4.png)

1. Define the Custom Report Type.

    * [!UICONTROL Report Type Focus] > [!UICONTROL Primary Object]: [!DNL Marketo Measure] Persons
    * [!UICONTROL Identification] > [!UICONTROL Report Type Label]: [!DNL Marketo Measure] Person with Buyer Touchpoints (Custom)
    * [!UICONTROL Store in Category]: Other Reports
    * [!UICONTROL Deployment] > [!UICONTROL Deployment Status]: Deployed

   ![](assets/5.png)

1. Define the Object Relationships.

    * Relate the [!DNL Marketo Measure] Person object (A) to the Buyer Touchpoint Object (B)
    * Ensure that "[!UICONTROL Each A record must have at least one B]" record is selected
    * [!UICONTROL Save]

   ![](assets/6.png)

## Opportunities with Buyer Attribution Touchpoint (Custom) {#opportunities-with-buyer-attribution-touchpoint-custom}

1. Go to **[!UICONTROL Setup]** > **[!UICONTROL Build]** > **[!UICONTROL Report Types]** > **[!UICONTROL New Custom Report Types]**.

   ![](assets/7.png)

1. Define the Custom Report Type.

    * [!UICONTROL Report Type Focus] > [!UICONTROL Primary Object]: Opportunities
    * [!UICONTROL Identification] > [!UICONTROL Report Type Label]: Opportunities with Buyer Attribution Touchpoint (Custom)
    * [!UICONTROL Store in Category]: Other Reports
    * [!UICONTROL Deployment] > [!UICONTROL Deployment Status]: Deployed

   ![](assets/8.png)

1. Define the Object Relationships.

    * Relate the Opportunities object (A) to the Buyer Attribution Touchpoint Object (B)
    * Ensure that "[!UICONTROL Each A record must have at least one B]" record is selected
    * [!UICONTROL Save]

   ![](assets/9.png)

## Adding Custom Fields to Custom Report Types {#adding-custom-fields-to-custom-report-types}

1. Once the reports are created, you'll be redirected to an overview of the report type. Click **[!UICONTROL Edit Layout]**.

   ![](assets/10.png)

1. Ensure that the custom fields you wish to add to the report appear in the Field Layout Properties section. If there are any other fields you'd like to add, use the "[!UICONTROL Add fields related via lookup]" option.

   ![](assets/11.png)
