---
description: '[!DNL Salesforce] Package Consolidation - [!DNL Marketo Measure] - Product Documentation'
title: '[!DNL Salesforce] Package Consolidation'
exl-id: f1bd5dcb-d021-4140-b6b9-cdb40e566c4b
---
# [!DNL Salesforce] Package Consolidation {#salesforce-package-consolidation}

We're excited to announce upcoming changes to the Marketo Measure Salesforce Packages. In an effort to enhance user experience and simplify usage, we're consolidating all existing packages into a single, comprehensive package.

## Package Retirement {#package-retirement}

As a consequence of this consolidation, the current V1, V2_EXT, V2_Security, and all Reporting packages will be retired after August 2023. If you already have the V2 package installed, you must update it to the new consolidated version.

## New Consolidated Package {#new-consolidated-package}

The new consolidated V2 package incorporates all features and functionality from the previous packages, providing an improved user experience. This updated package enables more efficient marketing and sales performance tracking and allows for deeper insights into customer behavior.

We've added two new fields to enhance your reporting capabilities:

* form_name: Now available in BT/BAT objects, this field enables users to create reports based on form names.
* user_touchpoint_id: This field enables users to create reports with unique user touchpoint counts.

## Support and Transition {#support-and-transition}

We understand this change may require adjustments, and we are committed to supporting you throughout the process. Our [Support team](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} is readily available to answer any questions and assist with ensuring a smooth transition to the new consolidated package.

## Required Actions {#retired-actions}

* If you already have the V2 package installed, you must update it to the new consolidated version.
* If you have reports or dashboards from any Reporting package, you can easily recreate them without any modifications required, since all the fields utilized exist in the consolidated package.
* If you have reports using fields in the V2_EXT package, you can recreate them in the consolidated package through the steps below:
   * All the data in V2_EXT fields are available in Touchpoint fields, so you can modify your reports to fetch data from corresponding V2 touchpoint fields by adding a filter on the touchpoint position.
   * Example report fetching all leads with Ad Content FT containing "Outreach" text.
      * V2_EXT query:
         * bizible2_ext__Ad_Content_FT__c contains Outreach

![](assets/package-consolidation-1.png)

* Corresponding query in the consolidated package:
   * bizible2__Touchpoint_Position__c contains FT AND
   * bizible2__Ad_Content__c contains Outreach

![](assets/salesforce-package-consolidation-2.png)

## FAQ {#faq}

**Will the consolidated package have conflicts with fields in my existing package?**

You don't need to uninstall your package before installing the consolidated package. There will be no conflicts in fields since they will be in a different namespace.

**How can I backfill the data from my current packages?**

You can file a ticket [with Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} for backfilling and reprocessing BT/BAT data to fill in Touchpoint ID and Form ID fields.

**Will the fields in V1 and V2_EXT packages be available in the consolidated package?**

Yes. The consolidated package will contain the same fields in V1 with further breakdowns by objects and V2_EXT fields through Touchpoint fields.

**Can reports that use V2_EXT fields be re-created in the consolidated package?**

Yes. Please follow the steps in the [Required Actions](#retired-actions) section above.
