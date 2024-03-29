---
unique-page-id: 18874694
description: Salesforce Sandbox to Production Migration - [!DNL Marketo Measure]
title: Salesforce Sandbox to Production Migration
exl-id: b2b71c4a-f192-43ce-a27e-cbd0ec3cf008
feature: Salesforce
---
# Salesforce Sandbox to Production Migration {#salesforce-sandbox-to-production-migration}

If you chose to test [!DNL Marketo Measure] in a [!DNL Salesforce] Sandbox environment, follow these instructions to migrate to Production once you are ready. The following instructions assume that you have already downloaded the [!DNL Marketo Measure] package into your Sandbox org, performed the necessary testing and are ready to push [!DNL Marketo Measure] to Production.

## Step 1: Install the [!DNL Marketo Measure] Package into Your Production [!DNL Salesforce] Instance

* Install the [!DNL Marketo Measure] package into Production with the "[!UICONTROL All Users]" setting

   * [Base Package](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3000000B3KLuEAN){target="_blank"}

* For more information about the [!DNL Marketo Measure] relationship with [!DNL Salesforce], look at [this article](/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md)
* A bit of [!DNL Salesforce] configuration is necessary. The specific action items are outlined below in [Step 4 below](#salesforce-configuration)

## Step 2: Delete the Current Sandbox CRM Connection in [!DNL Marketo Measure] App {#delete-the-current-sandbox-crm-connection-in-marketo-measure-app}

* Log in to the [!DNL Marketo Measure] application at experience.adobe.com/marketo-measure
* Navigate to My Account >[!UICONTROL Settings] >[!UICONTROL Connections]
* Click the trash icon next to your SFDC connection to delete
* You are prompted to confirm your deletion. Make sure to read over the prompt carefully and understand the consequences of the deletion

   ![](assets/salesforce-sandbox-to-production-migration-1.png)

   * Type the name of the Business as prompted in the confirmation model and click "I understand the consequences, delete this connection"
* This triggers the deletion process and will take some time to finish

## Step 3: Connect the Production CRM Instance in [!DNL Marketo Measure] App {#connect-the-production-crm-instance-in-marketo-measure-app}

* Log in to the [!DNL Marketo Measure] application at experience.adobe.com/marketo-measure
* Navigate to [!UICONTROL My Account] >[!UICONTROL Settings] > [!UICONTROL Connections]
* Once the deletion of the Sandbox connection has been successfully deleted the connection disappears from the page, otherwise the connection will still be present with a status of "Deletion in progress"
* Click "[!UICONTROL Set up New CRM connection]"
* In the "[!UICONTROL Select CRM Connection]" modal dialog, click the "[!UICONTROL Connect]" Action next to the [!DNL Salesforce] Platform, Select the "[!UICONTROL Production]" option
* You are prompted for your credentials, be sure to enter Production login details

## Step 4: Salesforce Configuration {#salesforce-configuration}

[Page Layouts](/help/configuration-and-setup/marketo-measure-and-salesforce/page-layout-instructions.md)

[Permission Sets](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md)

[Sharing reports](https://help.salesforce.com/s/articleView?language=en_US&id=analytics_share_folder.htm&type=0){target="_blank"}

[Hiding unnecessary report types](/help/configuration-and-setup/marketo-measure-and-salesforce/hiding-unnecessary-report-types.md)

[Custom workflow if applicable](/help/advanced-marketo-measure-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md)
