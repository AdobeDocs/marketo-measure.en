---
unique-page-id: 42762762
description: Set Up Marketo Connection - [!DNL Marketo Measure]
title: Set Up Marketo Connection
exl-id: 11660539-1cc5-4768-8f22-d6f7cd0b94f3
feature: Integration
TQID: 'https://experienceleague.adobe.com/IQhZzu6iqS-5BdooPRA6-A8BoJtQ936NRFJHPGu3Xp4'
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: c8f57308-7e33-4e41-a385-b55041c78939
    internal-label: Integrations
  - id: 7da342c5-06ee-5869-b3e8-b73d5bf75a9d
    internal-label: Integration
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
---
# Set Up Marketo Connection {#set-up-marketo-connection}

Here's how to set up your connection to Marketo.

>[!PREREQUISITES]
>
>[Create an API Only User role](https://experienceleague.adobe.com/docs/marketo/using/product-docs/administration/users-and-roles/create-an-api-only-user.html){target="_blank"} for the [!DNL Marketo Measure]/Marketo Engage connection.

1. In [!DNL Marketo Measure], click the **[!UICONTROL My Account]** drop-down and select **[!UICONTROL Settings]**.

   ![](assets/set-up-marketo-connection-1.png)

1. Under [!UICONTROL Integrations], click **[!UICONTROL Connections]**.

   ![](assets/set-up-marketo-connection-2.png)

1. Click **[!UICONTROL Set Up New CRM Connection]**.

   ![](assets/set-up-marketo-connection-3.png)

1. Click the **[!UICONTROL Connect]** button next to Marketo.

   ![](assets/set-up-marketo-connection-4.png)

1. In a new tab, log in to your Marketo Engage account. Go to **Admin** > **Web Services**. Scroll down to REST API. Highlight and save the Endpoint and Identity Service URL. You need them in the following steps.

   ![](assets/set-up-marketo-connection-5.png)

1. Still in Marketo Engage, select **LaunchPoint** in the tree on the left. Find the custom service that you want to connect to Marketo Measure and click **View Details**.

   ![](assets/set-up-marketo-connection-6.png)

1. Highlight and save the Client ID and Client Secret. Click **Close**.

   ![](assets/set-up-marketo-connection-7.png)

1. Back in [!DNL Marketo Measure], populate the fields with the data you collected.

   ![](assets/set-up-marketo-connection-8.png)

1. After you enter the values, click **[!UICONTROL Authenticate]**. Your Marketo Engage account is connected to [!DNL Marketo Measure].

   ![](assets/set-up-marketo-connection-9.png)

   >[!NOTE]
   >
   >[!DNL Marketo Measure] makes calls to the Marketo API on your behalf without consuming any of your Marketo API limits, so there's no need to worry about caps and credit allocation with other integrations.
