---
description: "Set Up Marketo Connection guidance for Marketo Measure users"
title: Set Up Marketo Connection
exl-id: 11660539-1cc5-4768-8f22-d6f7cd0b94f3
feature: Integration
---
# Set Up Marketo Connection {#set-up-marketo-connection}

Here's how to set up your connection to Marketo.

>[!PREREQUISITES]
>
>[Create an API Only User role](https://experienceleague.adobe.com/docs/marketo/using/product-docs/administration/users-and-roles/create-an-api-only-user.html) for the [!DNL Marketo Measure]/Marketo Engage connection.

1. In [!DNL Marketo Measure], click the **[!UICONTROL My Account]** drop-down and select **[!UICONTROL Settings]**.

   ![1. In Marketo Measure, click the My Account drop-down and](assets/set-connection-7.png)

1. Under [!UICONTROL Integrations], click **[!UICONTROL Connections]**.

   ![1. Under Integrations, click Connections.](assets/set-connection-8.png)

1. Click **[!UICONTROL Set Up New CRM Connection]**.

   ![1. Click Set Up New CRM Connection.](assets/set-connection-9.png)

1. Click the **[!UICONTROL Connect]** button next to Marketo.

   ![1. Click the Connect button next to Marketo.](assets/set-connection-5.png)

1. In a new tab, log in to your Marketo Engage account. Go to **Admin** > **Web Services**. Scroll down to REST API. Highlight and save the Endpoint and Identity Service URL. You need them in the following steps.

   ![1. In a new tab, log in to your Marketo Engage account.](assets/set-connection-6.png)

1. Still in Marketo Engage, select **LaunchPoint** in the tree on the left. Find the custom service that you want to connect to Marketo Measure and click **View Details**.

   ![1. Still in Marketo Engage, select LaunchPoint in the tree on the](assets/set-connection-4.png)

1. Highlight and save the Client ID and Client Secret. Click **Close**.

   ![1. Highlight and save the Client ID and Client Secret. Click Close.](assets/set-connection-3.png)

1. Back in [!DNL Marketo Measure], populate the fields with the data you collected.

   ![1. Back in Marketo Measure, populate the fields with the data](assets/set-connection-1.png)

1. After you enter the values, click **[!UICONTROL Authenticate]**. Your Marketo Engage account is connected to [!DNL Marketo Measure].

   ![1. After you enter the values, click Authenticate. Your Marketo Engage](assets/set-connection-2.png)

   >[!NOTE]
   >
   >[!DNL Marketo Measure] makes calls to the Marketo API on your behalf without consuming any of your Marketo API limits, so there's no need to worry about caps and credit allocation with other integrations.
