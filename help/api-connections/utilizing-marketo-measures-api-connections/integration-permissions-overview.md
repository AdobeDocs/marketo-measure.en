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
    <th>Integration</th>
    <th>Data Type
    <li>Web Interaction Data</li>
    <li>B2B System Data</li>
    <li>Ad Platform Data</li></th>
    <th>What We Track</th>
    <th>Permission Requirements</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Salesforce</td>
    <td>B2B System Data    
</td>
    <td>Marketo Measure is tracking:
    <br>
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
<br>
Touchpoints created and other data are written into custom bizible fields on Account, Campaign, CampaignMember, Case, Contact, Lead, and Opportunity.</td>
    <td><b>Salesforce connected user permissions (required)</b>
    <br>
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
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>
