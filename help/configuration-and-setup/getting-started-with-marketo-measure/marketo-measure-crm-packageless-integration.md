---
unique-page-id: 37356027
description: "[!DNL Marketo Measure] CRM Packageless Integration - [!DNL Marketo Measure] - Product Documentation"
title: "[!DNL Marketo Measure] CRM Packageless Integration"
exl-id: a4f31d82-63ec-4bb2-bc8b-d3495e61af4f
feature: Integration
---
# [!DNL Marketo Measure] CRM Packageless Integration {#marketo-measure-crm-packageless-integration}

Not all Marketing teams want (or have access) to run marketing reporting out of the CRM, whether it's because of limited access, CRM ownership, longer time to value, or legal implications. Going down the path of [!DNL Marketo Measure] Quick Start gives you the ability to effectively implement and run [!DNL Marketo Measure] with as little reliance on the CRM as possible.

## Standard [!DNL Marketo Measure] Installation {#standard-marketo-measure-installation}

Through the standard [!DNL Marketo Measure] installation, you're required to install a [!DNL Salesforce] Package or a [!DNL Microsoft Dynamics] Managed Solution. The installation includes custom objects/entities and custom fields that are added to the CRM that [!DNL Marketo Measure] can then write data to.

A packageless integration with [!DNL Marketo Measure] is for customers who don't want to create custom objects/entities or custom fields in your CRM. It's also a good option for customers who are using an external data warehouse.

## Permissions {#permissions}

A [!DNL Marketo Measure] CRM packageless integration still requires access to standard CRM objects such as Leads and Contacts. We strongly recommend a dedicated user serve as the connected user, as they will have the proper data access privileges.

To ensure that all data is properly pulling from your CRM, we require the following security and accessibility settings: View All Data for the Profile of the dedicated user. This permission set gives [!DNL Marketo Measure] the access needed to download data from standard objects. This permission set is at profile level.

## Setup up your Identity Provider and Data Connections {#setup-your-identity-provider-and-data-connections}

In the guides below, skip the steps to install the [!DNL Salesforce] package or [!DNL Microsoft Dynamics] Managed Solution and follow only the permissions and integration instructions.

[!DNL Salesforce] customers, click [here](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-salesforce-package-installation-and-set-up.md).

[!DNL Microsoft Dynamics] customers, click [here](/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/microsoft-dynamics-crm-installation-guide.md).

Once you complete the above steps, you are good to go. If you run into any issues along the way, please don't hesitate to reach out to your [!DNL Marketo Measure] representative or [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

>[!NOTE]
>
>If you start with the [!DNL Marketo Measure] CRM packageless integration you will be able to install the Salesforce package or Microsoft Dynamics Managed Solution later.
