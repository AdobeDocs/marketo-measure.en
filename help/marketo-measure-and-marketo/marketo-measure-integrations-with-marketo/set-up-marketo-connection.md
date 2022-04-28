---
unique-page-id: 42762762
description: Set Up Marketo Connection - Marketo Measure - Product Documentation
title: Set Up Marketo Connection
exl-id: 11660539-1cc5-4768-8f22-d6f7cd0b94f3
---
# Set Up Marketo Connection {#set-up-marketo-connection}

Here's how to set up your connection to Marketo.

1. In Marketo Measure, click the **My Account** drop-down and select **Settings**.

   ![](assets/one-2.png)

1. Under Integrations, click **Connections**.

   ![](assets/one-a.png)

1. Click **Set Up New CRM Connection**.

   ![](assets/two-2.png)

1. Click the **Connect** button next to Marketo.

   ![](assets/three-2.png)

1. Follow the steps to add your Identity Service URL, Client Id, and Client Secret. Follow the Marketo instructions to set up a dedicated Marketo Measure API user for the purposes of this integration. In the case that we need to debug or troubleshoot the connection through the API, we can pinpoint any issues through the dedicated Marketo Measure API user.

>[!NOTE]
>
>When you're setting up the Marketo Role, you do not need to select permissions, so you may leave all boxes unchecked.

1. Utilize the Marketo **Need help?** link to generate these values (if needed): [https://developers.marketo.com/rest-api/base-url/](https://developers.marketo.com/rest-api/base-url/) and [https://developers.marketo.com/rest-api/custom-services/.](https://developers.marketo.com/rest-api/custom-services/)

   ![](assets/four-2.png)

1. After you enter the values, click **Authenticate**. Your Marketo account will then be connected to Marketo Measure.

   ![](assets/five-2.png)

   >[!NOTE]
   >
   >Marketo Measure will make calls to the Marketo API on your behalf without consuming any of your Marketo API limits, so there is no need to worry about caps and credit allocation with other integrations.
