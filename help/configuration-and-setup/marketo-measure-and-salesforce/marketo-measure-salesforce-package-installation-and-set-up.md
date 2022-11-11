---
description: Marketo Measure Salesforce Package​ Installation and Set Up - Marketo Measure - Product Documentation
title: Marketo Measure Salesforce Package​ Installation and Set Up
hide: yes
hidefromtoc: yes
exl-id: ed58bc1e-cfb0-48db-aa53-96204e12de2e
---
# Marketo Measure Salesforce Package​ Installation and Set Up {#marketo-measure-salesforce-package​-installation-and-set-up}

Before you install the Marketo Measure Salesforce base package, you need to determine if you will be first installing it in a Salesforce sandbox before moving to your Salesforce production instance. 

>[!NOTE]
>
>Once your Marketo Measure account is connected to a Salesforce production instance, you cannot move backwards and connect to a sandbox. Also, a Marketo Measure account can only be connected to one Salesforce production instance. 

The Marketo Measure Base Package contains: 

* 7 Custom Marketo Measure Objects 
* Custom Marketo Measure Fields 
* 25 Stock Reports 

Marketo Measure is able to read standard Salesforce Objects, Fields, and Records, however, Marketo Measure will never update or push data to them. All the data collected by the Marketo Measure Javascript will be surfaced in the Marketo Measure Custom Objects and Fields. 

Follow the steps below to install the Marketo Measure Salesforce base package.

1. Using an incognito browser, go to the [Salesforce Appexchange](https://appexchange.salesforce.com/){target="_blank"} and log in.

1. Install in the Marketo Measure package in sandbox or production.

1. Log in to Salesforce as an Admin.

1. Select **Install for All Users**.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-1.png)

1. Once the installation is complete, you can view it.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-2.png)

After you've completed the installation, you can update your [Salesforce page layouts](/help/configuration-and-setup/marketo-measure-and-salesforce/page-layout-instructions.md){target="_blank"} with the Marketo Measure fields if desired. 

>[!NOTE]
>
>Read about the Marketo Measure Permissions sets created and [how they will be used](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md){target="_blank"}. 

## Install Marketo Measure Dashboard Package​ {#install-marketo-measure-dashboard-package}

The Dashboard Extension Package contains three pre-built dashboards. We recommend installing within Production for all users.​ 

1. Install the package from the [Salesforce Appexchange](https://appexchange.salesforce.com/){target="_blank"}.

1. Select **Install for All Users**.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-3.png)

## Creating a Marketo Measure Profile and User {#creating-a-marketo-measure-profile-and-user}

Marketo Measure sends and receives data through a connected Salesforce user within the Marketo Measure app. 

In order to push touchpoint data to your Salesforce instance, the connected user must have access to Marketo Measure custom objects (e.g., Buyer Touchpoint and Buyer Attribution Touchpoint) as well as standard Salesforce objects such as Leads and Contacts. 

Create a Marketo measure profile to ensure you won't run into validation errors when pushing data to Salesforce.  

Step 1: Create a specific Marketo measure profile

1. Assign the following permissions: 

* "Marketo measure Administrator Permission Set" 
   * The managed permission set gives an SFDC admin the ability to create, read, write, delete records from Marketo measure objects. 
* "View and Edit Converted Leads Permission Set" 
   * This allows Marketo measure to decorate leads after they have been converted to contacts. If this permission set is not enabled there can be significant data tracking gaps. 

>[!NOTE]
>
>This profile can be a clone of a System Admin profile.

Step 2: Create a dedicated Marketo measure user so you can track the impact of Marketo measure on your Salesforce instance

1. Assign the new Marketo measure Profile to that User.

1. Enable "Marketing User" as a user level permission.

* The Marketing User checkbox allows the user to create campaigns and use the Campaign Import Wizards. If this option isn't selected, the user can only view campaigns and advanced campaign setup, edit the Campaign History for a single lead or contact, and run campaign reports. Marketo measure needs to ability to read and write to the campaign object. 
 
Step 3: Exclude this Profile from all triggers, workflows, and processes

Step 4: Log-in to your Marketo measure Account and re-authorize the Salesforce connection with the new user 

1. Go to apps.bizible.com and log in with the new user production Salesforce credentials.

1. Select **Settings** within the **My Account** drop-down.

1. Select **Connections** within the **Integrations** grouping.

1. Click the Key Icon to the right of the current connected Salesforce connection and select to **Re-authorize with Production**. Log in with the new user credentials again (if prompted).
