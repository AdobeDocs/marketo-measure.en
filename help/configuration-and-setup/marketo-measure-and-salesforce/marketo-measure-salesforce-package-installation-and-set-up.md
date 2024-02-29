---
description: "[!DNL Marketo Measure] Salesforce Package Installation and Set Up - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] [!DNL Salesforce] Package Installation and Set Up"
exl-id: ed58bc1e-cfb0-48db-aa53-96204e12de2e
feature: Installation, Salesforce
---
# [!DNL Marketo Measure] Salesforce Package Installation and Set Up {#marketo-measure-salesforce-package-installation-and-set-up}

Before you install the [!DNL Marketo Measure] [!DNL Salesforce] base package, you must determine if you are first installing it in a [!DNL Salesforce] sandbox before moving to your Salesforce production instance.

>[!NOTE]
>
>Once your [!DNL Marketo Measure] account is connected to a [!DNL Salesforce] production instance, you cannot move backwards and connect to a sandbox. Also, a [!DNL Marketo Measure] account can only be connected to one [!DNL Salesforce] production instance.

The [!DNL Marketo Measure] Base Package contains:

* 7 Custom [!DNL Marketo Measure] Objects
* Custom [!DNL Marketo Measure] Fields
* 25 [!DNL Stock] Reports

[!DNL Marketo Measure] is able to read standard [!DNL Salesforce] Objects, Fields, and Records, however, [!DNL Marketo Measure] will never update or push data to them. All the data collected by the [!DNL Marketo Measure] JavaScript will be surfaced in the [!DNL Marketo Measure] Custom Objects and Fields.

Follow the steps below to install the [!DNL Marketo Measure Salesforce] base package.

1. Using an incognito browser, go to the [Salesforce AppExchange](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3000000B3KLuEAN){target="_blank"} and log in.

1. Install in the [!DNL Marketo Measure] package in sandbox or production.

1. Log in to [!DNL Salesforce] as an Admin.

1. Select **[!UICONTROL Install] for All Users**.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-1.png)

1. Once the installation is complete, you can view it.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-2.png)

After you've completed the installation, you can update your [[!DNL Salesforce] page layouts](/help/configuration-and-setup/marketo-measure-and-salesforce/page-layout-instructions.md){target="_blank"} with the [!DNL Marketo Measure] fields if desired.

>[!NOTE]
>
>Read about the [!DNL Marketo Measure] Permissions sets created and [how they are used](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md){target="_blank"}.

## Creating a [!DNL Marketo Measure] Profile and User {#creating-a-marketo-measure-profile-and-user}

[!DNL Marketo Measure] sends and receives data through a connected [!DNL Salesforce] user within the [!DNL Marketo Measure] app.

To push touchpoint data to your [!DNL Salesforce] instance, the connected user must have access to [!DNL Marketo Measure] custom objects (for example, Buyer Touchpoint and Buyer Attribution Touchpoint) as well as standard [!DNL Salesforce] objects such as Leads and Contacts.

Create a [!DNL Marketo Measure] profile to ensure you won't run into validation errors when pushing data to Salesforce.

Step 1: Create a specific [!DNL Marketo Measure] profile

1. Assign the following permissions:

* "[!DNL Marketo Measure] Administrator Permission Set"
   * The managed permission set gives an SFDC admin the ability to create, read, write, delete records from [!DNL Marketo Measure] objects.
* "View and Edit Converted Leads Permission Set"
   * This allows [!DNL Marketo Measure] to decorate leads after they have been converted to contacts. If this permission set is not enabled, there can be significant data tracking gaps.

>[!NOTE]
>
>This profile can be a clone of a System Admin profile.

Step 2: Create a dedicated [!DNL Marketo Measure] user so you can track the impact of [!DNL Marketo Measure] on your [!DNL Salesforce] instance

1. Assign the new [!DNL Marketo Measure] Profile to that User.

1. Enable "Marketing User" as a user level permission.

* The [!UICONTROL Marketing User] checkbox allows the user to create campaigns and use the Campaign Import Wizards. If this option is not selected, the user can only view campaigns and advanced campaign setup, edit the Campaign History for a single lead or contact, and run campaign reports. [!DNL Marketo Measure] must ability to read and write to the campaign object.

Step 3: Exclude this Profile from all triggers, workflows, and processes

Step 4: Log in to your [!DNL Marketo Measure] Account and reauthorize the [!DNL Salesforce] connection with the new user

1. Go to apps.bizible.com and log in with the new user production [!DNL Salesforce] credentials.

1. Select **[!UICONTROL Settings]** within the **[!UICONTROL My Account]** drop-down.

1. Select **[!UICONTROL Connections]** within the **[!UICONTROL Integrations]** grouping.

1. Click the Key Icon to the right of the current connected [!DNL Salesforce] connection and select to **Reauthorize with Production**. Log in with the new user credentials again (if prompted).

>[!MORELIKETHIS]
>
>[Adobe Admin Console Setup](/help/configuration-and-setup/getting-started-with-marketo-measure/adobe-admin-console-setup.md){target="_blank"}
