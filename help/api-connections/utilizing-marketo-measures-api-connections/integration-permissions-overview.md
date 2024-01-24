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
    <th style="width:25%">Data Type
    <li>Web Interaction Data</li>
    <li>B2B System Data</li>
    <li>Ad Platform Data</li></th>
    <th style="width:25%">What We Track</th>
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
    <br>
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
<br>
We recommend creating a dedicated Marketo Measure User within Dynamics for us to export and import data through to avoid any issues with other users in your CRM. Take note of the username and password as well as the endpoint URL as this will be used when creating the Marketo Measure account.
<p>
<b>Security Roles</b>
<br>
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
<br>
<a href="https://developers.facebook.com/docs/permissions/reference/ads_management/">ads_management</a>
<br>
<li>Programmatically create campaigns, manage ads, and fetch metrics.</li>
<li>Build ad management tools that provide innovative solutions and differentiated value for advertisers.</li>
<br>
<br>
<a href="https://developers.facebook.com/docs/permissions/reference/email">email</a>
<br>
<li>Communicating with people and letting them log into your app with the email address associated with their Facebook profile.</li></td>
  </tr>
  <tr>
    <td>LinkedIn</td>
    <td>Ad Platform Data
    <p>
    B2B System Data (Lead Gen Form Data, including forms and submissions, which categorized as CRM Activity).</td>
    <td>Marketo Measure is tracking LinkedIn Ads Campaigns, Creatives, and cost data, as well as Lead Gen Forms and responses. Based on data imported, we can generate LinkedIn touchpoints and associate lead form responses to leads for customers.</td>
    <td><li>Campaign Manager or Account Manager role is required for Marketo Measure to download cost data. (Scope row 1)</li>
    <br>
    <li>Super Admin (Page Admin Role, Scopes row 2) or Lead Gen Forms Manager (Paid Media Admin Role, Scopes row 3) is required for Marketo Measure to access lead gen forms data</li>
    <br>
    <li>Super Admin (Page Admin Role, Scopes row 2) or Sponsored Content Poster (Paid Media Admin Role, Scopes row 3) is required for Marketo Measure to manipulate auto-tagging</li>
    <p>
    <b>Scopes</b>
    <br>
    <a href="https://www.linkedin.com/campaignmanager/accounts">Set up user role in portal (requires login to LinkedIn account)</a> - <a href="https://www.linkedin.com/help/lms/answer/a425731/user-roles-and-functions-in-campaign-manager">User Roles Overview</a>: User role, view and manage user permission, assign roles like account manager or campaign manager
    <p>
    <a href="https://www.linkedin.com/help/linkedin/answer/a570172/add-or-remove-admins-on-your-showcase-page?lang=en">Set up Page Admin Role - <a href="https://www.linkedin.com/help/linkedin/answer/a541981/linkedin-page-admin-roles-overview">Page Admin Role Definitions</a>: Page admin role, on the desired admin page
    <p>
    <a href="https://www.linkedin.com/help/linkedin/answer/a570172/add-or-remove-admins-on-your-showcase-page?lang=en">Set up Paid Media Admin Role (look for Paid Media Admin) - <a href="https://www.linkedin.com/help/linkedin/answer/a554540">Paid Media Admin Definitions</a>: Paid Media Admin Roles</td>
  </tr>
  <tr>
    <td>DoubleClick</td>
    <td>Ad Platform Data</td>
    <td>Marketo Measure is tracking Accounts, Advertisers, Campaigns, (custom) Landing Pages, Ads, Creatives, Placements, and Sites.</td>
    <td><li>User's primary Google Account email address is required</li>
<li>Campaign Manager permissions required to access Campaign Manager 360 account</li>
<ul>
<li>View and manage DoubleClick advertisers reports</li>
<li>View and manage DoubleClick Campaign Managers display ad campaigns</li>
<p>
    <b>Scopes</b>
    <br>
    <a href="https://www.googleapis.com/auth/userinfo.email">https://www.googleapis.com/auth/userinfo.email</a>: See your primary Google Account email address
    <p>
     <a href="https://www.googleapis.com/auth/dfareporting">https://www.googleapis.com/auth/dfareporting</a>: View and manage DoubleClick for Advertisers reports
    <p>
     <a href="https://www.googleapis.com/auth/dfatrafficking">https://www.googleapis.com/auth/dfatrafficking</a>: View and manage your DoubleClick Campaign Manager's (DCM) display ad campaigns</td>
  </tr>
  <tr>
    <td>AdWords</td>
    <td>Ad Platform Data</td>
    <td>We integrate with AdWords to:
<p>
<li>Import customer ads data</li>
<li>Import customer ads cost data</li>
<li>Update client's ads by appending url parameters/updating Url Tracking Templates</li>
<p>
Marketo Measure is tracking Campaigns, Ad Groups, Creatives, Site Links, and Keywords.</td>
    <td><li>User's primary Google Account email address is required</li>
<p>
    <b>Scopes</b>
    <br>
    <a href="https://www.googleapis.com/auth/userinfo.email">https://www.googleapis.com/auth/userinfo.email</a>: See your primary Google Account email address</td>
  </tr>
  <tr>
    <td>Bing</td>
    <td>Ad Platform Data</td>
    <td>Marketo Measure is tracking Accounts, Campaigns, Ad Groups, Creatives, and Keywords.</td>
    <td><li>User must grant "offline access" via their Microsoft Account (Which grants Marketo Measure access to the End-User's UserInfo even when not logged in). See <a href="https://learn.microsoft.com/en-us/deployoffice/overview-extended-offline-access">Microsoft's page</a> on how to do so.</li>
<p>
    <b>Scopes</b>
    <br>
    <a href="https://learn.microsoft.com/en-us/deployoffice/overview-extended-offline-access">https://learn.microsoft.com/en-us/deployoffice/overview-extended-offline-access</a>: Maintain access to data you have given it access to permission.</td>
  </tr>
  <tr>
    <td>Marketo Engage</td>
    <td>B2B System Data</td>
    <td>The Marketo integration enables Marketo Measure to collect Marketo Activities, People, Programs, and Program Memberships. Additionally, Marketo Measure tracks Marketo cookies (Munchkin IDs) for the purposes of linking Marketo web activities to Marketo Measure lead touchpoints, <a href="/help/marketo-measure-and-marketo/marketo-measure-integrations-with-marketo/marketo-engage-programs-integration.md#cookie-mapping">as described here</a>:
    <p>
    <i>As a result of the Marketo Measure integration with Marketo, the Marketo Measure Cookie Id is also now mapped and synced with the Marketo Munchkin Id. This helps close the gap to attribute the anonymous first touch to a web session rather than attributing both the FT and LC touches to a Marketo Activity.</i>
    </td>
    <td>The customer must create a dedicated Marketo Engage API User and supply the credentials to Marketo Measure. No additional permissions configuration is required. <a href="/help/marketo-measure-and-marketo/marketo-measure-integrations-with-marketo/set-up-marketo-connection.md#configuring-the-integration">Learn more</a>.</td>
  </tr>
  <tr>
    <td>Adobe Analytics</td>
    <td>B2B System Data</td>
    <td>The B2B Customer Attributes integration enables mutual users of Marketo Measure and Adobe Analytics to enrich their Adobe Analytics user profiles with valuable metadata derived from the Marketo Measure attribution engine and through its sync capability with CRMs (Microsoft Dynamics and Salesforce). <a href="/help/marketo-measure-and-adobe/marketo-measure-integrations-with-adobe-analytics.md">Learn more</a>.</td>
    <td>The customer must provide Marketo Measure with an Alias ID and FTP server credentials to a location that data will be uploaded to their Analytics instance.
    <p>
    Take note of the following information, as you'll need it for some of the later steps in the process:
    <p>
    <li>The Alias ID, which can be any value you want it to be. We recommend "marketomeasure_id"</li>
    <li>The FTP server hostname and credentials (user name and password)</li>
    <p>
    <a href="/help/marketo-measure-and-adobe/marketo-measure-integrations-with-adobe-analytics.md#configuring-the-integration">Learn more</a></td>
  </tr>
  <tr>
    <td>Bizible Javascript</td>
    <td></td>
    <td><a href="/help/marketo-measure-tracking/setting-up-tracking/data-collected-by-javascript.md">What data bizible.js collects</a>.</td>
    <td></td>
  </tr>
</tbody>
</table>
