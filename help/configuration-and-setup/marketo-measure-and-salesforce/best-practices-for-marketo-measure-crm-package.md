---
description: Best Practices for [!DNL Marketo Measure] CRM Package - [!DNL Marketo Measure]
title: Best Practices for [!DNL Marketo Measure] CRM Package
exl-id: 97ce0ff3-8aa5-4789-9ee0-25d68c001def
feature: Salesforce
---
# Best Practices for [!DNL Marketo Measure] CRM Package {#best-practices-for-marketo-measure-crm-package}

>[!NOTE]
>
>You may see instructions specifying "[!DNL Marketo Measure]" in the documentation, but still see "Bizible" in your CRM. That is updated and the rebranding will be reflected in your CRM soon.

## Overview {#overview}

[!DNL Marketo Measure] integrates with both [!DNL Salesforce] and [!DNL Microsoft Dynamics], this document focuses on the [!DNL Marketo Measure] best practices for the CRM packages designed for [!DNL Salesforce].

During implementation the two following packages would have been installed into your [!DNL Salesforce] instance.

Base Package: This is the base package which includes custom objects and fields. It is recommended installing within Production for all users.
Dashboard Extension Package: This is our Dashboard Extension Package, which contains three pre-built dashboards. We recommend installing within Production for all users. This is optional but we encourage customers to install.

These packages enable your [!DNL Marketo Measure] users to easily access touchpoint data throughout their [!DNL Salesforce] instance. Confirming that you have these packages configured correctly is key to verifying that page layouts, permission sets, reports, and dashboards are presenting to your [!DNL Marketo Measure] users as expected.

## Best Practice {#best-practice}

When implementing and managing your [!DNL Marketo Measure] [!DNL Salesforce] Package, keep the following best practices in mind.

* Confirm that every necessary team member has access to the [!DNL Marketo Measure] report folders. There should be 1-3 [!DNL Marketo Measure] folders (these are explained below). To open up access, the person who installed the packages must share the report folders with the appropriate users or roles.
   * **Buyer Touchpoint Reports** - available to everyone
   * **[!DNL Marketo Measure] Account Based Marketing Reports** - reports will only be populated to customers Tier 2 and above
   * **Buyer Touchpoint Dashboards** - available to everyone, though this package is optional.

## Best Practice for Maintenance {#best-practice-for-maintenance}

While the setup of your CRM Package is covered during initial implementation, it is recommended that you review the setup of your CRM package once a year. This review confirms that all page layouts are set up correctly and that all appropriate team members have access to [!DNL Marketo Measure] reports and dashboards.

Other reasons to that might trigger a review...

* Addition of new team members
* Updates to your [!DNL Salesforce] page layouts
* Migration for [!DNL Salesforce] Classic to Lightening
* Upgrades to your [!DNL Marketo Measure] contract
* Check that you have the most recent version of the Buyer Touchpoints Package installed in [!DNL Salesforce]

>[!NOTE]
>
>When you disable Marketo Measure exporting data to Salesforce, it will not delete any existing data. To remove it, follow the steps in [this Salesforce help article](https://help.salesforce.com/s/articleView?language=en_US&id=sf.c360_a_delete_data_stream_records.htm&type=5){target="_blank"}.

>[!MORELIKETHIS]
>
>* [Update Buyer Touchpoint Package](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-salesforce-package-installation-and-set-up.md)
>* [[!DNL Marketo Measure] Permission Sets](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md)
>* [Sharing Reports and Dashboards Folder](https://help.salesforce.com/s/articleView?language=en_US&id=analytics_share_folder.htm&type=0)
>* [Connect Marketo Measure to Salesforce](/help/configuration-and-setup/marketo-measure-and-salesforce/connect-marketo-measure-to-salesforce.md)
