---
unique-page-id: 18874672
description: How [!DNL Marketo Measure] and [!DNL Salesforce] Interact - Marketo Measure - Product Documentation
title: How [!DNL Marketo Measure] and [!DNL Salesforce] Interact
exl-id: c2f9d7ce-c5b8-4664-8f92-cb54255190cd
feature: Salesforce
---
# How [!DNL Marketo Measure] and [!DNL Salesforce] Interact {#how-marketo-measure-and-salesforce-interact}

>[!NOTE]
>
>You may see instructions specifying "[!DNL Marketo Measure]" in the documentation, but still see "Bizible" in your CRM. We are working to have that updated and the rebranding will be reflected in your CRM soon.

Let's take a high-level look at the relationship between [!DNL Marketo Measure] and Salesforce.

## Salesforce and [!DNL Marketo Measure]  {#salesforce-and-marketo-measure}

Once the [!DNL Marketo Measure] account is created and [!DNL Salesforce] is connected, [!DNL Marketo Measure] begins pushing marketing data into the CRM instance as long as the [!DNL Marketo Measure] managed package is installed and the [!DNL Marketo Measure] Salesforce user has edit permissions.

If you did not install the [!DNL Marketo Measure] Salesforce package, [!DNL Marketo Measure] will not write any data to your Salesforce instance.

![](assets/1-3.png)

By default, [!DNL Marketo Measure] exports 200 records per API credit each time a job sends data to your CRM. For most customers, this provides the optimal balance between API credits consumed by [!DNL Marketo Measure] and CPU resource requirements on the CRM. However, for customers with complex CRM configurations, such as workflows and triggers, a smaller batch size might be helpful to improve CRM performance. To this end, [!DNL Marketo Measure] allows customers to configure the CRM export batch size. This setting is available on the [!UICONTROL Settings] > [!UICONTROL CRM] > [!UICONTROL General] page in the [!DNL Marketo Measure] web application and customers can choose between batch sizes of 200 (default), 100, 50, or 25.

![](assets/how-bizible-and-salesforce-interact-2.png)

When modifying this setting, keep in mind that smaller batch sizes consume more API credits from your CRM. It's advisable to reduce the batch size only if you are experiencing CPU timeout or high CPU load in your CRM.

## Salesforce Standard Objects and Access {#salesforce-standard-objects-and-access}

This lists the [!DNL Salesforce] Standard Objects that [!DNL Marketo Measure] interacts with, and the custom fields that we add to these objects once the connection is established and the [!DNL Marketo Measure] package is installed. Out of the box, [!DNL Marketo Measure] will NOT write into any standard [!DNL Salesforce] Object fields.

**Lead**

<table> 
 <tbody> 
  <tr> 
   <th>Fields</th> 
   <th>Standard/Custom</th> 
   <th>Read</th> 
   <th>Write</th> 
  </tr> 
  <tr> 
   <td>Id</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Email</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Status</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>CreatedDate</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>LastModifiedDate</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>ConvertedDate</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>ConvertedContactId</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>ConvertedOpportunityId</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsConverted</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsDeleted</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Website</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Company</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>bizible2__Account__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr>
 </tbody> 
</table>

**Contact**

<table> 
 <tbody> 
  <tr> 
   <th>Fields</th> 
   <th>Standard/Custom</th> 
   <th>Read</th> 
   <th>Write</th> 
  </tr> 
  <tr> 
   <td>Account</td> 
   <td>Standard</td> 
   <td><span>x</span></td> 
   <td><br></td> 
  </tr> 
  <tr> 
   <td>Id</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Email</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Created Date</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsDeleted</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>LastModifiedDate</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr>
 </tbody> 
</table>

**Case**

<table> 
 <tbody> 
  <tr> 
   <th>Fields</th> 
   <th>Standard/Custom</th> 
   <th>Read</th> 
   <th>Write</th> 
  </tr> 
  <tr> 
   <td>Id</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>CreatedDate</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>LastModifiedDate</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>SuppliedEmail</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsDeleted</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td>
  </tr> 
 </tbody> 
</table>

**Account**

<table> 
 <tbody> 
  <tr> 
   <th>Fields</th> 
   <th>Standard/Custom</th> 
   <th>Read</th> 
   <th>Write</th> 
  </tr> 
  <tr> 
   <td>Id</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Website</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>LastModifiedDate</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsDeleted</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>bizible2__Engagement_Score__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x </td> 
  </tr> 
 </tbody> 
</table>

**Opportunity**

<table> 
 <tbody> 
  <tr> 
   <th>Fields</th> 
   <th>Standard/Custom</th> 
   <th>Read</th> 
   <th>Write</th> 
  </tr> 
  <tr> 
   <td>Name</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td><br></td> 
  </tr>
  <tr> 
   <td>Account</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td><br></td> 
  </tr>
  <tr> 
   <td>Id</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>CreatedDate</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>LastModifiedDate</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsWon</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsClosed</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsDeleted</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>CloseDate</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>StageName</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Amount</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>bizible2__Bizible_Opportunity_Amount__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x </td> 
  </tr> 
 </tbody> 
</table>

**Opportunity Contact Role**

<table> 
 <tbody> 
  <tr> 
   <th>Fields</th> 
   <th>Standard/Custom</th> 
   <th>Read</th> 
   <th>Write</th> 
  </tr> 
  <tr> 
   <td>Id</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>CreatedDate</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsDeleted</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr>
  <tr> 
   <td>LastModifiedDate</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>OpportunityId</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>ContactId</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
   
  <tr> 
   <td>IsPrimary</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Role</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Campaign**

<table> 
 <colgroup> 
  <col> 
  <col> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <th>Fields</th> 
   <th>Standard/Custom</th> 
   <th>Read</th> 
   <th>Write</th> 
  </tr> 
  <tr> 
   <td>Id</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Email</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Status</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>CreatedDate</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>LastModifiedDate</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>ConvertedDate</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>ConvertedContactId</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>ConvertedOpportunityId</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsConverted</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsDeleted</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Website</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Company</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Type</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td><br></td> 
  </tr>
  <tr> 
   <td>Name</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td>x</td> 
  </tr>
  <tr> 
   <td>bizible2__UniqueId__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
 </tbody> 
</table>

**Campaign Member**

<table> 
 <tbody> 
  <tr> 
   <th>Fields</th> 
   <th>Standard/Custom</th> 
   <th>Read</th> 
   <th>Write</th> 
  </tr> 
  <tr> 
   <td>Id</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>CreatedDate</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>LastModifiedDate</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsDeleted</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>FirstRespondedDate</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>HasResponded</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>ContactId</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>LeadId</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsConverted</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>CampaignId</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>bizible2__Bizible_Touchpoint_Date__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Touchpoint_Status_Date__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Touchpoint_Status_Contact__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Touchpoint_Status_Leade__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Touchpoint_Status_Opportunity__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>To ensure the precision of Marketo Measure capturing deletion events within your Salesforce account, replicable permissions for the objects below are required. Replicable permissions come standard with the following objects:
>
>* Account
>* Campaign
>* Campaign Member
>* Contact
>* Event
>* Lead
>* Opportunity
>* Task


## [!DNL Marketo Measure] Custom Objects in [!DNL Salesforce]  {#marketo-measure-custom-objects-in-salesforce}

Apart from creating custom fields on SFDC's Standard Objects, once the [!DNL Marketo Measure] package is installed, it creates a couple of Custom Objects. Below is a list of these Custom Objects along with a table denoting the fields that [!DNL Marketo Measure] will write to.

**Buyer Touchpoint**

The Buyer Touchpoint is a [!DNL Marketo Measure] Custom Object to encapsulate the marketing interactions for Contacts, Leads, and Cases.

<table> 
 <tbody> 
  <tr> 
   <th>Fields</th> 
   <th>Standard/Custom</th> 
   <th>Read</th> 
   <th>Write</th> 
  </tr> 
  <tr> 
   <td>bizible2__Bizible_Person__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__SF_Campaign__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__UniqueId__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Marketing_Channel__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Marketing_Channel_Path__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Touchpoint_Type__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Ad_Id__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Ad_Content__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Ad_Group_Id__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Ad_Group_Name__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Ad_Campaign_Id__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Ad_Campaign_Name__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Placement_Id__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Placement_Name__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Site_Id__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Site_Name__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Form_URL__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Form_URL_Raw__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Platform__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Browser__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Geo_City__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Geo_Country__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Geo_Region__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Keyword_Id__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Keyword_MatchType__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Touchpoint_Position__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Keyword_Text__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Landing_Page__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Landing_Page_Raw__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Medium__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Referrer_Page__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Referrer_Page_Raw__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Search_Phrase__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Touchpoint_Date__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Touchpoint_Source__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Segment__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Count_First_Touch__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Count_Lead_Creation_Touch__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Count_U_Shaped__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Ad_Destination_URL__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Case__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Contact__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
 </tbody> 
</table>

**[!DNL Marketo Measure] Person**

The [!DNL Marketo Measure] Person is a [!DNL Marketo Measure] Custom Object that is related to both the Lead, Contact, and Case Objects.

<table> 
 <tbody> 
  <tr> 
   <th>Fields</th> 
   <th>Standard/Custom</th> 
   <th>Read</th> 
   <th>Write</th> 
  </tr> 
  <tr> 
   <td>bizible2__UniqueId__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Lead__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Case__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Contact__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x </td> 
  </tr> 
 </tbody> 
</table>

## Buyer Attribution Touchpoint {#buyer-attribution-touchpoint}

The Buyer Attribution Touchpoint is a [!DNL Marketo Measure] Custom Object to encapsulate marketing's influence on Opportunities.

**Buyer Attribution Touchpoint**

<table> 
 <tbody> 
  <tr> 
   <th>Fields</th> 
   <th>Standard/Custom</th> 
   <th>Read</th> 
   <th>Write</th> 
  </tr> 
  <tr> 
   <td>bizible2__Account__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__SF_Campaign__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Contact__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Opportunity__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__UniqueId__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Marketing_Channel__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Marketing_Channel_Path__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Touchpoint_Type__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Ad_Id__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Ad_Content__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Ad_Group_Id__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Ad_Group_Name__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Ad_Campaign_Id__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Ad_Campaign_Name__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Placement_Id__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Placement_Name__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Site_Id__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Site_Name__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Form_URL__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Form_URL_Raw__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Platform__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Browser__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Geo_City__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Geo_Country__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Geo_Region__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Keyword_Id__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Keyword_MatchType__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Touchpoint_Position__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Keyword_Text__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Landing_Page__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Landing_Page_Raw__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Medium__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Referrer_Page__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Referrer_Page_Raw__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Search_Phrase__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Touchpoint_Date__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Touchpoint_Source__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Segment__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Attribution_First_Touch__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Attribution_Lead_Conversion_Touch__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Attribution_U_Shaped__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Attribution_W_Shaped__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Attribution_Custom_Model__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Attribution_Custom_Model_2__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Count_First_Touch__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Count_Lead_Creation_Touch__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Count_U_Shaped__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Count_W_Shaped__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Count_Custom_Model__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Count_Custom_Model_2__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Ad_Destination_URL__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Revenue_First_Touch__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Revenue_Lead_Creation_Touch__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Revenue_U_Shaped__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Revenue_W_Shaped__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Revenue_Custom_Model__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Revenue_Custom_Model_2__c</td> 
   <td>Custom</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
 </tbody> 
</table>
