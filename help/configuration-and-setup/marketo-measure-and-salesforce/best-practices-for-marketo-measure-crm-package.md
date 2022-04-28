---
description: Best Practices for Marketo Measure CRM Package - Marketo Measure - Product Documentation
title: Best Practices for Marketo Measure CRM Package
exl-id: 97ce0ff3-8aa5-4789-9ee0-25d68c001def
---
# Best Practices for Marketo Measure CRM Package {#best-practices-for-marketo-measure-crm-package}

## Overview {#overview}

Marketo Measure integrates with both Salesforce and Microsoft Dynamics, this document will focus on the Marketo Measure best practices for the CRM packages designed for Salesforce.

During implementation the two following packages would have been installed into your Salesforce instance.

Base Package: This is our base package which includes our custom objects and fields. We recommend installing within Production for all users.
Dashboard Extension Package: This is our Dashboard Extension Package, which contains 3 pre-built dashboards. We recommend installing within Production for all users. This is optional but we encourage customers to install.

These packages enable your Marketo Measure users to easily access touchpoint data throughout their Salesforce instance. Confirming that you have these packages configured correctly will be key to verifying that page layouts, permission sets and reports and dashboards are presenting to your Marketo Measure users as expected.

## Best Practice {#best-practice}

When it comes to implementing and managing your Marketo Measure CRM Package, keep the following best practices in mind.

* Check that you have the most recent version of our Buyer Touchpoints Package (6.15) installed in Salesforce
* Confirm every necessary team member has access to the Marketo Measure report folders. There should be 1-3 Marketo Measure folders (these are explained below). To open up access, the person who installed the package(s) needs to share the report folders with the appropriate users or roles.
   * **Buyer Touchpoint Reports** – available to everyone
   * **Marketo Measure Account Based Marketing Reports** – reports will only be populated to customers Tier 2 and above
   * **Buyer Touchpoint Dashboards** – available to everyone, though this package is optional.

## Best Practice for Maintenance {#best-practice-for-maintenance}

While the setup of your CRM Package is covered during initial implementation, we recommend that you review the setup of your CRM package once a year. This review will confirm that all page layouts are set up correctly and that all appropriate team members have access to Marketo Measure reports and dashboards.

Other reasons to that might trigger a review...

* Addition of new team members
* Updates to you Salesforce page layouts
* Migration for Salesforce Classic to Lightening
* Upgrades to your Marketo Measure contract

>[!MORELIKETHIS]
>
>* [Update Buyer Touchpoint Package](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-installation-guide.md)
>* [Marketo Measure Permission Sets](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md)
>* [Sharing Reports and Dashboards Folder](https://help.salesforce.com/articleView?id=analytics_share_folder.htm&type=0)
>* [Installing and Connecting Marketo Measure](/help/configuration-and-setup/marketo-measure-and-salesforce/install-and-connect.md)
