---
unique-page-id: 18874580
description: Connect Marketo Measure to Salesforce - [!DNL Marketo Measure]
title: Connect Marketo Measure to Salesforce
exl-id: 9be8d3fa-1045-4e41-bc2e-5b9d4d3513ae
feature: Salesforce
---
# Connect Marketo Measure to Salesforce {#connect-marketo-measure-to-salesforce}

This article provides an overview of how to connect your [!DNL Salesforce] account to your [!DNL Marketo Measure] account.

## Connecting [!DNL Marketo Measure] with [!DNL Salesforce] {#connecting-marketo-measure-with-salesforce}

1. Use an incognito browser to log in to [!DNL Marketo Measure].

1. In the menu bar at the top of the screen, navigate to **[!UICONTROL My Account]** and click the **[!UICONTROL Settings]** option.

1. In the column of setting options on the left, click **[!UICONTROL Connections]** located under the [!UICONTROL Integrations] section.

   ![](assets/connect-marketo-measure-to-salesforce-1.png)

1. Under the CRM section in Connections, click **[!UICONTROL Set Up New CRM Connection]**.

   ![](assets/connect-marketo-measure-to-salesforce-2.png)

1. A pop-up window appears asking you to Select CRM connection. Click **[!UICONTROL Connect]** next to the [!DNL Salesforce] logo.

   ![](assets/connect-marketo-measure-to-salesforce-3.png)

1. A final pop-up window appears, asking you for your [!DNL Salesforce] credentials, sandbox, or production. Enter your information and click **[!UICONTROL Authorize]** to connect the account to [!DNL Marketo Measure].

>[!NOTE]
>
>[!DNL Marketo Measure] can only be connected to one [!DNL Salesforce] instance at a time.
>
>* A [!DNL Marketo Measure] instance can be connected to an SFDC Sandbox Instance to test the integration before switching the connection to your SFDC Production Instance.
>* If you test first with an SFDC Sandbox, we highly recommend you test with one which is an exact replica of your SFDC production instance in terms of fields on the Lead, Contact, Account, Opportunity, Campaign, and Case objects. If you have any active APEX triggers in production which fire on updates to the Lead, Contact, Account, Opportunity, Campaign and Case objects, you should try to have them active in your sandbox.
>* Once you are done with testing, you update your [!DNL Marketo Measure] account to point at your Production [!DNL Salesforce] (instead of Sandbox [!DNL Salesforce]). Due to the way the integration was built, once a [!DNL Marketo Measure] account is connected to Production [!DNL Salesforce], you cannot go "backwards" and connect to a Sandbox [!DNL Salesforce] org.

## API Credits Usage {#api-credits-usage}

Marketo Measure employs a CRM integration task to interface with a client's Salesforce through an Integrated User. All data exchanges via this user uses Salesforce API credits. You have the capability to allocate a credit quota to an integration user, which serves to regulate excessive API calls. This quota or limit is reset every 24 hours.

You can access this limit in Marketo Measure via: **My Account** > **Settings** > **CRM** > **General** > **Daily CRM API limit**, and can configure it for your tenants.

   ![](assets/connect-marketo-measure-to-salesforce-4.png)

### Setting a Limit for API Credits {#setting-a-limit-for-api-credits}

1. Navigate to **My Account** > **Settings**.

1. Under CRM, click **General**. You see the **Daily CRM API limit** option.

1. Click the Lock icon to edit.

   ![](assets/connect-marketo-measure-to-salesforce-5.png)

1. Enter a desired limit equal to or greater than 100,000. Click **Save** when done.

   ![](assets/connect-marketo-measure-to-salesforce-6.png)

>[!NOTE]
>
>To increase available Salesforce API credits for your connected solution, contact your Salesforce admin and reference [this Salesforce document](https://developer.salesforce.com/docs/atlas.en-us.salesforce_app_limits_cheatsheet.meta/salesforce_app_limits_cheatsheet/salesforce_app_limits_platform_api.htm){target="_blank"}.

>[!MORELIKETHIS]
>
>[Error Notifications](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"}
