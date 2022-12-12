---
description: Best Practices for [!DNL Marketo Measure] CRM Package - [!DNL Marketo Measure] - Product Documentation
title: Best Practices for [!DNL Marketo Measure] CRM Package
exl-id: 97ce0ff3-8aa5-4789-9ee0-25d68c001def
---
# Best Practices for [!DNL Marketo Measure] CRM Package {#best-practices-for-marketo-measure-crm-package}

>[!NOTE]
>
>You may see instructions specifying "[!DNL Marketo Measure]" in our documentation, but still see "Bizible" in your CRM. We are working to have that updated and the rebranding will be reflected in your CRM soon.

## Overview {#overview}

[!DNL Marketo Measure] integrates with both [!DNL Salesforce] and [!DNL Microsoft Dynamics], this document will focus on the [!DNL Marketo Measure] best practices for the CRM packages designed for [!DNL Salesforce].

During implementation the two following packages would have been installed into your [!DNL Salesforce] instance.

Base Package: This is our base package which includes our custom objects and fields. We recommend installing within Production for all users.
Dashboard Extension Package: This is our Dashboard Extension Package, which contains 3 pre-built dashboards. We recommend installing within Production for all users. This is optional but we encourage customers to install.

These packages enable your [!DNL Marketo Measure] users to easily access touchpoint data throughout their [!DNL Salesforce] instance. Confirming that you have these packages configured correctly will be key to verifying that page layouts, permission sets and reports and dashboards are presenting to your [!DNL Marketo Measure] users as expected.

## Best Practice {#best-practice}

When it comes to implementing and managing your [!DNL Marketo Measure] [!DNL Salesforce] Package, keep the following best practices in mind.

* Confirm every necessary team member has access to the [!DNL Marketo] Measure report folders. There should be 1-3 [!DNL Marketo Measure] folders (these are explained below). To open up access, the person who installed the package(s) needs to share the report folders with the appropriate users or roles.
   * **Buyer Touchpoint Reports** - available to everyone
   * **[!DNL Marketo] Measure Account Based Marketing Reports** - reports will only be populated to customers Tier 2 and above
   * **Buyer Touchpoint Dashboards** - available to everyone, though this package is optional.

## Best Practice for Maintenance {#best-practice-for-maintenance}

While the setup of your CRM Package is covered during initial implementation, we recommend that you review the setup of your CRM package once a year. This review will confirm that all page layouts are set up correctly and that all appropriate team members have access to [!DNL Marketo] Measure reports and dashboards.

Other reasons to that might trigger a review...

* Addition of new team members
* Updates to you [!DNL Salesforce] page layouts
* Migration for [!DNL Salesforce] Classic to Lightening
* Upgrades to your [!DNL Marketo Measure] contract
* Check that you have the most recent version of our Buyer Touchpoints Package installed in [!DNL Salesforce]

>[!MORELIKETHIS]
>
>* [Update Buyer Touchpoint Package](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-salesforce-package-installation-and-set-up.md)
>* [[!DNL Marketo Measure] Permission Sets](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md)
>* [Sharing Reports and Dashboards Folder](https://help.salesforce.com/articleView?id=analytics_share_folder.htm&type=0)
>* [Connect Marketo Measure to Salesforce](/help/configuration-and-setup/marketo-measure-and-salesforce/connect-marketo-measure-to-salesforce.md)
