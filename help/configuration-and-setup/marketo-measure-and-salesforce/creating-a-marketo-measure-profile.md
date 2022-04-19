---
unique-page-id: 18874698
description: Creating a Marketo Measure Profile - Measure - Product Documentation
title: Creating a Marketo Measure Profile
exl-id: dab2e2cb-fbd3-464a-9bd7-e9bf153d9848
---
# Creating a Marketo Measure Profile {#creating-a-marketo-measure-profile}

Learn how to create a Bizible profile. Creating a Bizible profile ensures we won’t run into validation errors when pushing data to your CRM.

1. Create a specific Bizible profile:

    * Assign the Bizible Administrator Permission Set
    * Enable the permission to View and Edit Converted Leads

   >[!NOTE]
   >
   >This profile can be a clone of a System Admin profile

1. Created a dedicated Bizible user:

    * Assign the new Bizible Profile to that User
    * Enable "Marketing User" as a user level permission

1. Exclude this Profile from all triggers, workflows, and processes.
1. Log-in to your Bizible Account and re-authorize the Salesforce connection with the new user:

    * Go to [apps.bizible.com](http://apps.bizible.com) and log-in with the new user production Salesforce credentials
    * Select "Settings" within the "My Account" drop-down
    * Select "Connections" within the "Integrations" grouping
    * Click the Key Icon to the right of the current connected Salesforce connection and select to Re-authorize with Production. Then log-in with the new user credentials again if prompted

   Done!  
  
   If you have any questions around creating a dedicated Bizible profile, please reach out to your success manager or support@bizible.com.
