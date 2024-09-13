---
description: Learn about the migration process when moving from the [!DNL Marketo Measure] Tiered subscription to [!DNL Marketo Measure] Ultimate.
title: Migration from Tier to [!DNL Marketo Measure] Ultimate
feature: Integration, Tracking, Attribution
---
# Migration from Tier 1-2 to [!DNL Marketo Measure] Ultimate {#migration-from-tier-to-marketo-measure-ultimate}

This article outlines the migration process for users moving from the Tier 1 or 2 subscription to [!DNL Marketo Measure] Ultimate.

>[!IMPORTANT]
>
>Remember to retain your existing Tier instance until the migration is complete.

## Data Collection {#data-collection}

### Web Traffic Data {#web-traffic-data}

* No changes are required for JavaScript deployment.

* Enable domains in the new Ultimate instance.

* If needed, submit a ticket to migrate and reprocess historical web data.

* Ad integrations remain unchanged, but remember to reconnect them in Ultimate. Before doing so, ensure that you disconnect your Ad accounts in the Tier tenant.

>[!NOTE]
>
>Historical ad cost data will not be imported. We will only import ad cost data moving forward after the Ad accounts are reconnected.

### Enterprise Data Connection {#enterprise-data-connection}

Reimplement all source data connections in AEP, including CRM and Marketo Engage connections.

## Data Transformation {#data-transformation}

* Account-Based Marketing features, including lead-to-account matching and predictive engagement scores, are not available in Ultimate.

  * You can, however, import your lead-to-account matching results through AEP and use them within the platform.

* In Ultimate, CRM historical stage transitions are inferred rather than directly read, as there is no direct CRM connection.

  * We read opportunity records and timestamps and see the current stage, then infer the historical stages.

## Reporting {#reporting}

* Ultimate does not push data back to CRMs.

  * If pushing data back to the CRM is desired, a custom ETL pipeline is required to extract data from Marketo Measure Snowflake to the CRM. You must set up a custom data model in your CRM.

* All Discover dashboards remain the same as in the Tiered solution, with the addition of Attribution AI dashboards.
