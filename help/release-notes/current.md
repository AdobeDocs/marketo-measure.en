---
description: Current Release Notes - [!DNL Marketo Measure] - Product Documentation
title: Current Release Notes
exl-id: e93ff03e-ea21-41f4-abb8-32313ee74c0c
feature: Release Notes
---
# Release Notes: 2023 {#release-notes-2023}

Below you'll find all the new and updated features for our 2023 releases.

## Q4 Release {#q4-release}

<p>

**Discover Dashboard Redesign**

All Marketo Measure users will experience our redesigned in-app dashboards that combine enhanced usability with added value. We're also introducing new metrics, such as "Realized ROI," which takes into account the typical delay between marketing investments and purchases in B2B go-to-markets.

The new set of pre-built dashboards is scheduled to be introduced in waves, beginning the first week of October and concluding before the end of the year. These new dashboards will automatically appear in your instances, along with in-product information and links to documentation.

* [New Discover Dashboard Guide](/help/marketo-measure-discover-ui/dashboards/new-discover-dashboard-guide.md){target="_blank"}
* [Discover Dashboard Basics](/help/marketo-measure-discover-ui/dashboards/discover-dashboard-basics.md){target="_blank"}
* [Revenue Overview Dashboard](/help/marketo-measure-discover-ui/dashboards/revenue-overview-dashboard.md){target="_blank"}
* [Attributed Revenue Dashboard](/help/marketo-measure-discover-ui/dashboards/attributed-revenue-dashboard.md){target="_blank"}
* [ROI Dashboard](/help/marketo-measure-discover-ui/dashboards/roi-dashboard.md){target="_blank"}
* [Passport Dashboard](/help/marketo-measure-discover-ui/dashboards/passport-dashboard.md){target="_blank"}

>[!NOTE]
>
>While the current dashboards will be deprecated by mid-January 2024, you can utilize both versions until then, ensuring a smooth transition.

### Deprecations {#deprecations}

<p>

* **"custom_properties" Field** 

In our data warehouse, the "custom_properties" field has been serving as a storage for additional data points not covered by our fixed schema. Stored in JSON format, this field's usage is limited and its integration with SQL queries can be complicated, affecting performance. Given these factors, we've decided to deprecate this field. This change will mainly affect the data processing layer within our Azure table storage and the data exported to our data warehouse.

* **Dynamics Package related**

   * To stay connected to Dynamics, install our latest package version, v6.12. Old versions `(<v6.12)` will no longer be supported. This update optimizes historical record creation to reduce storage usage.

   * The outdated method of OAuth with a RefreshToken will be deprecated. Please refer to [this guide](/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/oauth-with-azure-active-directory-for-dynamics-crm.md){target="_blank"} for updating your credentials to adhere to Microsoft's best practices of using ClientSecret.

### What's coming? {#q4-whats-coming}

<p>

**In-app Custom Reporting**

Marketo Measure customers, for the first time, will be able to create and save their own reports right in the app. This will follow the release of the pre-built dashboards in early 2024.

<br>

## Q2 Release {#q2-release}

<p>

* **Salesforce Package Consolidation**

We're merging all Salesforce packages into a single, comprehensive package for an improved user experience and simplified usage. The V1, V2_EXT, and Reporting packages will be retired next quarter. The new package combines all previous features, allowing for more efficient tracking and deeper customer insights.

Customers who already have the V2 package installed must update it to the new consolidated version.

We've added two new fields to enhance your reporting capabilities:

* form_name: Now available in BT/BAT objects, this field enables users to create reports based on form names.
* user_touchpoint_id: This field enables users to create reports with unique user touchpoint counts. 

[This article](/help/configuration-and-setup/marketo-measure-and-salesforce/salesforce-package-consolidation.md){target="_blank"} includes guides on recreating reports and dashboards from the legacy Reporting packages.

* **Salesforce API Version Updates**

All Salesforce API versions of Apex classes, including the UserActivityContext class, are updated to supported versions. (31.0 through 57.0)

* **New Package Installation**

The new consolidated package installation link [can be found here](https://login.salesforce.com/packaging/installPackage.apexp?p0=04t1P000000VY6Z){target="_blank"}

### What's coming? {#q2-whats-coming}

<p>

**Changes in IP Address Storage**

We will no longer store IP addresses in our system per privacy considerations. We will continue identifying and storing the geo-location of the IP address, but the format will change (e.g., "United States" to "US").
