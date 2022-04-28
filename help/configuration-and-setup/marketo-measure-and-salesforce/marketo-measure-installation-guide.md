---
unique-page-id: 18874787
description: Marketo Measure Installation Guide - Marketo Measure - Product Documentation
title: Marketo Measure Installation Guide
exl-id: 371e8e61-7f1b-4580-a00d-1ae309c8b1ab
---
# Marketo Measure Installation Guide {#marketo-measure-installation-guide}

In this guide we will be walking you through how to install and set up Marketo Measure. For implementation we will need admin level access to the following:

* Salesforce
* Integrated Ad Platforms - AdWords, Bing Ads, and Facebook
* Website

## Salesforce Packages to Install {#salesforce-packages-to-install}

We will be installing two packages within your Salesforce environment and then completing additional configuration for full visibility into Marketo Measure.  
  
[Base Package](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3000000B3KLuEAN){target="_blank"}: This is our base package which includes our custom objects and fields. We recommend installing within Production for all users.  
  
[Dashboard Extension Package](https://login.salesforce.com/packaging/installPackage.apexp?p0=04t610000001jI6){target="_blank"}: This is our Dashboard Extension Package, which contains 3 pre-built dashboards. We recommend installing within Production for all users.

![](assets/bizible-installation-guide-1.png)

## Salesforce Configuration {#salesforce-configuration}

[Page Layouts](/help/configuration-and-setup/marketo-measure-and-salesforce/page-layout-instructions.md): This is not necessary, but making these page layout updates allows Buyer Touchpoints to be visible on an individual record.

[Marketo Measure Permission Sets](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md): These are assigned to the users of the Marketo Measure product based on the level of accessibility you’d like the users to have.

[Sharing Reports and Dashboard Folders](https://help.salesforce.com/articleView?id=analytics_share_folder.htm&type=0): Out of the box, the reports and dashboard folders we create are only visible to the install user. These will need to be shared with additional Marketo Measure users.

[Hide Report Types](/help/configuration-and-setup/marketo-measure-and-salesforce/hiding-unnecessary-report-types.md): Many of the Report Types we create within our product are not needed. To avoid confusion when learning to report on the product, we recommend hiding those that you don't need.

[Custom Amount Field Workflow](/help/advanced-marketo-measure-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md) (if necessary): If you are using a custom amount field to record revenue in Salesforce, we will need a workflow created to map this field value to our Marketo Measure Opportunity Amount field for revenue attribution reporting. Please be sure to let your Success Manager know if you're using a custom amount.

## Set up Your Adobe Admin Console and Identity Provider {#set-up-your-adobe-admin-console-and-identity-provider}

The first step to using Marketo Measure is to create and sign-in to your provisioned Adobe Admin Console. If you haven't already received the email with log in instructions, please contact your Marketo Measure Account Representative.

>[!NOTE]
>
>Marketo Measure is a Digital Experience (DX) entitlement. If you have a pre-existing VIP, Team Direct, Classroom, or Allocation Adobe IMS Org, Marketo Measure will be added to a newly created IMS Org and Adobe Admin Console.

As a product within the Adobe Suite, Marketo Measure leverages the full functionality of Adobe Admin Console for Identity Management. More resources can be found here: [https://helpx.adobe.com/enterprise/using/admin-console.html](https://helpx.adobe.com/enterprise/using/admin-console.html).

We recommend reviewing all of the resources, best practices, and options available to you for Identity Management: [https://helpx.adobe.com/enterprise/using/set-up-identity.html](https://helpx.adobe.com/enterprise/using/admin-console.html).

For guidance and review of setting up your Identity Management within the Adobe Admin Console, please reach out to your Marketo Measure Account Representative.

In order to facilitate user authentication and authorization with your Marketo Measure instance(s), the following steps are required within the Adobe Admin Console:

**Setting Up the Marketo Measure Product Card**

Upon accessing the Adobe Admin Console, you will see your Marketo Measure Product instance(s) present in the Overview section.

   ![](assets/bizible-installation-guide-1a.png)

Clicking the Marketo Measure Product Card will show you all of your Marketo Measure instance(s). By default, each Marketo Measure Instance has its own profile prefixed with 'Marketo Measure'. Any Admins or Users added to this or any other profile within this instance will be able to log in to Marketo Measure.

   ![](assets/bizible-installation-guide-1b.png)

No action is required to create a new profile within the Marketo Measure Product instance(s).

To begin adding users who can access Marketo Measure, please refer to the [Adding Marketo Measure Admins and Marketo Measure Users](#adding-marketo-measure-admins-and-marketo-measure-users) section below.

## Adding Marketo Measure Admins and Marketo Measure Users {#adding-marketo-measure-admins-and-marketo-measure-users}

The next step is to grant access to the Marketo Measure application by adding users. This can be done in the admins and users directory of the Marketo Measure product card.

   ![](assets/adding-biz-admins-users.png)

| User Type | Description |
|---|---|
|Admins|these are administrators and power users of the Marketo Measure Application with full ability to update and manage Marketo Measure-specific configuration options|
|Users|these are standard users of the Marketo Measure Application with read only permissions within the Marketo Measure application|

When adding a user to their respective profile, you'll see their [Identity Type listed](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/set-up-identity.ug.html).

>[!NOTE]
>
>In order to be a Marketo Measure administrator (in experience.adobe.com/marketo-measure), a user must be added as a User _and_ an Admin to any Marketo Measure product profile within the Marketo Measure product card.

**Signing in to Marketo Measure**

After a user has been added to a Product Profile, they're able to access their Marketo Measure instance(s) by choosing the **Sign in with Adobe ID** option at [https://experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}.

   ![](assets/bizible-installation-guide-8.png)

<br>&nbsp;

## Configuring your Connections and Data Providers {#configuring-your-connections-and-data-providers}

After you've logged in to the Marketo Measure application and have been set up as a user in the Adobe Admin Console, the next step is to set up your various data connections.

**CRM as a Data Provider**

1. In your Marketo Measure account, click the **My Account** drop-down and select **Settings**.

   ![](assets/bizible-installation-guide-9.png)

1. Under Integrations in the left nav, click **Connections**.

   ![](assets/bizible-installation-guide-10.png)

1. Click the **Set Up New CRM Connection** button.

   ![](assets/bizible-installation-guide-11.png)

1. Next to Salesforce, click the **Connect** button.

   ![](assets/bizible-installation-guide-12.png)

1. Select Production or Sandbox.

   ![](assets/bizible-installation-guide-13.png)

   >[!NOTE]
   >
   >For more information, refer to this page: [Sandbox Testing](/help/configuration-and-setup/sandbox-testing/testing-a-staging-environment.md). If you have any questions about this process, please contact your Marketo Measure Account representative.

1. Once you've selected your connection option, you'll be prompted to connect to your Salesforce instance and give access to the Marketo Measure application. Click **Allow**.

   ![](assets/bizible-installation-guide-14.png)

After connecting, you'll see the details of your Salesforce connection in the CRM/MAP Connections list.

**Ad Account Connections**

To connect your Ad Accounts with Marketo Measure, start by visiting the Connections tab within the Marketo Measure application.

1. Follow Steps 1 & 2 from the **CRM as a Data Provider** section.

1. Click the **Set up New Ads Connection** button.

   ![](assets/bizible-installation-guide-15.png)

1. Select your desired platform.

   ![](assets/bizible-installation-guide-16.png)

**Marketo Measure Javascript**

In order for Marketo Measure to track your web activities, there are multiple steps for setup.

1. Any web domain(s) you'd like to track with the Marketo Measure JavaScript must be claimed in the Adobe Admin Console and then activated in the Marketo Measure Account. Please follow [these instructions](/help/marketo-measure-and-adobe/domain-management.md).

1. The [Marketo Measure JavaScript](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script.md) then needs to be placed across the entire site and landing pages. We recommend hardcoding the script within the head of your landing pages or adding through a Tag Management System such as [Google Tag Manager](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-via-google-tag-manager.md).
