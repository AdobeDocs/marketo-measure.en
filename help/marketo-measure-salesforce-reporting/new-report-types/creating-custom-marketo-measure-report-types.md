---
unique-page-id: 18874539
description: Creating Custom Marketo Measure Report Types - Marketo Measure - Product Documentation
title: Creating Custom Marketo Measure Report Types
exl-id: 1d72a04f-6a2d-4607-ad09-3b025125156a
---
# Creating Custom Marketo Measure Report Types {#creating-custom-marketo-measure-report-types}

Learn how to create custom Marketo Measure Salesforce report types. There are three different report types we recommend creating: Leads with Buyer Touchpoints (Custom), Marketo Measure Person with Buyer Touchpoints (Custom), Opportunities with Buyer Attribution Touchpoint (Custom).

## Leads with Buyer Touchpoints (Custom) {#leads-with-buyer-touchpoints-custom}

1. Go to **Setup** > **Build** > **Report Types** > **New Custom Report Types**.

   ![](assets/1.png)

1. Define the Custom Report Type.

    * Report Type Focus > Primary Object: Lead
    * Identification > Report Type Label: Leads with Buyer Touchpoints (Custom)
    * Store in Category: Other Reports
    * Deployment > Deployment Status: Deployed

   ![](assets/2.png)

1. Define the Object Relationships.

    * Relate the Lead object (A) to the Marketo Measure Person Object (B) and then to the Buyer Touchpoint Object (C)
    * Ensure that “Each A/B record must have at least one B/C” record is selected
    * Save

   ![](assets/3.png)

## Marketo Measure Person with Buyer Touchpoints (Custom) {#marketo-measure-person-with-buyer-touchpoints-custom}

1. Go to **Setup** > **Build** > **Report Types** > **New Custom Report Types**.

   ![](assets/4.png)

1. Define the Custom Report Type.

    * Report Type Focus > Primary Object: Marketo Measure Persons
    * Identification > Report Type Label: Marketo Measure Person with Buyer Touchpoints (Custom)
    * Store in Category: Other Reports
    * Deployment > Deployment Status: Deployed

   ![](assets/5.png)

1. Define the Object Relationships.

    * Relate the Marketo Measure Person object (A) to the Buyer Touchpoint Object (B)
    * Ensure that “Each A record must have at least one B” record is selected
    * Save

   ![](assets/6.png)

## Opportunities with Buyer Attribution Touchpoint (Custom) {#opportunities-with-buyer-attribution-touchpoint-custom}

1. Go to **Setup** > **Build** > **Report Types** > **New Custom Report Types**.

   ![](assets/7.png)

1. Define the Custom Report Type.

    * Report Type Focus > Primary Object: Opportunities
    * Identification > Report Type Label: Opportunities with Buyer Attribution Touchpoint (Custom)
    * Store in Category: Other Reports
    * Deployment > Deployment Status: Deployed

   ![](assets/8.png)

1. Define the Object Relationships.

    * Relate the Opportunities object (A) to the Buyer Attribution Touchpoint Object (B)
    * Ensure that “Each A record must have at least one B” record is selected
    * Save

   ![](assets/9.png)

## Adding Custom Fields to Custom Report Types {#adding-custom-fields-to-custom-report-types}

1. Once the reports are created, you’ll be redirected to an overview of the report type. Click **Edit Layout**.

   ![](assets/10.png)

1. Ensure that the custom fields you wish to add to the report appear in the Field Layout Properties section. If there are any other fields you’d like to add, use the “Add fields related via lookup” option.

   ![](assets/11.png)
