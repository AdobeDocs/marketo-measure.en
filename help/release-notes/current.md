---
description: Current Release Notes - [!DNL Marketo Measure] - Product Documentation
title: Current Release Notes
hide: yes
hidefromtoc: yes
---
# Release Notes: 2023 {#release-notes-2023}

Below you'll find all the new and updated features for our 2023 releases.

## Q2 Release {q2-release}

**Salesforce Package Consolidation**

* We're merging all Salesforce packages into a single, comprehensive package for an improved user experience and simplified usage. The V1, V2_EXT, and Reporting packages will be retired next quarter. The new package combines all previous features, allowing for more efficient tracking and deeper customer insights.
* Customers who already have the V2 package installed must update it to the new consolidated version. 
* We've added two new fields to enhance your reporting capabilities:
     * form_name: Now available in BT/BAT objects, this field enables users to create reports based on form names.
     * user_touchpoint_id: This field enables users to create reports with unique user touchpoint counts. 
* [This article](/help/configuration-and-setup/marketo-measure-and-salesforce/salesforce-package-consolidation.md){target="_blank"} includes guides on recreating reports and dashboards from the legacy Reporting packages.

**Salesforce API Version Updates**

* All Salesforce API versions of Apex classes, including the UserActivityContext class, are updated to supported versions. (31.0 through 57.0)

**New Package Installation**

* The new consolidated package installation link [can be found here](https://login.salesforce.com/packaging/installPackage.apexp?p0=04t1P000000VY6Z){target="_blank"}

### What's coming? {#whats-coming}

**Changes in IP Address Storage**

* We will no longer store IP addresses in our system per privacy considerations. We will continue identifying and storing the geo-location of the IP address, but the format will change (e.g., "United States" to "US").
