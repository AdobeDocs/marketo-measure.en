---
unique-page-id: 18874771
description: Using Data Loader to Update Marketo Measure Custom Amount Field - Marketo Measure - Product Documentation
title: Using Data Loader to Update Marketo Measure Custom Amount Field
exl-id: 55e91ac4-a835-48e0-a6ce-1d85b32aeac0
---
# Using Data Loader to Update Marketo Measure Custom Amount Field {#using-data-loader-to-update-marketo-measure-custom-amount-field}

Marketo Measure recommends using Data Loader as a convenient option to update opportunity values when using a custom revenue field (we use the Amount field out of the box) in Marketo Measure. Data Loader is preferred over using the Marketo Measure update script as the script requires users to disable all Salesforce validation rules while the Marketo Measure script runs.

## Using Data Loader to Update Marketo Measure Custom Amount Field{#using-data-loader-to-update-marketo-measure-custom-amount-field-1}

1. Create an excel sheet with the:

    * Opportunity Id
    * Custom Opportunity Amount field (your preferred revenue field)
    * Marketo Measure Opportunity Amount field

1. Copy and paste the values from your preferred revenue field into the Marketo Measure Opportunity Amount field. Then, update these Opps using the .csv file.

**_Alternatively, you can go into Salesforce and use a custom list view to mass edit all the opportunities..._**

1. Create a Custom List view for all Opportunities.
1. Add a filter for preferred revenue field is not blank _and_ Marketo Measure Opportunity Amount field is blank.
1. Click **Mass Edit**, but don’t actually change anything.
1. Click **Save**. This will trigger the workflow to populate the Marketo Measure Opportunity Amount fields with the Software Revenue field.
