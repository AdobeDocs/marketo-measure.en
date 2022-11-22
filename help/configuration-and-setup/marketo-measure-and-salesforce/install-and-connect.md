---
unique-page-id: 18874580
description: Install and Connect - [!DNL Marketo Measure] - Product Documentation
title: Install and Connect
exl-id: 9be8d3fa-1045-4e41-bc2e-5b9d4d3513ae
---
# Install and Connect {#install-and-connect}

This article provides an overview of how to connect your [!DNL Salesforce] account to your [!DNL Marketo Measure] account.

## Connecting [!DNL Marketo Measure] with [!DNL Salesforce] {#connecting-marketo-measure-with-salesforce}

1. Use an incognito browser to log in to [!DNL Marketo Measure].

1. In the menu bar at the top of the screen, navigate to **[!UICONTROL My Account]** and click the [!UICONTROL Settings] option.

1. In the column of setting options on the left, click [!UICONTROL Connections] located under the [!UICONTROL Integrations] section.

   ![](assets/1.png)

1. Under the CRM section in Connections, click **[!UICONTROL Set Up New CRM Connection]**.

   ![](assets/2.png)

1. A pop-up window will appear asking you to Select CRM connection. Click the [!UICONTROL Connect] button next to the [!DNL Salesforce] logo.

   ![](assets/3.png)

1. A final pop-up window will appear, asking you for your [!DNL Salesforce] credentials, sandbox or production. Enter your information and click **[!UICONTROL Authorize]** to connect the account to [!DNL Marketo Measure].

>[!NOTE]
>
>[!DNL Marketo Measure] can only be connected to one [!DNL Salesforce] instance at a time.
>
>* A [!DNL Marketo] Measure instance can be connected to a SFDC Sandbox Instance to test the integration before switching the connection to your SFDC Production Instance.
>* If you test first with a SFDC Sandbox, we highly recommend you test with one which is an exact replica of your SFDC production instance in terms of fields on the Lead, Contact, Account, Opportunity, Campaign and Case objects. If you have any active APEX triggers in production which fire on updates to the Lead, Contact, Account, Opportunity, Campaign and Case objects, you should try to have them active in your sandbox.
>* Once you are done with testing, you will update your [!DNL Marketo Measure] account to point at your Production [!DNL Salesforce] (instead of Sandbox [!DNL Salesforce]). Due to the way the integration was built, once a [!DNL Marketo Measure] account is connected to Production [!DNL Salesforce], you cannot go "backwards" and connect to a Sandbox [!DNL Salesforce] org.

