---
description: "[!DNL Marketo Measure] Integrations with Adobe Analytics - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Integrations with [!DNL Adobe Analytics]"
exl-id: 3a125a15-eb74-454a-afb3-75746a1dfac6
feature: Integration
---
# [!DNL Marketo Measure] Integrations with Adobe Analytics {#marketo-measure-integrations-with-adobe-analytics}

The B2B Customer Attributes integration enables mutual users of [!DNL Marketo Measure] and Adobe Analytics to enrich their [!DNL Adobe Analytics] user profiles with valuable metadata derived from the [!DNL Marketo Measure] attribution engine and through its sync capability with CRMs ([!DNL Microsoft Dynamics] and [!DNL Salesforce]). It's available for free to all customers that use [!DNL Adobe Analytics] and [!DNL Marketo Measure].

>[!PREREQUISITES]
>
>You must have active subscriptions to both [!DNL Marketo Measure] and [!DNL Adobe Analytics].

## Configuring the Integration {#configuring-the-integration}

1. Create a  new Customer Attributes Data Source in your Experience Cloud console. Detailed instructions [can be found here](https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/t-crs-usecase.html).

   Take note of the following information, needed in the later steps:

   * The Alias ID, which can be any value you want it to be. We recommend "marketomeasure_id"

   * The FTP server hostname and credentials (user name and password)

1. Once the Customer Attributes Data Source is created, continue the configuration process by navigating to the **[!UICONTROL Integrations]** > **[!UICONTROL Connections]** screen in the [!DNL Marketo Measure] admin menu.

1. Click the **[!UICONTROL Set Up New Customer Attributes Connection]** button and follow the instructions to configure the Customer Attributes integration. The UI prompts you for the Alias ID and FTP connection information that you acquired when creating the Customer Attributes Source in your Core Services Console. Select the set of account attributes that you'd like to sync to your [!DNL Adobe Analytics] account.

   Enter your Adobe IMS Org ID. This ID is displayed in the lower-right corner of your Adobe Experience Cloud Admin Console. For more help with finding this ID, consult with the Adobe Account Team (your Account Manager).

1. After you've finished creating the connection in your [!DNL Marketo Measure] account, you must head back to your Experience Cloud console to [validate the schema](https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/validate-schema.html?lang=en). You don't need to worry about the FTP file upload, [!DNL Marketo Measure] has automated that part for you. Go to the "View/Edit" schema screen for the Customer Attribute Source you created in Step 1 and tell Adobe what the data types are for each of the attributes that [!DNL Marketo Measure] has uploaded on your behalf. You can also create new display-friendly names for the uploaded attributes, if desired.

   If you elected to sync attributes from your CRM account object, it's highly recommended that you choose new display names for them, as [!DNL Marketo Measure] only populates the API-level names for these attributes, which are typically not reporting-friendly.

1. The last step is to configure Attribute Subscriptions for the Experience Cloud applications that you'd like to use the attributes in. You can configure Subscriptions for [!DNL Adobe Analytics] or [!DNL Adobe Target].  More information on how to do that [can be found here](https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/subscription.html).

## Attribute Descriptions {#attribute-descriptions}

When you create a B2B Customer Attribute Connection, [!DNL Marketo Measure] automatically creates a standard set of B2B Customer Attributes for you. These attributes are described in the table below.

In addition to those listed below, you can also upload any attributes attached to the account object in your CRM. If more than one account is tied to the given user, [!DNL Marketo Measure] populates all matching account attribute values in a semicolon-delimited list.

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <td><b>Attribute Name</b></td> 
   <td><b>Description</b></td>
  </tr> 
  <tr> 
   <td>Account.Name</td> 
   <td>The account names associated with the given web visitor. If more than one account is tied to the given user, [!DNL Marketo Measure] populates all matching account names in a semicolon-delimited list.<br/>
   <strong>Note:</strong> account.name is the Salesforce-API-level name for the name attribute on the account object. You can choose a better display name (for example, "Company") for this attribute during the Schema Validation step of the integration configuration (step 4).</td>
  </tr>
  <tr> 
   <td>Attributed Revenue - &#8249;MODEL&#8250;</td> 
   <td>The revenue attributed to this customer by virtue of their association with closed-won opportunities in your CRM, as calculated by the [!DNL Marketo Measure] attribution engine.<br/>
   There are one of these attributes for each attribution model that your [!DNL Marketo Measure] subscriptions allows for (for example, "Attributed Revenue – Full Path").</td>
  </tr>
  <tr> 
   <td>Deepest Funnel Stage</td> 
   <td>The deepest funnel stage of any open opportunity associated with the given user.</td>
  </tr>
  <tr> 
   <td>Open Opportunities</td> 
   <td>A semicolon-delimited list of the opportunity IDs that the given user is tied to according to your CRM data.</td>
  </tr> 
 </tbody> 
</table>

**A note about attribute limits**

The attributes surfaced via this integration count against your contractual attribute limits in [!DNL Adobe Analytics] and [!DNL Adobe Target]. Only attributes that are surfaced via an Attribute Subscription (step 5 in [Configuring the Integration](#configuring-the-integration)) count against your limit for the subscribed application.

## FAQs {#faqs}

**How do I change the set of attributes that I want to share via this integration?**

For an attribute shared by [!DNL Marketo Measure] to your Adobe IMS Org via this integration to be visible and used in [!DNL Adobe Analytics], it must be surfaced via an Attribute Subscription configured in the Core Services Console. Therefore, if you want to remove an attribute so that it no longer appears in [!DNL Adobe Analytics], you can achieve this simply by deleting the attribute subscription.  

You can also delete the B2B Customer Attribute connection in [!DNL Marketo Measure] and re-create it with the attribute you no longer wish to share excluded from the connection configuration. Similarly, to add attributes to the integration, you must delete the existing connection and create a new one with the desired attributes added to the configuration.  

Given the above, it's highly recommended that when configuring the attribute connection for the first time, be as inclusive as possible when selecting attributes.

**What are some example use cases for this integration?**

1. Account-Based Traffic Metrics: Using the account name attribute, you can create segments of one or more target accounts in Adobe Analytics and analyze site traffic metrics for just the subset of traffic originating from target accounts.
1. Content Analytics: Use the revenue metric to analyze which site content is most engaging to customers who ultimately purchase your product or service, or those who reach a specific funnel stage of interest.
1. Live-deal support: Arm your sales team with actionable insight by analyzing site behavior for users associated with a specific open opportunity in your CRM.
