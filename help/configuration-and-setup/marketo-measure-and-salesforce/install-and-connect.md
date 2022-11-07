---
unique-page-id: 18874580
description: Install and Connect - [!DNL Marketo] Measure - Product Documentation
title: Install and Connect
exl-id: 9be8d3fa-1045-4e41-bc2e-5b9d4d3513ae
---
# Install and Connect {#install-and-connect}

This lesson provides an overview of the [!DNL Marketo] Measure components that are added to your [!DNL Salesforce] upon installation and how to connect your [!DNL Salesforce] account to your [!DNL Marketo Measure] account.

## Installation {#installation}

Two packages must be installed in order to use [!DNL Marketo] Measure in your [!DNL Salesforce] environment:

* Marketo Measure’s base package
* Dashboard Extension Package

To integrate with [!DNL Salesforce], [!DNL Marketo Measure] mirrors the way [!DNL Salesforce] organizes and displays data. [!DNL Salesforce] organizes data into Objects, Records, Fields, and allows you to visualize this data through Reports and Dashboards. When [!DNL Marketo Measure] is installed into SF, we add our own Objects, Fields, Reports, and Dashboards.

Marketo Measure's **Base Package** contains:

* 7 Custom Marketo Measure Objects
* Custom Marketo Measure Fields
* 25 [!DNL Stock] Reports

Marketo Measure's **Dashboard Extension Package** contains three pre-built Dashboards.

Marketo Measure is able to read standard SF Objects, Fields and Records, however Marketo Measure will never update or push data to them. All the data collected by Marketo Measure's Javascript will be surfaced in the Marketo Measure Custom Objects and Fields.

For the complete installation guide, [click here](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-installation-guide.md).

## Connecting Accounts {#connecting-accounts}

1. Go to the Marketo Measure App and log-in.

1. In the menu bar at the top of the screen, navigate to **My Account** and  click the [!UICONTROL Settings] option.

1. In the column of setting options on the left, click [!UICONTROL Connections] located under the [!UICONTROL Integrations] section.

   ![](assets/1.png)

1. Under the CRM section in Connections, click **Set Up New CRM Connection**.

   ![](assets/2.png)

1. A pop-up window will appear asking you to Select CRM connection. Click the Connect button next to the Salesforce logo.

   ![](assets/3.png)

1. A final pop-up window will appear, asking you for your [!DNL Salesforce] credentials. Enter your information and click **[!UICONTROL Authorize]** to connect the account to Marketo Measure.
