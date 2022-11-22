---
unique-page-id: 18874698
description: Creating a [!DNL Marketo Measure] Profile - [!DNL Marketo Measure] - Product Documentation
title: Creating a [!DNL Marketo Measure] Profile
exl-id: dab2e2cb-fbd3-464a-9bd7-e9bf153d9848
---
# Creating a [!DNL Marketo] Measure Profile {#creating-a-marketo-measure-profile}

Learn how to create a [!DNL Marketo Measure] profile. Creating a [!DNL Marketo Measure] profile ensures we won't run into validation errors when pushing data to your CRM.

1. Create a specific [!DNL Marketo] Measure profile:

   * Assign the [!DNL Marketo Measure] Administrator Permission Set
   * Enable the permission to View and Edit Converted Leads

   >[!NOTE]
   >
   >This profile can be a clone of a [!DNL System Admin] profile

1. Created a dedicated [!DNL Marketo Measure] user:

   * Assign the new [!DNL Marketo Measure] Profile to that User
   * Enable "Marketing User" as a user level permission

1. Exclude this Profile from all triggers, workflows, and processes.
1. Log in to your [!DNL Marketo Measure] Account and re-authorize the [!DNL Salesforce] connection with the new user:

   * Go to [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} and log in with the new user production Salesforce credentials
   * Select "[!UICONTROL Settings]" within the "[!UICONTROL My Account]" drop-down
   * Select "[!UICONTROL Connections]" within the "[!UICONTROL Integrations]" grouping
   * Click the Key Icon to the right of the current connected [!DNL Salesforce] connection and select to Re-authorize with Production. Then log in with the new user credentials again if prompted

   Done!

   If you have any questions around creating a dedicated [!DNL Marketo Measure] profile, please reach out to your customer success manager or [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
