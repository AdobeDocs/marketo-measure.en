---
unique-page-id: 18874769
description: Marketo Measure Insights Configuration - Marketo Measure - Product Documentation
title: Marketo Measure Insights Configuration
exl-id: f6fe296b-d22a-43f2-b124-5d4b2f74d67a
---
# Marketo Measure Insights Configuration {#marketo-measure-insights-configuration}

The Marketo Measure Insights Canvas App should be added to the Lead Page Layout but it requires additional setup in the Connected Apps section of your Salesforce Setup. Please follow these instructions to ensure the Canvas App has the appropriate permissions.

1. Navigate to Salesforce Setup and click **Connected Apps** under the Manage Apps tab.

1. Select the Marketo Measure Insights from the list that populates.

1. Under the OAuth policies section, change the Permitted Users setting to “Admin approved users are pre-authorized.” A pop-up will appear, click **OK** and then **Save**.

   ![](assets/1-1.png)

1. Once the page is saved, you'll be able to click the **Manage Profiles** button.

   ![](assets/2-1.png)

1. Select all the profiles that should have access to Marketo Measure Insights and click **Save**.
