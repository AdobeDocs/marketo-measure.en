---
unique-page-id: 34406495
description: Marketing Ops Tiles - [!DNL Marketo Measure]
title: Marketing Ops Tiles
exl-id: e7978a79-6f6e-4bfd-9962-b35b7d46a9ac
feature: Reporting
---
# Marketing Ops Tiles {#marketing-ops-tiles}

Marketing Ops allows you to validate and diagnose [!DNL Marketo Measure] data with complete visibility into individual touchpoints per Leads, Contacts, Accounts, Campaigns, and Opportunities.

<table> 
 <colgroup> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <td><br></td> 
   <td><p><strong>Account ID</strong></p></td> 
   <td><p><strong>Account Name</strong></p></td> 
   <td><p><strong>Opp ID</strong></p></td> 
   <td><p><strong>Opp Name</strong></p></td> 
   <td><p><strong>Lead or Contact ID</strong></p></td> 
   <td><p><strong>Lead or Contact Email</strong></p></td> 
   <td><p><strong>Campaign ID</strong></p></td> 
   <td><p><strong>Opp Won</strong></p></td> 
   <td><p><strong>Opp Created Date</strong></p></td> 
   <td><p><strong>Opp Close Date</strong></p></td> 
   <td><p><strong>Touchpoint Date</strong></p></td> 
   <td><p><strong>Attribution Model</strong></p></td> 
  </tr> 
  <tr> 
   <td><p><strong>Accounts</strong></p></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><br></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
  </tr> 
  <tr> 
   <td><p><strong>Opportunity</strong></p></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><br></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
  </tr> 
  <tr> 
   <td><p><strong>Contacts</strong></p></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
  </tr> 
  <tr> 
   <td><p><strong>Leads</strong></p></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X*</strong></td> 
   <td><strong>X*</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X*</strong></td> 
   <td><strong>X*</strong></td> 
   <td><strong>X*</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
  </tr> 
  <tr> 
   <td><p><strong>Campaigns</strong></p></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><br></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
  </tr> 
 </tbody> 
</table>

## Account Tile {#account-tile}

![](assets/one-1.png)

Displays the following data related to Account(s) specified.

**Accounts must have Touchpoint data (only applicable if you have ABM enabled)**

-Account ID: Account ID in CRM

-Account Name: Account name in CRM

-Created Date: Created date of the Account in the CRM

* Drill-down: See Created Date by Hour, Minute, Time

-Web Site: Value found in the Website field on the Account

-Engagement Rating: Predictive Engagement Score (PES) populated by [!DNL Marketo Measure]^1

-Opportunities: Number of Opportunities connected to the account

* Drill-down: See details for the associated Opportunity(s)

-Contacts: Number of Contacts listed on this account

* Drill-down: See details for the associated contacts

-Leads: Number of leads mapped to this account through lead to account mapping^1

* Drill-down: See details for the leads that have been mapped to the account

-Attribution Touchpoints: Number of Buyer Attribution Touchpoints for the account

* Drill-down: See Buyer Attribution Touchpoint details (ID, Email, Touchpoint Date, Account Name, Campaign, Channel, Subchannel, Marketing Touch Type, Attribution Model)

-Touchpoints: Number of Touchpoints the contacts on this account have^2

* Drill-down: See Touchpoints on the account Touchpoint details (ID, Email, Touchpoint Date, Account Name, Campaign, Channel, Subchannel, Marketing Touch Type)

>[!NOTE]
>
>If you have ABM, it will show Touchpoints related to the leads that have been mapped through Lead to Account Mapping.

## Opportunity Tile {#opportunity-tile}

![](assets/two-1.png)

Displays the following data related to Opportunity(s) specified.

-Opportunity ID: Opportunity ID in CRM

-Opportunity Name: Opportunity name in CRM

-Account Name: Account name associated to the opportunity

-Created Date: Created date of the Opportunity in the CRM

Drill-down: See Created Date by Hour, Minute, Time

-Close Date: Closed date of the Opportunity in the CRM

Drill-down: See Close Date by Hour, Minute, Time

-Amount: The total amount of the Opportunity

-Contacts: Number of Contacts associated to the Opportunity

Drill-down: See details for the associated contacts

-Attribution Touchpoints: Number of related Buyer Attribution Touchpoints

Drill-down: See Buyer Attribution Touchpoint details (ID, Email, Touchpoint Date, Account Name, Campaign, Channel, Subchannel, Marketing Touch Type, Attribution Model)

## Contacts Tile {#contacts-tile}

![](assets/three-1.png)

Displays the following data related to Contact(s) specified.

-Contact ID: Contact ID in CRM

-Email: Contact record email address

-Created Date: Created date of the contact in the CRM

* Drill-down: See Created Date by Hour, Minute, Time

-Account Name: Account name associated to the contact

-Attribution Touchpoints: Number of Buyer Attribution Touchpoints for the contact

* Drill-down: See Buyer Attribution Touchpoint details (ID, Email, Touchpoint Date, Account Name, Campaign, Channel, Subchannel, Marketing Touch Type, Attribution Model)

-Touchpoints: Number of Buyer Touchpoints for the contact

* Drill-down: See Contacts on the account Touchpoint details (ID, Email, Touchpoint Date, Account Name, Campaign, Channel, Subchannel, Marketing Touch Type)

## Leads Tile {#leads-tile}

![](assets/four-1.png)

Displays the following data related to Lead(s) specified.

-Lead ID: Lead ID in CRM

-Email: Lead record email address

-Created Date: When the Lead was created in the CRM

* Drill-down: See Created Date by Hour, Minute, Time

-Company (from Lead): The company that is listed on the record in the CRM populated by customer

-Account Name: The account name [!DNL Marketo Measure] populates based on our Lead to Account Mapping

-Touchpoints: The number of Touchpoints associated to the lead (s)

* Drill-down: See Contacts on the account Touchpoint details (ID, Email, Touchpoint Date, Account Name, Campaign, Channel, Subchannel, Marketing Touch Type)

## Campaigns Tile {#campaigns-tile}

![](assets/five-1.png)

Displays the following data related to Campaign(s) specified.

-Campaign ID: Campaign ID in CRM

-Campaign Name: Campaign Name in CRM

-Campaign Spend: The spend [!DNL Marketo Measure] has recorded associated to the campaign

-Attribution Model: This will show the appropriate attribution based on the model selected

-Attribution Touchpoints: The number of Buyer Attribution Touchpoints associated to the campaign (s)

* Drill-down: See Buyer Attribution Touchpoint details (ID, Email, Touchpoint Date, Account Name, Campaign, Channel, Subchannel, Marketing Touch Type, Attribution Model)

-Touchpoints: The number of Touchpoints associated to the campaign(s)

* Drill-down: See Contacts on the account Touchpoint details (ID, Email, Touchpoint Date, Account Name, Campaign, Channel, Subchannel, Marketing Touch Type)
