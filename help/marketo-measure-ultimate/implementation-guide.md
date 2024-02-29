---
description: '[!DNL Marketo Measure] Ultimate Implementation Guide - [!DNL Marketo Measure]'
title: '[!DNL Marketo Measure] Ultimate Implementation Guide'
feature: Integration, Tracking, Attribution
---
# [!DNL Marketo Measure] Ultimate Implementation Guide {#marketo-measure-ultimate-implementation-guide}

This article serves as an implementation guide for Marketo Measure Ultimate, providing clear steps and insights to ensure a successful integration and utilization.

## Main Differences When Using Ultimate over Standard Tiers {#main-differences-when-using-ultimate-over-standard-tiers}

Import B2B Data Through AEP: Marketers are expected to bring their B2B data (e.g. Account, Opportunity, Contact, Lead, Campaign, Campaign Member, Activity) through AEP. Ingest from nearly any data source as well as multiple data sources of the same type to bring in all your data for attribution.
   
   * Use with nearly any CRM, not just Salesforce and Dynamics.
   * Connect multiple CRM instances and/or MAP instances to one Marketo Measure instance.
   * Bring in 3rd-party webinar registration and participation data.

The direct CRM and Marketo Engage connections are no longer available for Ultimate.

   * Ultimate does not push data back to the CRM. Customers can consume data from the data warehouse.
   * Marketers will continue bringing Ad Platform data through direct connections and tracking web activities through Marketo Measure javascript.

Ultimate users will be provisioned AEP. If they already have AEP, we will not re-provision a new instance.

   * The AEP version provisioned will include all source connectors, schema data modeling, datasets, ad hoc query service, and a destination for Marketo Measure only.

Learn more about [Marketo Measure Ultimate](/help/marketo-measure-ultimate/marketo-measure-ultimate-overview.md){target="_blank"}.

## Schemas and Datasets {#schemas-and-datasets}

>[!NOTE]
>
>Check out [Building Blocks of a Schema](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=en#building-blocks-of-a-schema){target="_blank"} for an overview of schemas, classes, and field groups.

**XDM Schema = Class + Schema Field Group&#42;**

   * Required fields are not changeable. Customers can create and add custom fields as needed.
   * Example of field name based on hierarchy: accountOrganization.annualRevenue.amount

&#42; _A schema comprises a class and zero or more schema field groups. This means you could compose a dataset schema without using field groups._

![](assets/marketo-measure-ultimate-implementation-guide-1.png)

[Datasets overview](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html){target="_blank"}: All data successfully ingested into AEP is persisted within the Data Lake as datasets. A dataset is a storage and management construct for a collection of data, typically a table, that contains a schema (columns) and fields (rows).

## Creating a Schema {#creating-a-schema}

We recommend using an auto-generation utility to create 10 standard B2B schemas.

   * Steps to download and set up the utility [can be found here](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo-namespaces.html#set-up-b2b-namespaces-and-schema-auto-generation-utility){target="_blank"}.

For those with a _**CDP entitlement**_: Create schemas by going to the Sources page.

   * From a source, select Add Data > Use templates

![](assets/marketo-measure-ultimate-implementation-guide-2.png)

   * Select an account and all B2B templates to create 10 standard B2B schemas.

![](assets/marketo-measure-ultimate-implementation-guide-3.png)

## Dataflows {#dataflows}

>[!IMPORTANT]
>
>When adding a new dataset, we recommend creating a new flow instead of using an existing one. 

[Dataflows Overview](https://experienceleague.adobe.com/docs/experience-platform/dataflows/home.html){target="_blank"}

**Steps to create a dataflow:**

1. Select a Source.
1. Select an existing account or create an account.
1. Select a data type from the list of available types to import from the Source.
1. Select an existing dataset or create a new dataset.
1. Map the fields from the Source to the schema.

   >[!NOTE]
   >
   >* If you map one schema type to another identical one, it will be done automatically.
   >* You can also import mapping from another flow in the system. 
   >* You can map one Source field to multiple destination fields but can't do the opposite.
   >* You can create calculated fields ([Data Prep mapping functions](https://experienceleague.adobe.com/docs/experience-platform/data-prep/functions.html){target="_blank"}).

   >[!CAUTION]
   >
   >* You could edit a dataflow, but the data is not backfilled when a mapping is changed.
   >* If a required field is NULL, the entire flow will be rejected.

   >[!NOTE]
   >
   >[Marketo Measure Ultimate Data Integrity Requirement](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}

1. Set a data load cadence.
1. Review and Complete.
1. Check "Account Status" page in Measure UI settings for dataflow status.

**Monitoring:**

Sources > Dataflows page to check the status of dataflows

   * To view the activity details of a dataset, simply click on the dataset.
   * To view dataflow errors, select a dataflow, choose a dataflow run, and click "Error diagnostics preview."

## Data Inspection {#data-inspection}

Option 1: To run queries directly from the UI, access the Queries tab under Data Management.

![](assets/marketo-measure-ultimate-implementation-guide-4.png)

Option 2: [Download and use PSQL](https://experienceleague.adobe.com/docs/experience-platform/query/clients/psql.html){target="_blank"} (faster and more reliable).

## Activate Dataset for Marketo Measure {#activate-dataset-for-marketo-measure}

Before you begin, go to the "Experience Platform > Sandbox Mapping" section in the Measure UI settings and map a sandbox.

>[!CAUTION]
>
>This can't be changed once selected. 

1. In AEP, go to "Destinations > Marketo Measure page" to export datasets.
1. Configure destination.
1. Activate dataset.
1. Check "Account Status" page in Measure UI settings for dataflow status.

>[!NOTE]
>
>* Data for a given entity (e.g., Account) from a given source can only go into one dataset. Each dataset can only be included in one data flow. Violations will stop the data flow at run time.
>* Delete the entire destination in AEP to delete data in Measure. Disabling will only stop new data exports and keep the old data. 
>* The Measure configuration will mostly look the same, but some parts, like Stage Mapping, will look different.
>* It takes a few hours for a new dataflow to generate a flow run, and then they occur at regular hourly intervals.

In Measure, the default currency needs to be set in the "Currency" section

   * If you use multi-currency, the currency conversion rate schema has to be populated in AEP for us to read and use for conversions. 

**Stage Mapping:**

We don't automatically import stages from user data, so all stages must be mapped manually.

   * Users can map stages from different sources.

![](assets/marketo-measure-ultimate-implementation-guide-5.png)

If the stages are not mapped, the system will not function because there will be nowhere for the data to go.

If you're a Marketo Measure Ultimate customer and have set your Default Dashboard Object as Contact, do not use the below two fields specific to Lead ([learn more here](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}). 
      
* b2b.personStatus
* b2b.isConverted

**Campaign Member Rules:**

Need to pick a dataset and set rules for each. 

**Experience Events Rules:**

Need to pick a dataset and select activity types.

   * Custom activities are not supported yet. 
   * If the customer has activities that do not fit the available options, we suggest categorizing them as "Interesting Moments" and using custom fields to distinguish them.

**Offline Channels:**

   * We don't do dataset-specific channel mapping rules, so this would be global.
   * We need to match both CRM Campaign Type and Channel eventually, but for now, we can map the channel name to both fields as a workaround. 
   * **Channel rules: Backfilled data won't have stage transition data.**

Touchpoint and Segment settings remain the same.
