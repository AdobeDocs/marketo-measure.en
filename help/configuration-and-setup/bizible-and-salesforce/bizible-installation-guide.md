---
unique-page-id: 18874787
description: Marketo Measure Installation Guide - Measure - Product Documentation
title: Marketo Measure Installation Guide
exl-id: 371e8e61-7f1b-4580-a00d-1ae309c8b1ab
---
# Marketo Measure Installation Guide {#marketo-measure-installation-guide}

In this guide we will be walking you through how to install and set up Bizible. For implementation we will need admin level access to the following:

* Salesforce
* Integrated Ad Platforms - AdWords, Bing Ads, and Facebook
* Website

## Salesforce Packages to Install {#salesforce-packages-to-install}

We will be installing two packages within your Salesforce environment and then completing additional configuration for full visibility into Bizible.  
  
[Bizible.com/sf](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3000000B3KLuEAN): This is our base package which includes our custom objects and fields. We recommend installing within Production for all users.  
  
[Bizible.com/dashboard-mt](https://login.salesforce.com/packaging/installPackage.apexp?p0=04t610000001jI6): This is our Dashboard Extension Package, which contains 3 pre-built dashboards. We recommend installing within Production for all users.

![](assets/bizible-installation-guide-1.png)

## Salesforce Configuration {#salesforce-configuration}

[Page Layouts](/help/configuration-and-setup/bizible-and-salesforce/page-layout-instructions.md): This is not necessary, but making these page layout updates allows Bizible Touchpoints to be visible on an individual record.

[Bizible Permission Sets](/help/configuration-and-setup/bizible-and-salesforce/bizible-permission-sets.md): These are assigned to the users of the Bizible product based on the level of accessibility you’d like the users to have.

[Sharing Reports and Dashboard Folders](https://help.salesforce.com/articleView?id=analytics_share_folder.htm&type=0): Out of the box, the reports and dashboard folders we create are only visible to the install user. These will need to be shared with additional Bizible users.

[Hide Report Types](/help/configuration-and-setup/bizible-and-salesforce/hiding-unnecessary-report-types.md): Many of the Report Types we create within our product are not needed. To avoid confusion when learning to report on the product, we recommend hiding those that you don't need.

[Custom Amount Field Workflow](/help/advanced-bizible-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md) (if necessary): If you are using a custom amount field to record revenue in Salesforce, we will need a workflow created to map this field value to our Bizible Opportunity Amount field for revenue attribution reporting. Please be sure to let your Success Manager know if you're using a custom amount.
<br>&nbsp;

## Set up Your Adobe Admin Console and Identity Provider {#set-up-your-adobe-admin-console-and-identity-provider}

The first step to using Bizible is to create and sign-in to your provisioned Adobe Admin Console. If you haven't already received the email with log in instructions, please contact your Bizible Account Representative.

>[!NOTE]
>
>Bizible is a Digital Experience (DX) entitlement. If you have a pre-existing VIP, Team Direct, Classroom, or Allocation Adobe IMS Org, Bizible will be added to a newly created IMS Org and Adobe Admin Console.

As a product within the Adobe Suite, Bizible leverages the full functionality of Adobe Admin Console for Identity Management. More resources can be found here: [https://helpx.adobe.com/enterprise/using/admin-console.html](https://helpx.adobe.com/enterprise/using/admin-console.html).

We recommend reviewing all of the resources, best practices, and options available to you for Identity Management: [https://helpx.adobe.com/enterprise/using/set-up-identity.html](https://helpx.adobe.com/enterprise/using/admin-console.html).

For guidance and review of setting up your Identity Management within the Adobe Admin Console, please reach out to your Bizible Account Representative.

In order to facilitate user authentication and authorization with your Bizible instance(s), the following steps are required within the Adobe Admin Console:

**Setting Up the Bizible Product Card**

Upon accessing the Adobe Admin Console, you will see your Bizible Product instance(s) present in the Overview section.

   ![](assets/bizible-installation-guide-1a.png)

Clicking the Bizible Product Card will show you all of your Bizible instance(s). By default, each Bizible Instance has its own profile prefixed with 'Bizible'. Any Admins or Users added to this or any other profile within this instance will be able to log in to Bizible.

   ![](assets/bizible-installation-guide-1b.png)

No action is required to create a new profile within the Bizible Product instance(s).

To begin adding users who can access Bizible, please refer to the [Adding Bizible Admins and Bizible Users](#adding-bizible-admins-and-bizible-users) section below.

## Adding Bizible Admins and Bizible Users {#adding-bizible-admins-and-bizible-users}

The next step is to grant access to the Bizible application by adding users. This can be done in the admins and users directory of the Bizible product card.

   ![](assets/adding-biz-admins-users.png)

| User Type | Description |
|---|---|
|Admins|these are administrators and power users of the Bizible Application with full ability to update and manage Bizible-specific configuration options|
|Users|these are standard users of the Bizible Application with read only permissions within the Bizible application|

When adding a user to their respective profile, you'll see their [Identity Type listed](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/set-up-identity.ug.html).

>[!NOTE]
>
>In order to be a Bizible administrator (in apps.bizible.com), a user must be added as a User _and_ an Admin to any Bizible product profile within the Bizible product card.

**Signing in to Bizible**

After a user has been added to a Product Profile, they're able to access their Bizible instance(s) by choosing the **Sign in with Adobe ID** option at [https://apps.bizible.com](https://apps.bizible.com).

   ![](assets/bizible-installation-guide-8.png)

<br>&nbsp;

## Configuring your Connections and Data Providers {#configuring-your-connections-and-data-providers}

After you've logged in to the Bizible application and have been set up as a user in the Adobe Admin Console, the next step is to set up your various data connections.

**CRM as a Data Provider**

1. In your Bizible account, click the **My Account** drop-down and select **Settings**.

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
   >For more information, refer to this page: [Sandbox Testing](/help/configuration-and-setup/sandbox-testing/testing-a-staging-environment.md). If you have any questions about this process, please contact your Bizible Account representative.

1. Once you've selected your connection option, you'll be prompted to connect to your Salesforce instance and give access to the Bizible application. Click **Allow**.

   ![](assets/bizible-installation-guide-14.png)

After connecting, you'll see the details of your Salesforce connection in the CRM/MAP Connections list.

**Ad Account Connections**

To connect your Ad Accounts with Bizible, start by visiting the Connections tab within the Bizible application.

1. Follow Steps 1 & 2 from the **CRM as a Data Provider** section.

1. Click the **Set up New Ads Connection** button.

   ![](assets/bizible-installation-guide-15.png)

1. Select your desired platform.

   ![](assets/bizible-installation-guide-16.png)

**Bizible Javascript**

In order for Bizible to track your web activities, there are multiple steps for setup.

1. Any web domain(s) you'd like to track with the Bizible JavaScript must be claimed in the Adobe Admin Console and then activated in the Bizible Account. Please follow [these instructions](/help/bizible-and-adobe/domain-management.md).

1. The [Bizible JavaScript](/help/bizible-tracking/setting-up-tracking/adding-bizible-script.md) then needs to be placed across the entire site and landing pages. We recommend hardcoding the script within the head of your landing pages or adding through a Tag Management System such as [Google Tag Manager](/help/bizible-tracking/setting-up-tracking/adding-bizible-script-via-google-tag-manager.md).
