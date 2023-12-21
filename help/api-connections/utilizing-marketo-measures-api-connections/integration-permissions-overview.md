---
description: Integration Permissions Overview - [!DNL Marketo Measure] - Product Documentation
title: Integration Permissions Overview
hide: yes
hidefromtoc: yes
feature: APIs, Integration
---
# Integration Permissions Overview {#integration-permissions-overview}

This guide outlines the necessary permissions for seamless integration with Marketo Measure, ensuring each integration operates effectively and without issue.

<table>
<thead>
  <tr>
    <th style="width:10%">Integration</th>
    <th style="width:20%">Data Type
    <li>Web Interaction Data</li>
    <li>B2B System Data</li>
    <li>Ad Platform Data</li></th>
    <th style="width:30%">What We Track</th>
    <th style="width:40%">Permission Requirements</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Salesforce</td>
    <td>B2B System Data    
</td>
    <td>Marketo Measure is tracking:
    <p>
    <li>Account</li>
    <li>Campaign</li>
    <li>CampaignMember</li>
    <li>Contact</li>
    <li>CurrencyConversionRange</li>
    <li>CurrencyStatus</li>
    <li>Events</li>
    <li>FieldHistory (Lead, Contact, and Opportunity)</li>
    <li>Lead</li>
    <li>Opportunity</li>
    <li>OpportunityContactRole</li>
    <li>OpportunityHistory</li>
    <li>Tasks</li>
<p>
Touchpoints created and other data are written into custom bizible fields on Account, Campaign, CampaignMember, Case, Contact, Lead, and Opportunity.</td>
    <td><b>Salesforce Connected User Permissions (required)</b>
    <p>
    <b>Marketo Measure Administrator Permission Set For Dedicated User:</b> Allow SFDC admin to perform CRUD operations on marketo measure objects.
    <br>
    <b>View and Edit Converted Leads Permission Set:</b> This allows Marketo Measure to decorate leads after they have been converted to contacts.
    <br>
    <b>Salesforce Marketing User Checkbox:</b> The Marketing User checkbox allows users to create campaigns and use the Campaign Import Wizards.
    <br>
    <b>Marketo Measure Standard User:</b> Gives a user the ability to read records from Marketo Measure objects.
    <p>
    <b>Salesforce Standard Field Permissions</b>
    <a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">Salesforce standard objects and access</a>
    <p>
    <b>Salesforce Custom Field Permissions</b>
    <br>
    We provide feature settings to hold custom salesforce fields that the customers can use. If these feature settings are defined then we need READ access to each of the salesforce fields saved in the feature setting (e.g., if CustomLeadSourceField setting value is equal to "LeadSource__c" then we require READ access to this field).
    </td>
  </tr>
  <tr>
    <td>Dynamics</td>
    <td>B2B System Data</td>
    <td>Marketo Measure is tracking:
    <p>
    <li>Account
<li>ActivityParty
<li>ActivityPointer
<li>Campaign
<li>CampaignItem (CampaignList in our system)
<li>CampaignResponse (CampaignMember in our system)
<li>Contact
<li>Lead
<li>List (MarketingList in our system)
<li>ListMember (MarketingListMember in our system)
<li>Opportunity
<li>Organization
<li>TransactionCurrency (CurrencyConversionRange and CurrencyStatus in our system)
<li>Appointment, CampaignActivity, Email, Fax, IncidentResolution, Letter, PhoneCall, RecurringAppointmentMaster, ServiceAppointment, Task
<li>bizible2_bizible_abtest
<li>bizible2_bizible_attribution_touchpoint
<li>bizible2_bizible_event
<li>bizible2_bizible_history
<li>bizible2_bizible_touchpoint
<p>
Touchpoints created and other data are written into custom bizible fields on Account, Campaign, CampaignResponse, Contact, Lead, List, Opportunity, and PhoneCall</td>
    <td><b>Marketo Measure User Permissions</b>
<p>
We recommend creating a dedicated Marketo Measure User within Dynamics for us to export and import data through to avoid any issues with other users in your CRM. Take note of the username and password as well as the endpoint URL as this will be used when creating the Marketo Measure account.
<p>
<b>Security Roles</b>
<p>
If your organization uses Dynamics Security Roles, please make sure the connected user, or the dedicated Marketo Measure User has sufficient read/write permissions to the required entities.
<br>
Security Roles are located here: Settings > Security > Security Roles
<br>
For Marketo Measure custom entities, we will need full permissions across all of our entities.
<p>
<b>Dynamics Standard Field Permissions</b>
<br>
<a href="/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/marketo-measure-dynamics-schema.md">Marketo Measure Dynamics Schema</a>
<p>
<b>Dynamics Custom Field Permissions</b>
<br>
We need READ access for any field on the Lead or Contact entity that the customer wants to use for custom Suppress/Remove Touchpoint Settings rules.
<br>
We need READ access for any field on the Lead or Opportunity entity that the customer wants to use for Segment rules or Stage Mapping.
<br>
We need READ access for any field on the Campaign, CampaignResponse, and List entities that the customer wants to use for Syncing Campaign/MarketingList members.
</td>
  </tr>
  <tr>
    <td>Facebook</td>
    <td>Ad Platform Data</td>
    <td>We integrate with Facebook to:
<p>
<li>Import customer ads data</li>
<li>Import customer ads cost data</li>
<li>Update client's ads by appending url parameters</li>
<p>
Marketo Measure is tracking Accounts, Campaigns, Ad Groups, Ads, Filter IDs and URLs.</td>
    <td><li>The ads_management permission is required to create campaigns, manage ads or fetch Ad metrics.</li>
<li>The email permission is required to allow users to login their Facebook email.</li>
<p>
<b>Scopes</b>
<p>
<a href="https://developers.facebook.com/docs/permissions/reference/ads_management/">ads_management</a>
<br>
<li>Programmatically create campaigns, manage ads, and fetch metrics.</li>
<li>Build ad management tools that provide innovative solutions and differentiated value for advertisers.</li>
<p>
<a href="https://developers.facebook.com/docs/permissions/reference/email">email</a>
<br>
<li>Communicating with people and letting them log into your app with the email address associated with their Facebook profile.</li></td>
  </tr>
  <tr>
    <td>LinkedIn</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>DoubleClick</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>AdWords</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Bing</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Marketo Engage</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobe Analytics</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Bizible Javascript</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>
