---
unique-page-id: 35586140
description: Data Warehouse Schema - Marketo Measure - Product Documentation
title: Data Warehouse Schema
exl-id: f1895eb1-a32d-4c43-93fb-0aa838527946
feature: Data Warehouse
---
# Data Warehouse Schema {#data-warehouse-schema}

Data Warehouse allows you to track as much as you want, report on your attribution data wherever you want, and plug it in to other data sets.

>[!IMPORTANT]
>
>* Rows with a value for _DELETED_DATE will be retained for 7 days, then removed from Snowflake.
>* The time zones used in Snowflake adhere to Coordinated Universal Time (UTC).

>[!NOTE]
>
>[Click here](#sample-queries) to see sample queries at the bottom of this article.

## Entity Relationship Diagrams {#entity-relationship-diagrams}

The _Data Warehouse Data Model_ ERD shows how data in the data warehouse is intended to flow and be linked together. This diagram does not include all tables available in the data warehouse because some of them represent mapping tables, views of other tables already present, or deprecated tables we don't recommend using any more. See the detailed descriptions of tables and columns present in the data warehouse below. Many of these tables contain denormalized fields, however, this diagram is the recommended data model, leveraging data from dimensional tables instead.  

The additional _Ads Dimensional Data Model_ ERD presents a view of how tables for ads specific dimensions can be best linked back to the tables in the main data model. Though ads dimensions are also denormalized in other tables, this represents the recommended model for joining these dimensions.

_Click an image for its full-size version_

<table style="table-layout:auto"> 
 <tbody> 
  <tr> 
   <th>Data Warehouse Data Model</th> 
   <th>Ads Dimensional Data Model</th> 
  </tr> 
  <tr> 
   <td><a href="assets/data-warehouse-data-model.pdf"><img src="assets/data-warehouse-data-model-thumb.png"></a></td>
   <td><a href="assets/ads-dimensional-data-model.pdf"><img src="assets/ads-dimensional-data-model-thumb.png"></a></td> 
  </tr> 
 </tbody> 
</table>

## Views {#views}

### BIZ_ACCOUNTS {#biz-accounts}

Accounts imported from the source system.

<table>
  <tbody>
    <tr>
      <th><strong>Column</strong></th>
      <th><strong>Data Type</strong></th>
      <th><strong>Description</strong></th>
      <th><strong>Sample Data</strong></th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>The Account Id from the source system.</td>
      <td>0013100001kpAZxAAM</td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>The created date of the Account, from the source system.</td>
      <td>2016-08-28 00:32:55.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>The last modified date of the Account, from the source system.</td>
      <td>2018-08-01 17:38:30.000</td>
    </tr>
    <tr>
      <td>NAME</td>
      <td>varchar</td>
      <td>The Account Name, from the source system.</td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>WEB_SITE</td>
      <td>varchar</td>
      <td>Website for the Account, as recorded in the source system, used for Lead to Account mapping.</td>
      <td>www.adobe.com</td>
    </tr>
    <tr>
      <td>ENGAGEMENT_RATING</td>
      <td>varchar</td>
      <td>A letter grade (A, B, C, D, N/A) that is generated from the [!DNL Marketo Measure] Machine Learning model. This will be null if ABM is disabled.</td>
      <td>B</td>
    </tr>
    <tr>
      <td>ENGAGEMENT_SCORE</td>
      <td>number(38,19)</td>
      <td>A numerical score calculated by [!DNL Marketo Measure] Machine Learning to generate the Predictive Engagement Score (Engagement_Rating). This will be null if ABM is disabled.</td>
      <td>0.1417350147058800000</td>
    </tr>
    <tr>
      <td>DOMAIN</td>
      <td>varchar</td>
      <td>The parsed down version of the website, only storing the domain.</td>
      <td>adobe</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>boolean</td>
      <td>Whether or not the record is deleted in the source system.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Custom properties that [!DNL Marketo Measure] has imported from the source system, in JSON format.</td>
      <td>{"Account_Type__c": "Security", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td><b>&#8727;</b> INDUSTRY</td>
      <td>varchar</td>
      <td>Primary business of the Account.</td>
      <td>Retail, Telecommunication</td>
    </tr>
    <tr>
      <td><b>&#8727;</b> COUNTRY</td>
      <td>varchar</td>
      <td>Country portion of the Account's address.</td>
      <td>USA, Canada</td>
    </tr>
  </tbody>
</table>
<p>
<b>&#8727;</b> <i>Only available in Marketo Measure Ultimate</i>
<p>

### BIZ_ACCOUNT_TO_EMAILS {#biz-account-to-emails}

Mapping table between known Lead/Contact email addresses and Accounts. This table will be empty if ABM is disabled.

<table>
  <tbody>
    <tr>
    <th><strong>Column</strong></th>
      <th><strong>Data Type</strong></th>
      <th><strong>Description</strong></th>
      <th><strong>Sample Data</strong></th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>A unique Id for the record.</td>
      <td>0013800001MMPPiAAP_person@adobe.com|2022-01-05 17:22:13.000</td>
    </tr>
    <tr>
      <td>ACCOUNT_ID</td>
      <td>varchar</td>
      <td>Source system Account Id.</td>
      <td>0013100001phrBAAAY</td>
    </tr>
    <tr>
      <td>EMAIL</td>
      <td>varchar</td>
      <td>Email address that has been mapped to the Account, either through Contact relationships or Lead to Account mapping.</td>
      <td>person@adobe.com</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>The last modified date of the Account, from the source system.</td>
      <td>2018-08-31 23:53:39.000</td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>The created date of the Account, from the source system.</td>
      <td>2018-08-18 22:01:32.000</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>boolean</td>
      <td>Whether or not the record is considered deleted.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_ACTIVITIES {#biz-activities}

Activities imported from a source system or connected Ad Account.

<table>
  <tbody>
  <tr>
    <th><strong>Column</strong></th>
    <th><strong>Data Type</strong></th>
    <th><strong>Description</strong></th>
    <th><strong>Sample Data</strong></th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>The Activity Id from the source system.</td>
      <td>1678625515</td>
    </tr>
    <tr>
      <td>LEAD_ID</td>
      <td>varchar</td>
      <td>Id for the Lead associated with the Activity.</td>
      <td>15530482</td>
    </tr>
    <tr>
      <td>CONTACT_ID</td>
      <td>varchar</td>
      <td>Id for the Contact associated with the Activity.
      </td>
      <td>13792552</td>
    </tr>
    <tr>
      <td>ACTIVITY_TYPE_ID</td>
      <td>varchar</td>
      <td>Id for the Activity Type, from the source system.</td>
      <td>104</td>
    </tr>
    <tr>
      <td>ACTIVITY_TYPE_NAME</td>
      <td>varchar</td>
      <td>The Activity Name, from the source system.</td>
      <td>
        <p>change status in progression</p>
      </td>
    </tr>
    <tr>
      <td>START_DATE</td>
      <td>timestamp_ntz</td>
      <td>Start Date of the Activity, from the source system.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>END_DATE</td>
      <td>timestapm_ntz</td>
      <td>End Date of the Activity, from the source system.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>CAMPAIGN_ID</td>
      <td>varchar</td>
      <td>Id for the Campaign the Activity is a part of, from the source system.</td>
      <td>
        <p>li.508038570.147643566</p>
      </td>
    </tr>
    <tr>
      <td>SOURCE_SYSTEM</td>
      <td>varchar</td>
      <td>Identifies the source system type.</td>
      <td>Marketo</td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the row was created in the source system.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the row was last modified in the source system.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>boolean</td>
      <td>Whether or not the record is considered deleted in the source system.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>AD_FORM_ID</td>
      <td>varchar</td>
      <td>Id for the Ad Form the Activity is part of, from the source system.</td>
      <td>li.507063119.3757704</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_ADS {#biz-ads}

Ads imported from any connected Ad Account.

<table>
  <tbody>
    <tr>
      <th><strong>Column</strong></th>
      <th><strong>Data Type</strong></th>
      <th><strong>Description</strong></th>
      <th><strong>Sample Data</strong></th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>A unique Id for the Ad.</td>
      <td>fb.106851586409075.6052044288804.6052044290004.6053457066804</td>
    </tr>
    <tr>
      <td>DISPLAY_ID</td>
      <td>varchar</td>
      <td>The Ad Id from the source system.</td>
      <td>6053457066804</td>
    </tr>
    <tr>
      <td>AD_ACCOUNT_UNIQUE_ID</td>
      <td>varchar</td>
      <td>Id for the Ad Account from which the Ad was imported.</td>
      <td>fb.106851586409075</td>
    </tr>
    <tr>
      <td>AD_ACCOUNT_NAME</td>
      <td>varchar</td>
      <td>Name of the Ad Account from which the Ad was imported.</td>
      <td>[!DNL Marketo Measure] Account</td>
    </tr>
    <tr>
      <td>ADVERTISER_UNIQUE_ID</td>
      <td>varchar</td>
      <td>Id of the Advertiser for the Ad, specifically for Doubleclick.</td>
      <td>300181641</td>
    </tr>
    <tr>
      <td>ADVERTISER_NAME</td>
      <td>varchar</td>
      <td>Name of the Advertiser for the Ad, specifically for Doubleclick.</td>
      <td>Marketing Analytics</td>
    </tr>
    <tr>
      <td>AD_GROUP_UNIQUE_ID</td>
      <td>varchar</td>
      <td>Id of the Ad Group for the Ad.</td>
      <td>fb.106851586409075.6052044288804.6052044290004</td>
    </tr>
    <tr>
      <td>AD_GROUP_NAME</td>
      <td>varchar</td>
      <td>Name of the Ad Group for the Ad.</td>
      <td>Ad Set for Ad B</td>
    </tr>
    <tr>
      <td>AD_CAMPAIGN_UNIQUE_ID</td>
      <td>varchar</td>
      <td>Id of the Campaign for the Ad.</td>
      <td>fb.106851586409075.6052044288804</td>
    </tr>
    <tr>
      <td>AD_CAMPAIGN_NAME</td>
      <td>varchar</td>
      <td>Name of the Campaign for the Ad.</td>
      <td>Lead generation Campaign</td>
    </tr>
    <tr>
      <td>IS_ACTIVE</td>
      <td>boolean</td>
      <td>Whether or not the Ad is still active in the source system.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>boolean</td>
      <td>Whether or not the Ad has been deleted in the source system.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified.</td>
      <td>2018-08-02 06:35:59.000</td>
    </tr>
    <tr>
      <td>FIRST_IMPORTED</td>
      <td>timestamp_ntz</td>
      <td>Date the record was first imported from the source system.</td>
      <td>2018-08-02 06:35:59.000</td>
    </tr>
    <tr>
      <td>NAME</td>
      <td>varchar</td>
      <td>Name of the Ad, from the source system.</td>
      <td>Ad 2</td>
    </tr>
    <tr>
      <td>NEEDS_UPDATE</td>
      <td>boolean</td>
      <td>Whether or not the Ad needs to be updated for [!DNL Marketo Measure] tagging.
      <p>(Diagnostic field, used by internal processing.)
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>GROUPING_KEY</td>
      <td>varchar</td>
      <td>Diagnostic field, used for internal processing.</td>
      <td>fb.106851586409075.6052044288804.6052044290004</td>
    </tr>
    <tr>
      <td>ENTITY_TYPE</td>
      <td>varchar</td>
      <td>The main object or entity for this table. In this case, "Ad".</td>
      <td>Ad</td>
    </tr>
    <tr>
      <td>PROVIDER_TYPE</td>
      <td>varchar</td>
      <td>Name of the Ad Provider for the Ad.</td>
      <td>Facebook</td>
    </tr>
    <tr>
      <td>URL_CURRENT</td>
      <td>varchar</td>
      <td>The URL for the landing page.
        <p>(Diagnostic field, for internal processing.)
      </td>
      <td></td>
    </tr>
    <tr>
      <td>URL_OLD</td>
      <td>varchar</td>
      <td>Previous value for URL_CURRENT.
      <p>(Diagnostic field, for internal processing.)
      </td>
      <td></td>
    </tr>
    <tr>
      <td>URL_REQUESTED</td>
      <td>varchar</td>
      <td>What the URL will be decorated with [!DNL Marketo Measure] parameters.
      <p>(Diagnostic field, for internal processing.)
      </td>
      <td></td>
    </tr>
    <tr>
      <td>URL_ALTENATIVES</td>
      <td>varchar</td>
      <td>Imported from the source system.
      <p>(Diagnostic field, for internal processing.)
      </td>
      <td></td>
    </tr>
    <tr>
      <td>ROW_KEY</td>
      <td>number(38,0)</td>
      <td>Foreign Key to the Biz_Facts view.</td>
      <td>6008900572523230000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_ADVERTISERS {#biz-advertisers}

Advertisers imported from any connected Ad Account.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>A unique Id for the Advertiser.</td>
      <td>dc.6114.9143143</td>
    </tr>
    <tr>
      <td>DISPLAY_ID</td>
      <td>varchar</td>
      <td>The Advertiser Id from the source system.</td>
      <td>9143143</td>
    </tr>
    <tr>
      <td>AD_ACCOUNT_UNIQUE_ID</td>
      <td>varchar</td>
      <td>Id for the Ad Account from which the Ad was imported.</td>
      <td>fb.106851586409075</td>
    </tr>
    <tr>
      <td>AD_ACCOUNT_NAME</td>
      <td>varchar</td>
      <td>Name of the Ad Account from which the Ad was imported.</td>
      <td>[!DNL Marketo Measure] Account</td>
    </tr>
    <tr>
      <td>ADVERTISER_UNIQUE_ID</td>
      <td>varchar</td>
      <td>Id of the Advertiser, specifically for Doubleclick.</td>
      <td>300181641</td>
    </tr>
    <tr>
      <td>ADVERTISER_NAME</td>
      <td>varchar</td>
      <td>Name of the Advertiser, specifically for Doubleclick.</td>
      <td>[!DNL Marketo Measure] Marketing Analytics</td>
    </tr>
    <tr>
      <td>AD_GROUP_UNIQUE_ID</td>
      <td>varchar</td>
      <td>Expected to be null since there is no Ad Group above the Advertiser in any ads hierarchy.</td>
      <td>null</td>
    </tr>
    <tr>
      <td>AD_GROUP_NAME</td>
      <td>varchar</td>
      <td>Expected to be null since there is no Ad Group above the Advertiser in any ads hierarchy.</td>
      <td>null</td>
    </tr>
    <tr>
      <td>AD_CAMPAIGN_UNIQUE_ID</td>
      <td>varchar</td>
      <td>Expected to be null since there is no Ad Campaign above the Advertiser in any ads hierarchy.</td>
      <td>null</td>
    </tr>
    <tr>
      <td>AD_CAMPAIGN_NAME</td>
      <td>varchar</td>
      <td>Expected to be null since there is no Campaign above the Ad Advertiser in any ads hierarchy.</td>
      <td>null</td>
    </tr>
    <tr>
      <td>IS_ACTIVE</td>
      <td>boolean</td>
      <td>Whether or not the Advertiser is still active in the source system.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>boolean</td>
      <td>Whether or not the Advertiser has been deleted in the source system.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified.</td>
      <td>2018-08-02 06:35:59.000</td>
    </tr>
    <tr>
      <td>FIRST_IMPORTED</td>
      <td>timestamp_ntz</td>
      <td>Date the record was first imported from the source system.</td>
      <td>2018-08-02 06:35:59.000</td>
    </tr>
    <tr>
      <td>NAME</td>
      <td>varchar</td>
      <td>Name of the Advertiser, from the source system.</td>
      <td>[!DNL Marketo Measure] Marketing Analytics</td>
    </tr>
    <tr>
      <td>NEEDS_UPDATE</td>
      <td>boolean</td>
      <td>Whether or not the Advertiser needs to be updated for [!DNL Marketo Measure] tagging.
      <p>(Diagnostic field, used by internal processing.)
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>GROUPING_KEY</td>
      <td>varchar</td>
      <td>Diagnostic field, used for internal processing.</td>
      <td></td>
    </tr>
    <tr>
      <td>ENTITY_TYPE</td>
      <td>varchar</td>
      <td>The main object or entity for this table. In this case, "Advertiser".</td>
      <td>Advertiser</td>
    </tr>
    <tr>
      <td>PROVIDER_TYPE</td>
      <td>varchar</td>
      <td>The Ad Provider for the Advertiser.</td>
      <td>Doubleclick</td>
    </tr>
    <tr>
      <td>ROW_KEY</td>
      <td>number(38,0)</td>
      <td>Foreign Key to the Biz_Facts view.</td>
      <td>6008900572523230000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_ACCOUNTS {#biz-ad-accounts}

Ad Accounts imported from any connected Ad Account.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique identifier for the Ad Account.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>varchar</td>
      <td>The Ad Account Id from the source system.</td>
      <td>
        <p>6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>Expected to be null since this is the record for the Ad Accounts in the ads hierarchy.</td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>Expected to be null since this is the record for the Ad Accounts in the ads hierarchy.</td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Advertiser above the Ad Accounts in any ads hierarchy.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Advertiser above the Ad Accounts in any ads hierarchy.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Ad Group above the Ad Accounts in any ads hierarchy.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Ad Group above the Ad Accounts in any ads hierarchy.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Ad Campaign above the Ad Accounts in any ads hierarchy.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Ad Campaign above the Ad Accounts in any ads hierarchy.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Ad Account is still active in the source system.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Ad Account has been deleted in the source system.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was last modified.</p>
      </td>
      <td>
        <p>2018-09-06 12:54:37.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was first imported from the source system.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>varchar</td>
      <td>Name of the Ad Account, from the source system.</td>
      <td>
        <p>[!DNL Marketo Measure] Ad Account</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Advertiser needs to be updated for [!DNL Marketo Measure] tagging.</p>
        <p>(Diagnostic field, used by internal processing.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>varchar</td>
      <td>Diagnostic field, used for internal processing.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The main object or entity for this table. In this case, "Account".</p>
      </td>
      <td>
        <p>Account</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The name of the Ad Provider for the Ad Account.</p>
      </td>
      <td>
        <p>AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_CURRENCY_UNIT</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The currency code used for the Ad Account, from the source system.</p>
      </td>
      <td>
        <p>USD</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COMPANY_ID</p>
      </td>
      <td>varchar</td>
      <td>Used for internal processing.</td>
      <td>1933789</td>
    </tr>
    <tr>
      <td>
        <p>SOURCE</p>
      </td>
      <td>varchar</td>
      <td>Parsed from the URL from utm_source.</td>
      <td>
        <p>Social</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDIUM</p>
      </td>
      <td>varchar</td>
      <td>Parsed from the URL from utm_medium.</td>
      <td>
        <p>lisu07261601</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_30_DAYS_COST</p>
      </td>
      <td>
        <p>number(38,19)</p>
      </td>
      <td>
        <p>The amount of spend imported for the last 30 days, only applicable to AdWords.</p>
      </td>
      <td>
        <p>17260.000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_30_DAYS_IMPRESSIONS</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>The number of impressions from the last 30 days, only applicable to AdWords.</p>
      </td>
      <td>
        <p>730060</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_30_DAYS_CLICKS</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>The number of clicks from the last 30 days, only applicable to AdWords.</p>
      </td>
      <td>
        <p>3400</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_30_DAYS_CONVERSIONS</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>The number of conversions reported from the last 30 days, only applicable to AdWords.</p>
      </td>
      <td>
        <p>180</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>varchar</td>
      <td>Used for internal diagnostics.</td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>varchar</td>
      <td>Used for internal diagnostics.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>varchar</td>
      <td>Used for internal diagnostics.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The tracking template added on the Ad Account level for AdWords or Bing for tagging landing pages.</p>
      </td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Foreign Key to the Biz_Facts view.</p>
      </td>
      <td>
        <p>-4609512587744160000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_CAMPAIGNS {#biz-ad-campaigns}

Campaigns imported from connected Ad Accounts, source systems, utm, and self reported.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>Unique Id for the Campaign.</p>
      </td>
      <td>
        <p>aw.6601259029.285114995</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>varchar</td>
      <td>The Campaign Id from the source system.</td>
      <td>
        <p>285114995</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Ad Account from which the Campaign was imported.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name for the Ad Account from which the Campaign was imported.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Advertiser for the Campaign, specifically for Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Advertiser for the Campaign, specifically for Doubleclick.</p>
      </td>
      <td>
        <p>Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Ad Group above the Campaign in any ads hierarchy.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Ad Group above the Campaign in any ads hierarchy.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Unique Id for the Campaign, use the Id field instead.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Campaign, use the Name field instead.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Campaign is still active in the source system.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Campaign has been deleted in the source system.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was last modified.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was first imported from the source system.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Campaign.</p>
      </td>
      <td>
        <p>Partner Retargeting</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Campaign needs to be updated for [!DNL Marketo Measure] tagging.</p>
        <p>(Diagnostic field, used by internal processing.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>varchar</td>
      <td>Diagnostic field, used for internal processing.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The main object or entity for this table. In this case, "Campaign".</p>
      </td>
      <td>
        <p>Campaign</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Provider for the Campaign.</p>
      </td>
      <td>
        <p>AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DAILY_BUDGET</p>
      </td>
      <td>
        <p>number(38,19)</p>
      </td>
      <td>
        <p>The daily budget that's set in the Ad Platform for the Campaign.</p>
      </td>
      <td>
        <p>0.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>varchar</td>
      <td>Used for internal diagnostics.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>varchar</td>
      <td>Used for internal diagnostics.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>varchar</td>
      <td>Used for internal diagnostics.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The tracking template added on the Campaign level for AdWords or Bing for tagging landing pages.</p>
      </td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Foreign Key to the Biz_Facts view.</p>
      </td>
      <td>
        <p>-6008900572523230000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_FORMS {#biz-ad-forms}

Ad Forms imported from any connected Ad Account.

<table>
  <tr>
    <th>
      <p>Column</p>
    </th>
    <th>
      <p>Data Type</p>
    </th>
    <th>
      <p>Description</p>
    </th>
    <th>
      <p>Sample Data</p>
    </th>
  </tr>
  <tbody>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the Ad Form.</p>
      </td>
      <td>
        <p>li.507063119.3757704</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Ad Account from which the Ad Form was imported.</p>
      </td>
      <td>
        <p>li.507063119</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Account from which the Ad Form was imported.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Deleted status from the source system. Set to deleted if the status is Draft, Archived, or Canceled.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was last modified.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was first imported from the source system.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Form.</p>
      </td>
      <td>
        <p>NSPA Ebook LGF (May 2020)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The main object or entity for this table. In this case, "AdForm".</p>
      </td>
      <td>
        <p>AdForm</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Provider for the Ad Form.</p>
      </td>
      <td>
        <p>LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DESCRIPTION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Description of the Ad Form.</p>
      </td>
      <td>
        <p>Learn how intelligent automation can increase process efficiency in mortgage refinance loan applications.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HEADLINE</p>
      </td>
      <td>varchar</td>
      <td>Headline of the Ad Form.</td>
      <td>
        <p>It's Time to Automate the Refinancing Application Process</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_URL</p>
      </td>
      <td>varchar</td>
      <td>Landing URL of the Ad Form.</td>
      <td>
        <p>https://adobe.com/blog/refinancing-application-process/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>QUESTIONS</p>
      </td>
      <td>varchar</td>
      <td>List of Questions for the Ad Form.</td>
      <td>
        <p>First name:Last name:Email address:Country/Region:Job title:Company name</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STATUS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Status of the Ad Form.</p>
      </td>
      <td>
        <p>submitted</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>SOURCE_ID</td>
      <td>varchar</td>
      <td>Id for the Source from which the record originated.</td>
      <td>aw.3284209</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_GROUPS {#biz-ad-groups}

Ad Groups imported from any connected Ad Account.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the Ad Group.</p>
      </td>
      <td>
        <p>aw.6601259029.317737955.23105326115</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>varchar</td>
      <td>The Ad Group Id from the source system.</td>
      <td>
        <p>23105326115</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Ad Account from which the Ad Group was imported.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name for the Ad Account from which the Ad Group was imported.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Ad Group in the Doubleclick ads hierarchy.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Ad Group in the Doubleclick ads hierarchy.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since this is the record for the Ad Group in the hierarchy.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since this is the record for the Ad Group in the hierarchy.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Campaign for the Ad Group.</p>
      </td>
      <td>
        <p>aw.6601259029.317737955</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Campaign for the Ad Group.</p>
      </td>
      <td>
        <p>Revenue Attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Ad Account is still active in the source system.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Ad Account has been deleted in the source system.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was last modified.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:14.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was first imported from the source system.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:14.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Group.</p>
      </td>
      <td>
        <p>Revenue Attribution - Account Based</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Advertiser needs to be updated for [!DNL Marketo Measure] tagging.</p>
        <p>(Diagnostic field, used by internal processing.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>varchar</td>
      <td>Diagnostic field, used for internal processing.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The main object or entity for this table. In this case, "AdGroup".</p>
      </td>
      <td>
        <p>AdGroup</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Provider for the Ad Group.</p>
      </td>
      <td>
        <p>AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_NETWORK_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The medium(s) that the Ad Group is running on.</p>
      </td>
      <td>
        <p>Search, Display, YouTube_Search, YouTube_Watch</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>varchar</td>
      <td>Used for internal diagnostics.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>varchar</td>
      <td>Used for internal diagnostics.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>varchar</td>
      <td>Used for internal diagnostics.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The tracking template added on the Ad Account level for AdWords or Bing for tagging landing pages.</p>
      </td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Foreign Key to the Biz_Facts view.</p>
      </td>
      <td>
        <p>-5594512713562690000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_PROVIDERS

<p>Ad Providers from any connected Ad Account, including an entry for self reported if applicable.</p>

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the Ad Provider.</p>
      </td>
      <td>
        <p>Bing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Provider.</p>
      </td>
      <td>
        <p>Bing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Foreign Key to the Biz_Facts view.</p>
      </td>
      <td>
        <p>4783788151269206864</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_ATTRIBUTION_TOUCHPOINTS {#biz-attribution-touchpoints}

<p>Buyer Attribution Touchpoints, all touchpoints associated with an Opportunity.</p>
<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the Buyer Attribution Touchpoint (BAT).</p>
      </td>
      <td>
        <p>BAT2_0060Z00000lFHtOQAW_</p>
        <p>0030Z00003K5bpKQAR_2017-06-20:01-05-20-6193330.0b5c5678807c</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was last modified.</p>
      </td>
      <td>
        <p>2018-09-01 04:53:53.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPPORTUNITY_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Opportunity the BAT is attributed to.</p>
      </td>
      <td>
        <p>0060Z00000lFHtOQAW</p>
      </td>
    </tr>
    <tr>
      <td>CONTACT_ID</td>
      <td>varchar</td>
      <td>
        <p>Id for the Contact associated with the BAT.</p>
      </td>
      <td>
        <p>0030Z00003K5bpKQAR</p>
      </td>
    </tr>
    <tr>
      <td>EMAIL</td>
      <td>varchar</td>
      <td>Email address associated with the BAT.</td>
      <td>person@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Account the BAT is attributed to.</p>
      </td>
      <td>
        <p>0013100001otbIAAAY</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>USER_TOUCHPOINT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the User Touchpoint which generated the BAT.</p>
      </td>
      <td>
        <p>person@adobe.com_00v1B00003ZbWzHQAV</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TOUCHPOINT_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date of the touchpoint.</p>
      </td>
      <td>
        <p>2017-06-20 01:05:20.000</p>
      </td>
    </tr>
    <tr>
      <td>VISITOR_ID</td>
      <td>varchar</td>
      <td>Id for the visitor associated with the BAT.</td>
      <td>v_277d79d01678498fea067c9b631bf6df</td>
    </tr>
    <tr>
      <td>
        <p>MARKETING_TOUCH_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The type of activity, Web Visit, Web Form, Web Chat, Phone Call, [CRM] Campaign, or [CRM] Activity. Referred to in the CRM as "Touchpoint Type."</p>
      </td>
      <td>
        <p>Web Form</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CHANNEL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The channel the touchpoint falls into, as defined in the custom channel definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Marketing Channel - Path."</p>
      </td>
      <td>
        <p>Social.LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY1</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The segment value for the 1st Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments."</p>
      </td>
      <td>
        <p>ABC</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY2</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The segment value for the 2nd Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments."</p>
      </td>
      <td>
        <p>Yes</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY3</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The segment value for the 3rd Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments."</p>
      </td>
      <td>
        <p>SMB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY4</p>
      </td>
      <td>varchar</td>
      <td>The segment value for the 4th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments."</td>
      <td>
        <p>New Business</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY5</p>
      </td>
      <td>varchar</td>
      <td>The segment value for the 5th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments."</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY6</p>
      </td>
      <td>varchar</td>
      <td>The segment value for the 6th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments."</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY7</p>
      </td>
      <td>varchar</td>
      <td>The segment value for the 7th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments."</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY8</p>
      </td>
      <td>varchar</td>
      <td>The segment value for the 8th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments."</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY9</p>
      </td>
      <td>varchar</td>
      <td>The segment value for the 9th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments."</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY10</p>
      </td>
      <td>varchar</td>
      <td>The segment value for the 10th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments."</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY11</p>
      </td>
      <td>varchar</td>
      <td>The segment value for the 11th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments."</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY12</p>
      </td>
      <td>varchar</td>
      <td>The segment value for the 12th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments."</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY13</p>
      </td>
      <td>varchar</td>
      <td>The segment value for the 13th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments."</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY14</p>
      </td>
      <td>varchar</td>
      <td>The segment value for the 14th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments."</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY15</p>
      </td>
      <td>varchar</td>
      <td>The segment value for the 15th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments."</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected browser that the user was on during the session.</p>
      </td>
      <td>
        <p>Chrome</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_VERSION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected version of the browser that the user was on during the session.</p>
      </td>
      <td>
        <p>58</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected platform that the user was on during the session.</p>
      </td>
      <td>
        <p>Mac</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_VERSION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected version of the platform that the user was on during the session.</p>
      </td>
      <td>
        <p>10_12</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first landing page of the session which resulted in a touchpoint. Referred to in the CRM as "Landing Page".</p>
      </td>
      <td>
        <p>http://www.adobe.com/blog/uncover- truth-behind-cost-per-lead</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first landing page of the session that resulted in a touchpoint. A raw landing page will contain all query parameters in the URL. Referred to in the CRM as "Landing Page - Raw".</p>
      </td>
      <td>
        <p>http://www.adobe.com/blog/uncover-truth -behind-cost-per-lead?utm_content=27322869&amp;utm_ medium=social&amp;utm_source=linkedin</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Typically the external landing page immediately before the user comes onto the website. Referred to in the CRM as "Referrer Page".</p>
      </td>
      <td>
        <p>https://www.linkedin.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Typically the external landing page immediately before the user comes onto the website. A raw referrer page may contain query parameters in the URL. Referred to in the CRM as "Referrer Page - Raw".</p>
      </td>
      <td>
        <p>https://www.linkedin.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first form recorded in a session which resulted in a touchpoint. Subsequent form submissions will not show up in the Attribution_Touchpoints table, but rather in the Form_Submits table. Referred to in the CRM as "Form URL".</p>
      </td>
      <td>
        <p>http://info.adobe.com/intro-guide-b2b-marketing-attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first form recorded in a session which resulted in a touchpoint. Subsequent form submissions will not show up in the Attribution_Touchpoints table, but rather in the Form_Submits table. A raw form page may contain query parameters in the URL. Referred to in the CRM as "Form URL - Raw".</p>
      </td>
      <td>
        <p>http://info.adobe.com/intro-guide-b2b-marketing-attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the form submission occurred.</p>
      </td>
      <td>
        <p>2017-06-20 01:06:41.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CITY</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected city the user was in during the session.</p>
      </td>
      <td>
        <p>San Francisco</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REGION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected region the user was in during the session.</p>
      </td>
      <td>
        <p>California</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COUNTRY</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected country the user was in during the session.</p>
      </td>
      <td>
        <p>United States</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDIUM</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Used to define the medium which resulted in the touchpoint. This can either be parsed out from the URL from utm_medium. Or, if [!DNL Marketo Measure] is able to resolve an ad, it may be values such as "cpc" or "display."</p>
      </td>
      <td>
        <p>social</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEB_SOURCE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Used to define the source which resulted in the touchpoint. This can be parsed out from the URL from utm_source, generically set as "CRM Campaign" if it was synced from the CRM, or if [!DNL Marketo Measure] is able to resolve an ad, it may be values such as "Google AdWords" or "Facebook." Referred to in the CRM as "Touchpoint Source".</p>
      </td>
      <td>
        <p>linkedin</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEARCH_PHRASE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The value which the user entered in the browser to search for and ended up on the website. Depending on the keyword buys, this may or may not match the keywords purchased from the Paid Search platform.</p>
      </td>
      <td>
        <p>google [!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Ad platform [!DNL Marketo Measure] was able to resolve from, typically one of our integration partners.</p>
      </td>
      <td>
        <p>Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Ad Account in which the ad was resolved from.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Account in which the ad was resolved from.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Advertiser from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Advertiser from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Site from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Site from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Placement from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Placement from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>roadblock</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Campaign from the Ad Account in which the Ad was resolved from.</p>
      </td>
      <td>
        <p>aw.6601259029.317738075</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Campaign from the Ad Account in which the Ad was resolved from.</p>
      </td>
      <td>
        <p>Marketing Attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Ad Group from the Ad Account in which the Ad was resolved from. This only applies to Google Adwords.</p>
      </td>
      <td>
        <p>aw.6601259029.317738075.23105327435</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Group from the Ad Account in which the Ad was resolved from. This only applies to Google AdWords.</p>
      </td>
      <td>
        <p>Marketing Attribution - General</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Ad from the Ad Account in which the Ad was resolved from. This applies to Doubleclick Campaign Manager and Facebook (display).</p>
      </td>
      <td>
        <p>dc.6114.8882972.25272734.492579576</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad from the Ad Account in which the Ad was resolved from. This applies to Doubleclick Campaign Manager and Facebook (display).</p>
      </td>
      <td>
        <p>Budget Webinar - sidebar</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Creative from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>aw.6601259029.317738075.23105327435.182716179597</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Creative from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>B2B Marketing Attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first line of the Creative from the search Ad, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>Download The CMOs Guide</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The second line of the Creative from the search Ad, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>Learn how attribution measures ROI by connecting marketing activities to revenue</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The landing page that clicks through from the search Ad, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>http://info.adobe.com/cmos-guide-to-b2b-marketing-attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The friendly URL name that's shown on the search Ad, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>http://info.adobe.com/CMOs-Guide</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Keyword purchased from the Paid Search buy, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>aw.6601259029.317738075.23105327435.4838421670</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Keyword purchased from the Paid Search buy, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search)</p>
      </td>
      <td>
        <p>"marketing attribution"</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The type of match found between the search phrase and the purchased keyword.</p>
      </td>
      <td>
        <p>Exact</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_FIRST_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not this touchpoint is treated as the first touch of the opportunity journey.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_LEAD_CREATION_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not this touchpoint is treated as the lead creation touch of the opportunity journey.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_OPP_CREATION_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not this touchpoint is treated as the opportunity creation touch of the opportunity journey.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_CLOSED_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not this touchpoint is treated as the closed touch of the opportunity journey.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGES_TOUCHED</p>
      </td>
      <td>varchar</td>
      <td>This field has been deprecated. Use the Stage_Transitions tables for stage information.</td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>IS_FORM_SUBMISSION_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not this touchpoint had a form fill during the session.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_IMPRESSION_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not this touchpoint is treated as the first impression touch of the opportunity journey</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>The calculated percentage allocated to this touchpoint because it's a first touch (See Is_First_Touch).</p>
      </td>
      <td>
        <p>0.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_ANON_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>The calculated percentage allocated to this touchpoint because it's a lead creation touch (See Is_Lead_Creation_Touch).</p>
      </td>
      <td>
        <p>0.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>U_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>The calculated percentage allocated to this touchpoint because it's part of a u-shaped touch (See Is_First_Touch and Is_Lead_Creation_Touch).</p>
      </td>
      <td>
        <p>0.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>W_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>The calculated percentage allocated to this touchpoint because it's part of a w-shaped touch (See Is_First_Touch, Is_Lead_Creation_Touch, and Is_Opp_Creation_Touch).</p>
      </td>
      <td>
        <p>0.0153374234214425</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FULL_PATH_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>The calculated percentage allocated to this touchpoint because it's part of a full path model (See Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch, Is_Closed_Touch).</p>
      </td>
      <td>
        <p>0.0143061513081193</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CUSTOM_MODEL_PERCENTAGE</p>
      </td>
      <td>number(22,19)</td>
      <td>The calculated percentage allocated to this touchpoint because it's part of a custom model (See Is_First_Touch,  Is_Lead_Creation_Touch, Is_Opp_Creation_Touch, Is_Closed_Touch).</td>
      <td>0.0143061513081193</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether this touchpoint is deleted.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Foreign Key to the Biz_Facts view.</p>
      </td>
      <td>
        <p>-2712935512233520000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPPORTUNITY_ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>LANDING_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>FORM_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERTISER_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_ROW_KEY</p>
      </td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_ATTRIBUTION_AI_TOUCHPOINTS {#biz-attribution-ai-touchpoints}

Data generated from the Attribution AI integration. These fields are only populated for Marketo Measure Ultimate customers. 

<table>
<thead>
  <tr>
    <th>Column</th>
    <th>Data Type</th>
    <th>Description</th>
    <th>Sample Data</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>CONVERSION_DATE</td>
    <td>Timestamp_ntz</td>
    <td>date of the conversion</td>
    <td>2020-01-01 01:01:00.000</td>
  </tr>
  <tr>
    <td>CONVERSION_NAME</td>
    <td>varchar</td>
    <td>name of the conversion event (as specified by the customer in the UI setting)</td>
    <td> </td>
  </tr>
  <tr>
    <td>CONVERSION_ID</td>
    <td>varchar</td>
    <td>id for the conversion event (this is the original unique id value sent with the event data record in the source dataset)</td>
    <td>0013100001b44aGAAQ</td>
  </tr>
  <tr>
    <td>CONVERSION_EVENT_ID</td>
    <td>varchar</td>
    <td>original MM event id for the conversion event 
    <br>maps to a user touchpoint or a stage transition</td>
    <td>00U0Z00000pCZmyUAG</td>
  </tr>
  <tr>
    <td>CONVERSION_ACCOUNT_ID</td>
    <td>varchar</td>
    <td>original MM account id for the conversion event</td>
    <td>0013100001kpAZxAAM</td>
  </tr>
  <tr>
    <td>CONVERSION_OPPORTUNITY_ID</td>
    <td>varchar</td>
    <td>original MM opportunity id for the conversion event</td>
    <td>0060Z00000lFHtOQAW</td>
  </tr>
  <tr>
    <td>CONVERSION_LEAD_ID</td>
    <td>varchar</td>
    <td>original MM lead id for the conversion event <br>likely to be null most of the time</td>
    <td>00Q0Z000013dw4GUAQ</td>
  </tr>
  <tr>
    <td>CONVERSION_CONTACT_ID</td>
    <td>varchar</td>
    <td>original MM contact id for the conversion event
    <br>likely to be null most of the time</td>
    <td>00331000032hMxRAAU</td>
  </tr>
  <tr>
    <td>CONVERSION_EVENT_TYPE</td>
    <td>varchar</td>
    <td>type of conversion event (b2b = lead conversion, b2c = opportunity conversion)</td>
    <td>b2b</td>
  </tr>
  <tr>
    <td>SCORE_DATE</td>
    <td>Timestamp_ntz</td>
    <td>date the touchpoints were last scored</td>
    <td>2020-01-01 01:01:00.000</td>
  </tr>
  <tr>
    <td>INFLUENCED_PERCENT</td>
    <td>number(38,35)</td>
    <td>the fraction of the conversion that each touchpoint is responsible for</td>
    <td>0.10</td>
  </tr>
  <tr>
    <td>INCREMENTAL_PERCENT</td>
    <td>number(38,35)</td>
    <td>the amount of marginal impact directly caused by a touchpoint</td>
    <td>0.25</td>
  </tr>
  <tr>
    <td>TOUCHPOINT_DATE</td>
    <td>Timestamp_ntz</td>
    <td>the touchpoint or stage transition date</td>
    <td>2020-01-01 01:01:00.000</td>
  </tr>
  <tr>
    <td>TOUCHPOINT_EVENT_ID</td>
    <td>varchar</td>
    <td>id for the event which generated the touchpoint</td>
    <td>00U3100000VLUnEEAX</td>
  </tr>
  <tr>
    <td>TOUCHPOINT_OPPORTUNITY_ID</td>
    <td>varchar</td>
    <td>id for the opportunity associated with the touchpoint</td>
    <td>0060Z00000lFHtOQAW</td>
  </tr>
  <tr>
    <td>TOUCHPOINT_ACCOUNT_ID</td>
    <td>varchar</td>
    <td>id for the account associated with the touchpoint</td>
    <td>0013100001kpAZxAAM</td>
  </tr>
  <tr>
    <td>TOUCHPOINT_LEAD_ID</td>
    <td>varchar</td>
    <td>id for the lead associated with the touchpoint</td>
    <td>00Q0Z000013dw4GUAQ</td>
  </tr>
  <tr>
    <td>TOUCHPOINT_CONTACT_ID</td>
    <td>varchar</td>
    <td>id for the contact associated with the touchpoint</td>
    <td>00331000032hMxRAAU</td>
  </tr>
  <tr>
    <td>COUNT_TO_CONVERSION</td>
    <td>number(38,0)</td>
    <td>the rank or ordinal value of the touchpoint in the chain leading to the conversion event</td>
    <td>10000</td>
  </tr>
  <tr>
    <td>AAI_SOURCE_ID</td>
    <td>varchar</td>
    <td>foreign key to the attribution ai sources table</td>
    <td> </td>
  </tr>
  <tr>
    <td>_CREATED_DATE</td>
    <td>Timestamp_ntz</td>
    <td>date the record was created in Snowflake</td>
    <td>2020-01-01 01:01:00.000</td>
  </tr>
  <tr>
    <td>_MODIFIED_DATE</td>
    <td>Timestamp_ntz</td>
    <td>date the record was last modified in Snowflake</td>
    <td>2020-01-01 01:01:00.000</td>
  </tr>
  <tr>
    <td>_DELETED_DATE</td>
    <td>Timestamp_ntz</td>
    <td>date the record was deleted in Snowflake</td>
    <td>2020-01-01 01:01:00.000</td>
  </tr>
</tbody>
</table>

### BIZ_CAMPAIGN_MEMBERS {#biz-campaign-members}

Campaign Members imported from the source system. This table will be empty if Campaign Sync is disabled.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>The Campaign Member Id from the source system.</td>
      <td>00v0Z00001VVzdLQAT</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>The last modified date of the Campaign Member, from the source system.</p>
      </td>
      <td>
        <p>2018-08-31 20:49:54.000</p>
      </td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>The created date of the Campaign Member, from the source system.</p>
      </td>
      <td>
        <p>2018-08-31 20:49:54.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_TOUCH_POINT_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date and time the customer sets to override the campaign date and use this value for the Touchpoint Date instead.</p>
      </td>
      <td>
        <p>2018-08-30 18:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Lead the Campaign Member is tied to.</p>
      </td>
      <td>
        <p>00Q0Z000013dw4GUAQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Email for the Lead the Campaign Member is tied to.</p>
      </td>
      <td>persona@adobe.com</td>
    </tr>
    <tr>
      <td>CONTACT_ID</td>
      <td>varchar</td>
      <td>
        <p>Id for the Contact the Campaign Member is tied to.</p>
      </td>
      <td>
        <p>00331000032hMxRAAU</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Email for the Contact the Campaign Member is tied to.</p>
      </td>
      <td>persona@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>STATUS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Status of the Campaign Member, usually set to Sent or Responded or another custom value. This status is tied to the Campaign_Sync_Type to determine which Campaign Members to create touchpoints for.</p>
      </td>
      <td>
        <p>Sent</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_RESPONDED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Tells if the Campaign Member was marked as "Responded" from the Status picker.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_RESPONDED_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the Campaign Member first responded.</p>
      </td>
      <td>
        <p>2018-08-30 07:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the related Campaign the Campaign Member is a part of.</p>
      </td>
      <td>
        <p>Fast CMO Interviews</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the related Campaign the Campaign Member is a part of.</p>
      </td>
      <td>
        <p>7010Z000001TcKlQAK</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Type selected on the related Campaign the Campaign Member is a part of. The Type is used to map the Marketing Channel.</p>
      </td>
      <td>
        <p>Offline</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_SYNC_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Determines which Campaign Members to create touchpoints for. The possible values are: Include_All, Include_Responded, Exclude_All.</p>
      </td>
      <td>
        <p>Include_All</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SYNC_STATUS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Audit field, states whether or not a Buyer Touchpoint was generated for the Lead. If no touchpoint was created, the reason why it didn't qualify is given.</p>
      </td>
      <td>
        <p>No Touchpoint: Date outside model</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_SYNC_STATUS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Audit field, states whether or not a Buyer Touchpoint was generated for the Contact. If no touchpoint was created, the reason why it didn't qualify is given.</p>
      </td>
      <td>
        <p>Touchpoint Created</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPP_SYNC_STATUS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Audit field, states whether or not a Buyer Attribution Touchpoint was generated for the Opportunity. If no touchpoint was created, the reason why it didn't qualify is given.</p>
      </td>
      <td>
        <p>Touchpoint Created</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the record is considered deleted in the source system .</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Custom properties that [!DNL Marketo Measure] has imported from the source system, in JSON format.</td>
      <td>{"Campaign_Type__c":"Dinners","Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CHANNELS {#biz-channels}

Marketing Channels, as created in the [!DNL Marketo Measure] application.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the Channel.</p>
      </td>
      <td>
        <p>Organic Search.Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Channel.</p>
      </td>
      <td>
        <p>Organic Search.Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Foreign Key to the Biz_Facts view.</p>
      </td>
      <td>
        <p>6008900572523230000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>The date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>The date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>The date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CONTACTS {#biz-contacts}

Contacts imported from the source system.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>The Contact Id from the source system.</p>
      </td>
      <td>
        <p>0030Z00003OzioeQAB</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the Contact record was last modified, from the source system.</p>
      </td>
      <td>
        <p>2018-09-05 05:17:53.000</p>
      </td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the Contact record was created, from the source system.</p>
      </td>
      <td>
        <p>2018-09-05 05:17:51.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Email address of the Contact, from the source system.</p>
      </td>
      <td>persona@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNTID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Account related to the Contact.</p>
      </td>
      <td>
        <p>0013100001b44aGAAQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SOURCE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Source in which the Lead was created.</p>
      </td>
      <td>
        <p>Advertisement</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Current stage of the Contact, recognized as a custom stage which can be created in the [!DNL Marketo Measure] application.</p>
      </td>
      <td>
        <p>Demo Scheduled</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE_PREVIOUS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>All previous stages for the Contact, recognized as custom stages which can be created in the [!DNL Marketo Measure] application.</p>
      </td>
      <td>
        <p>Open - Contact</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ODDS_OF_CONVERSION</p>
      </td>
      <td>
        <p>number(38,19)</p>
      </td>
      <td>
        <p>This feature has been deprecated. Do not use this column.</p>
      </td>
      <td>
        <p>N/A</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_COOKIE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The [!DNL Marketo Measure] Cookie Id used to populate from an integration partner to map an offline event to a web session. Requirement: Enable Call Tracking: True</p>
      </td>
      <td>
        <p>08c1063cb0a64349ad0d2d862f5cc700</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the record is deleted in the source system.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>IS_DUPLICATE</td>
      <td>boolean</td>
      <td>Used to de-duplicate records if both a CRM and Marketo integration are set up. If there are duplicates, the Marketo Contact is marked true.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>SOURCE_SYSTEM</td>
      <td>varchar</td>
      <td>Indicates if the record came from a CRM or a Marketo integration.</td>
      <td>Crm</td>
    </tr>
    <tr>
      <td>OTHER_SYSTEM_ID</td>
      <td>varchar</td>
      <td>Maps a person from a Marketo integration with a Contact from a CRM integration. If both a CRM and Marketo integration exist, the value is the corresponding Id.</td>
      <td>1234 / 00Q0Z00001OohgTUAR</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Custom properties that [!DNL Marketo Measure] has imported from the source system , in JSON format.</td>
      <td>{"Contact_Type__c":"CMO", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>ROW_KEY</td>
      <td>number(38,0)</td>
      <td>Foreign Key to the Biz_Facts view.</td>
      <td>3263982503087870000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td><b>&#8727;</b> JOB_TITLE</td>
      <td>varchar</td>
      <td>Job Title of the Contact.</td>
      <td>CEO, Vice President</td>
    </tr>
  </tbody>
</table>
<p>
<b>&#8727;</b> <i>Only available in Marketo Measure Ultimate</i>
<p>

### BIZ_CONVERSION_RATES {#biz-conversion-rates}

Currency conversion rates imported from the source system.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
      <td>ID</td>
      <td>number(38,0)</td>
      <td>A unique Id for the record.</td>
      <td>-5942345438803054604</td>
    </tr>
    <tr>
      <td>CURRENCY_ID</td>
      <td>number(38,0)</td>
      <td>Id value for the Currency.</td>
      <td>7493833133899044458</td>
    </tr>
    <tr>
      <td>SOURCE_ISO_CODE</td>
      <td>varchar</td>
      <td>Currency ISO code, from the source system.</td>
      <td>USD</td>
    </tr>
    <tr>
      <td>START_DATE</td>
      <td>timestamp_ntz</td>
      <td>Start date of the Conversion Rate.</td>
      <td>2018-11-01 00:00:00.000</td>
    </tr>
    <tr>
      <td>END_DATE</td>
      <td>timestamp_ntz</td>
      <td>Next start date for the Conversion Rate. (The end date for the Conversion Rate is end_date minus 1 day.)</td>
      <td>2018-09-01 00:00:00.000</td>
    </tr>
    <tr>
      <td>CONVERSION_RATE</td>
      <td>number(38,0)</td>
      <td>Rate used to convert the currency to the corporate currency.</td>
      <td>0.76728300</td>
    </tr>
    <tr>
      <td>IS_CURRENT</td>
      <td>boolean</td>
      <td>The semantics of this field have been corrupted. Do not use.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in the source system.</td>
      <td>2019-03-30 00:54:50.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in the source system.</td>
      <td>2019-03-30 00:54:50.000</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>boolean</td>
      <td>Whether or not the record is considered deleted in the source system.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_COSTS {#biz-costs}

Cost data imported from connected Ad Accounts or self reported marketing spend.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>A unique Id for the Cost record.</td>
      <td>aw.6601259029.285114995.21703163075.[AdWords Display]_2018-09-06</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified.</td>
      <td>2018-09-06 12:22:45.000</td>
    </tr>
    <tr>
      <td>COST_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the Cost was incurred (or attributed to).</td>
      <td>2018-09-06 00:00:00.000</td>
    </tr>
    <tr>
      <td>SOURCE</td>
      <td>varchar</td>
      <td>Source of the reported Cost.</td>
      <td>[AdWords Display]</td>
    </tr>
    <tr>
      <td>COST_IN_MICRO</td>
      <td>number(38,0)</td>
      <td>Cost amount in millions. User will need to divide the value by 1000000.</td>
      <td>1410000</td>
    </tr>
    <tr>
      <td>CLICKS</td>
      <td>number(38,0)</td>
      <td>Number of clicks reported for the group for the day.</td>
      <td>4</td>
    </tr>
    <tr>
      <td>IMPRESSIONS</td>
      <td>number(38,0)</td>
      <td>Number of impressions reported for the group for the day.</td>
      <td>4187</td>
    </tr>
    <tr>
      <td>ESTIMATED_TOTAL_POSSIBLE_IMPRESSIONS</td>
      <td>number(38,0)</td>
      <td>Total number of impressions estimated from DCM for the group for the day.</td>
      <td>5024</td>
    </tr>
    <tr>
      <td>AD_PROVIDER</td>
      <td>varchar</td>
      <td>Provider for which the Cost was pulled.</td>
      <td>Google</td>
    </tr>
    <tr>
      <td>CHANNEL_UNIQUE_ID</td>
      <td>varchar</td>
      <td>Id for the marketing Channel, created by [!DNL Marketo Measure].</td>
      <td>Display.Google</td>
    </tr>
    <tr>
      <td>CHANNEL_NAME</td>
      <td>varchar</td>
      <td>Name for the marketing Channel, created by the customer in the [!DNL Marketo Measure] app.</td>
      <td>Display.Google</td>
    </tr>
    <tr>
      <td>CHANNEL_IS_AGGREGATABLE_COST</td>
      <td>boolean</td>
      <td>Indicates if the row contains Cost which can be summed up by Channel. (i.e. to get Channel Cost, sum rows where this column equals true.)</td>
      <td>false</td>
    </tr>
    <tr>
      <td>ADVERTISER_UNIQUE_ID</td>
      <td>varchar</td>
      <td>Id of the Advertiser pulled from the Ad connection, specifically for Doubleclick connections.</td>
      <td>300181641</td>
    </tr>
    <tr>
      <td>ADVERTISER_NAME</td>
      <td>varchar</td>
      <td>Name of the Advertiser pulled from the Ad connection, specifically for Doubleclick connections.</td>
      <td>[!DNL Marketo Measure] Marketing Analytics</td>
    </tr>
    <tr>
      <td>ADVERTISER_IS_AGGREGATABLE_COST</td>
      <td>boolean</td>
      <td>Indicates if the row contains Cost which can be summed up by Advertiser. (i.e. to get Advertiser Cost, sum rows where this column equals true.)</td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Ad Account pulled from the Ad connection.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Account pulled from the Ad connection.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the row contains Cost which can be summed up by Account. (i.e. to get Account Cost, sum rows where this column equals true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Campaign pulled from the Ad connection.</p>
      </td>
      <td>
        <p>aw.6601259029.285114995</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Campaign pulled from the Ad connection.</p>
      </td>
      <td>
        <p>Partner Retargeting</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the row contains Cost which can be summed up by Campaign. (i.e. to get Campaign Cost, sum rows where this column equals true.)</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Ad Group pulled from the Ad connection.</p>
      </td>
      <td>
        <p>aw.6601259029.285114995.21703163075</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Group pulled from the Ad connection.</p>
      </td>
      <td>
        <p>Attribution Management Software | Phrase</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the row contains Cost which can be summed up by Ad Group. (i.e. to get Ad Group Cost, sum rows where this column equals true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Ad pulled from the Ad connection.</p>
      </td>
      <td>
        <p>dc.6114.9131003.24149929.467969200</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad pulled from the Ad connection.</p>
      </td>
      <td>
        <p>Ad name: Ad3-320x50.gif; 320 x 50</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the row contains Cost which can be summed up by Ad. (i.e. to get Ad Cost, sum rows where this column equals true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Creative pulled from the Ad connection.</p>
      </td>
      <td>
        <p>aw.6601259029.285114995.51749608028.266050115160</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Creative pulled from the Ad connection.</p>
      </td>
      <td>
        <p>Gartner Magic Quadrant 2019</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the row contains Cost which can be summed up by Creative. (i.e. to get Creative Cost, sum rows where this column equals true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Keyword pulled from the Ad connection.</p>
      </td>
      <td>
        <p>aw.6601259029.669328935.39419128772.99608705795</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Keyword pulled from the Ad connection.</p>
      </td>
      <td>
        <p>sfdc marketing attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the row contains Cost which can be summed up by Keyword. (i.e. to get Keyword Cost, sum rows where this column equals true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Placement pulled from the Ad connection.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Placement pulled from the Ad connection.</p>
      </td>
      <td>
        <p>roadblock</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the row contains Cost which can be summed up by Placement. (i.e. to get Placement Cost, sum rows where this column equals true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Site pulled from the Ad connection.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Site pulled from the Ad connection.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the row contains Cost which can be summed up by Site . (i.e. to get Site Cost, sum rows where this column equals true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the record is considered deleted in the source system .</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>ISO_CURRENCY_CODE</td>
      <td>varchar</td>
      <td>ISO code for the currency, imported from the source system.</td>
      <td>USD</td>
    </tr>
    <tr>
      <td>SOURCE_ID</td>
      <td>varchar</td>
      <td>Id for the Source from which the record originated.</td>
      <td>aw.3284209</td>
    </tr>
    <tr>
      <td>ROW_KEY</td>
      <td>number(38,0)</td>
      <td>
        <p>Foreign Key to the Biz_Facts view.</p>
      </td>
      <td>6008900572523230000</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ROW_KEY</p>
      </td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERTISER_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CURRENCY_ID</td>
      <td>number(38,0)</td>
      <td>Id value of the Currency for the record.</td>
      <td>
        <p>-3253183181619994799</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CREATIVES {#biz-creatives}

Creatives imported from any connected Ad Account.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the Creative.</p>
      </td>
      <td>
        <p>ba.3284209.132855866.4556709270.10426699711</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>varchar</td>
      <td>The Creative Id from the source system.</td>
      <td>
        <p>10426699711</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Ad Account from which the Creative was imported.</p>
      </td>
      <td>fb.106851586409075</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name for the Ad Account from which the Creative was imported.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Advertiser for the Creative, specifically for Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Advertiser for the Creative, specifically for Doubleclick.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Ad Group for the Creative.</p>
      </td>
      <td>fb.106851586409075.6052044288804.6052044290004</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Group for the Creative.</p>
      </td>
      <td>Ad Set for Ad B</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Campaign for the Creative.</p>
      </td>
      <td>
        <p>ba.3284209.132855866</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Campaign for the Creative.</p>
      </td>
      <td>
        <p>PipelineMarketing.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Creative is still active in the source system.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Creative has been deleted in the source system.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was last modified.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:25.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was first imported from the source system.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:25.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Creative, from the source system.</p>
      </td>
      <td>
        <p>PipelineMarketing.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Creative needs to be updated for [!DNL Marketo Measure] tagging.</p>
        <p>(Diagnostic field, used by internal processing.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>varchar</td>
      <td>Diagnostic field, for internal processing.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The main object or entity for this table. In this case, "Creative".</p>
      </td>
      <td>
        <p>Creative</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Provider for the Creative.</p>
      </td>
      <td>
        <p>BingAds</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The current version of the URL including all tags.</p>
        <p>(Diagnostic field, for internal processing.)</p>
      </td>
      <td>
        <p>cdn.adobe.com/redir?lp=http%3a%2f%2fwww.pipelinemarketing.com%2f&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}&amp;utm_content={adid}&amp;utm_term={keyword}&amp;utm_campaign=PipelineMarketing.com&amp;utm_source=bing&amp;utm_medium=cpc</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_DISPLAY</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The shortened and friendly URL that's displayed on the Creative.</p>
      </td>
      <td>
        <p>PipelineMarketing.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previous value for URL_CURRENT.</p>
        <p>(Diagnostic field, for internal processing.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_REQUESTED</p>
      </td>
      <td>varchar</td>
      <td>
        <p>What the URL will be decorated with [!DNL Marketo Measure] parameters.</p>
        <p>(Diagnostic field, for internal processing.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_SHORTENED</p>
      </td>
      <td>varchar</td>
      <td>The shortened and friendly URL that's displayed on the Creative. (Used for LinkedIn Ads only.)</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The type of Creative, which could be Text or Display</p>
      </td>
      <td>
        <p>Text</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_UPGRADED_URL</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the creative is using Upgraded URLs.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HEADLINE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The top line (headline) of the creative</p>
      </td>
      <td>
        <p>PipelineMarketing.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DESCRIPTION_LINE_1</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The copy from the first line of the creative</p>
      </td>
      <td>
        <p>Connect & Learn From Revenue-Driven B2B Marketers. Join the Community.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DESCRIPTION_LINE_2</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The copy from the second line of the creative</p>
      </td>
      <td>
        <p>Have You Used Analytics? Leave a Review Today!</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>varchar</td>
      <td>Diagnostics field, for internal processing.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>varchar</td>
      <td>Diagnostics field, for internal processing.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>varchar</td>
      <td>Diagnostics field, for internal processing.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Diagnostics field, for internal processing.</p>
      </td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SHARE_URN</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The share Id. (Used for LinkedIn Ads only.)</p>
      </td>
      <td>
        <p>urn:li:share:6376987561897848832</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>Foreign Key to the Biz_Facts view.</td>
      <td>6008900572523230000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CRM_EVENTS {#biz-crm-events}

Events imported from the source system. This table will be empty if Activities Sync is disabled.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>The Event Id from the source system.</p>
      </td>
      <td>
        <p>00U3100000VLUnEEAX</p>
      </td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the Event was created, from the source system.</p>
      </td>
      <td>
        <p>2016-12-12 19:32:53.000</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the Event was last modified, from the source system.</p>
      </td>
      <td>
        <p>2018-09-03 08:39:51.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Lead associated with the Event.</p>
      </td>
      <td>
        <p>00Q0Z000013eVrxUAE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Email for the Lead associated with the Event.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>CONTACT_ID</td>
      <td>varchar</td>
      <td>
        <p>Id for the Contact associated with the Event.</p>
      </td>
      <td>
        <p>0030Z00003OyjbOQAR</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Email for the Contact associated with the Event.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_COOKIE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The [!DNL Marketo Measure] Cookie Id used to populate from an integration partner to map an offline event to a web session. Requirement: Enable Call Tracking: True</p>
      </td>
      <td>
        <p>08c1063cb0a64349ad0d2d862f5cc700</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACTIVITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Activity Type Name, from the source system.</p>
      </td>
      <td>
        <p>Email</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EVENT_START_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Start date for the Event, one of the options used to determine the Touchpoint date.</p>
      </td>
      <td>
        <p>2016-12-16 19:30:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EVENT_END_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>End date for the Event, one of the options used to determine the Touchpoint date.</p>
      </td>
      <td>
        <p>2016-12-16 21:30:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Whether or not the record is considered deleted in the source system.</td>
      <td>
        <p>False</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Custom properties that [!DNL Marketo Measure] has imported from the source system, in JSON format.</td>
      <td>{"Contact_Type__c":"CMO","Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CRM_TASKS {#biz-crm-tasks}

Tasks imported from the source system. This table will populate if Activities Sync OR Call Tracking are enabled.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>The Task Id from the source system.</p>
      </td>
      <td>
        <p>00T0Z00004Rf62rUAB</p>
      </td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the Task was created, from the source system.</p>
      </td>
      <td>
        <p>2018-08-27 18:30:25.000</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the Task was last modified, from the source system.</p>
      </td>
      <td>
        <p>2018-08-27 18:31:53.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Lead associated with the Task.</p>
      </td>
      <td>
        <p>00Q0Z000013eVrxUAE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Email for the Lead associated with the Task.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>CONTACT_ID</td>
      <td>varchar</td>
      <td>
        <p>Id for the Contact associated with the Task.</p>
      </td>
      <td>
        <p>00331000038uGfhAAE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Email for the Contact associated with the Task.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_COOKIE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The [!DNL Marketo Measure] Cookie Id used to populate from an integration partner to map an offline event to a web session. Requirement: Enable Call Tracking: True</p>
      </td>
      <td>
        <p>08c1063cb0a64349ad0d2d862f5cc700</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACTIVITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Activity Type Name, from the source system.</p>
      </td>
      <td>
        <p>Call</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACTIVITY_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the Task occurred, one of the options used to determine the Touchpoint date.</p>
      </td>
      <td>
        <p>2018-08-27 07:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Whether or not the record is considered deleted in the source system.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Custom properties that [!DNL Marketo Measure] has imported from the source system, in JSON format.</td>
      <td>{"Contact_Type__c":"CMO", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CURRENCIES {#biz-currencies}

Table of all ISO currencies.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>number(38,0)</td>
      <td>A unique Id for the Currency record.</td>
      <td>139474809945095870</td>
    </tr>
    <tr>
      <td>ISO_CODE</td>
      <td>varchar</td>
      <td>ISO code for the Currency.</td>
      <td>USD</td>
    </tr>
    <tr>
      <td>IS_CORPORATE</td>
      <td>boolean</td>
      <td>Designates if the Currency is the corporate Currency.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>IS_ENABLED</td>
      <td>boolean</td>
      <td>Designates if the Currency is enabled in the source system.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modefied in [!DNL Marketo Measure].</td>
      <td>2018-08-27 18:30:25.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE_CRM</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in the source system.</td>
      <td>2018-08-27 18:30:25.000</td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in [!DNL Marketo Measure]</td>
      <td>2018-08-27 18:30:25.000</td>
    </tr>
    <tr>
      <td>CREATED_DATE_CRM</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in the source system.</td>
      <td>2018-08-27 18:30:25.000</td>
    </tr>
    <tr>
      <td>ISO_NUMERIC</td>
      <td>number(38,0)</td>
      <td>ISO standard numeric code.</td>
      <td>048</td>
    </tr>
    <tr>
      <td>EXPONENT</td>
      <td>number(38,0)</td>
      <td>The number of decimal places between the smallest defined Currency unit and a whole Currency unit.</td>
      <td>2</td>
    </tr>
    <tr>
      <td>NAME</td>
      <td>varchar</td>
      <td>Name of the Currency.</td>
      <td>Argentine Peso</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CUSTOMER_AB_TESTS {#biz-customer-ab-tests}

AB Tests recorded. This table will be empty if AB Tests are not enabled.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first cookie id of the related visitor id.</p>
      </td>
      <td>v_36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The recorded cookie id at the time the event was logged.</p>
      </td>
      <td>36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the chat was logged.</p>
      </td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>IP_ADDRESS</td>
      <td>varchar</td>
      <td>
        <p>The recorded IP address at the time the experiment was logged.</p>
      </td>
      <td>192.0.2.1</td>
    </tr>
    <tr>
      <td>
        <p>EXPERIMENT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The id of the experiment pulled from the AB test platform.</p>
      </td>
      <td>123</td>
    </tr>
    <tr>
      <td>
        <p>EXPERIMENT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The name of the experiment pulled from the AB test platform.</p>
      </td>
      <td>Experiment A</td>
    </tr>
    <tr>
      <td>
        <p>VARIATION_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The variation id of the experiment pulled from the AB test platform.</p>
      </td>
      <td>456</td>
    </tr>
    <tr>
      <td>
        <p>VARIATION_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The variation name of the experiment pulled from the AB test platform.</p>
      </td>
      <td>Blue Test</td>
    </tr>
    <tr>
      <td>
        <p>ABTEST_USER_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The id of the user who was served the experiment pulled from the AB test platform.</p>
      </td>
      <td>584d64et</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the record was deleted, used for diagnostics and auditing.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CUSTOMER_EVENTS {#biz-customer-events}

Web events that have been recorded using custom events in the Javascript. This table will be empty if [!DNL Marketo Measure] Events are not enabled.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first cookie id of the related visitor id.</p>
      </td>
      <td>v_36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The recorded cookie id at the time the event was triggered from the custom javascript.</p>
      </td>
      <td>36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>The date the event was triggered from the custom javascript.</p>
      </td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>The last date the record was modified.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>
        <p>IP_ADDRESS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The recorded IP address at the time the event was triggered from the custom javascript.</p>
      </td>
      <td>192.0.2.1</td>
    </tr>
    <tr>
      <td>
        <p>KEY</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The name given to the event which was triggered from the custom javascript.</p>
      </td>
      <td>Video View</td>
    </tr>
    <tr>
      <td>
        <p>VALUE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The value given to the event which was triggered from the custom javascript.</p>
      </td>
      <td>75% viewed</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the record was deleted, used for diagnostics and auditing.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_CUSTOM_LANDING_PAGES {#biz-custom-landing-pages}

Landing Pages downloaded from any connected Ad Account.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the record.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>Id for the Ad Account from which the landing page was imported.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>Name of the Ad Account from which the landing page was imported</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Advertiser for the landing page, specifically for Doubleclick.</p>
      </td>
      <td>300181641</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Advertiser for the landing page, specifically for Doubleclick.</p>
      </td>
      <td>
        <p>Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>Id of the Ad Group for the landing page.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Group for the landing page.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Campaign for the landing page.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Campaign for the landing page.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>The last modified date of the row</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>timestamp_ntz</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_DISPLAY_ID</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_ID</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_EMAIL_TO_VISITOR_IDS {#biz-email-to-visitor-ids}

Mapping table for email addresses and visitor ids.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>A unique Id for the record.</td>
      <td>
        <p>0013800001MMPPiAAP_person@adobe.com|2022-01-05 17:22:13.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>A known email address that's tied to a given visitor Id from a session</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first cookie of the related visitor Id</p>
      </td>
      <td>
        <p>v_36ec805b4db344d6e92c972c86aee34a</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>The last modified date of the row</p>
      </td>
      <td>
        <p>2018-08-14 23:55:03.000</p>
      </td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>The created date of the row</p>
      </td>
      <td>
        <p>2018-08-14 23:55:03.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the record is considered deleted, used for diagnostics and auditing.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>IS_IGNORE</td>
      <td>boolean</td>
      <td>Indicates if the email or visitor id is considered noise or spam, used for internal processing.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_FACTS {#biz-facts}

Unions together Impressions, Page Views, Visits, Form Submits, User Touchpoints, Touchpoint (BT), Attribution Touchpoints (BAT), and Cost data. Used internally to support [!DNL Marketo Measure] reporting.

>[!IMPORTANT]
>
>Marketo Measure will be deprecating this table in mid-2024. If you wish to create it on your side, run [this SQL query](/help/marketo-measure-data-warehouse/assets/BIZ_FACTS.sql).

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
      <td>COST_KEY</td>
      <td>number(38,0)</td>
      <td>Used to join to the Costs table.</td>
      <td>2672629811884560039</td>
    </tr>
    <tr>
      <td>ATP_KEY</td>
      <td>number(38,0)</td>
      <td>Used to join to the Attribution Touchpoints table.</td>
      <td>2672629811884560039</td>
    </tr>
    <tr>
      <td>TP_KEY</td>
      <td>number(38,0)</td>
      <td>Used to join to the Touchpoints or User Touchpoints tables.</td>
      <td>5028390208679093800</td>
    </tr>
    <tr>
      <td>PAGE_VIEW_KEY</td>
      <td>number(38,0)</td>
      <td>Used to join to the Page Views table.</td>
      <td>-8044063242541720607</td>
    </tr>
    <tr>
      <td>SESSION_KEY</td>
      <td>number(38,0)</td>
      <td>Used to join to the Sessions table.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>VISITOR_ID</td>
      <td>varchar</td>
      <td>The first cookie id of the related visitor id.</td>
      <td>v_530d8334c455460df0d48f48270a4b23</td>
    </tr>
    <tr>
      <td>COOKIE_ID</td>
      <td>varchar</td>
      <td>The recorded cookie id at the time the event was logged.</td>
      <td>530d8334c455460df0d48f48270a4b23</td>
    </tr>
    <tr>
      <td>FORM_SUBMIT_KEY</td>
      <td>number(38,0)</td>
      <td>Used to join to the Form Submits table.</td>
      <td>-8659572802702769670</td>
    </tr>
    <tr>
      <td>IMPRESSION_KEY</td>
      <td>number(38,0)</td>
      <td>Used to join to the Impressions table.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CURRENT_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Used to join to the Urls table.</td>
      <td>4079876040770132443</td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Used to join to the Urls table.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>FORM_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Used to join to the Urls table.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>AD_PROVIDER_KEY</td>
      <td>number(38,0)</td>
      <td>Used to join to the Ad Providers table.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>
        <p>CHANNEL_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Used to join to the Channels table.</p>
      </td>
      <td>
        <p>-1921844114032355934</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Used to join to the Ad Campaigns table.</p>
      </td>
      <td>
        <p>252687814634577606</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Used to join to the Keywords table.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Used to join to the Ads table.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Used to join to the Ad Groups table.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Used to join to the Creatives table.</p>
      </td>
      <td>
        <p>-2333871387956621113</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Used to join to the Sites table.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Used to join to the Advertisers table.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Used to join to the Ad Accounts table.</p>
      </td>
      <td>
        <p>1825012532740770032</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Used to join to the Placements table.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>CATEGORY_01_KEY</td>
      <td>nubmer(38,0)</td>
      <td>Used to join to the Segments table.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_02_KEY</td>
      <td>nubmer(38,0)</td>
      <td>Used to join to the Segments table.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_03_KEY</td>
      <td>nubmer(38,0)</td>
      <td>Used to join to the Segments table.</td>
      <td>-2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_04_KEY</td>
      <td>nubmer(38,0)</td>
      <td>Used to join to the Segments table.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_05_KEY</td>
      <td>nubmer(38,0)</td>
      <td>Used to join to the Segments table.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_06_KEY</td>
      <td>nubmer(38,0)</td>
      <td>Used to join to the Segments table.</td>
      <td>-2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_07_KEY</td>
      <td>nubmer(38,0)</td>
      <td>Used to join to the Segments table.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_08_KEY</td>
      <td>nubmer(38,0)</td>
      <td>Used to join to the Segments table.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_09_KEY</td>
      <td>nubmer(38,0)</td>
      <td>Used to join to the Segments table.</td>
      <td>2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_10_KEY</td>
      <td>nubmer(38,0)</td>
      <td>Used to join to the Segments table.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_11_KEY</td>
      <td>nubmer(38,0)</td>
      <td>Used to join to the Segments table.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_12_KEY</td>
      <td>nubmer(38,0)</td>
      <td>Used to join to the Segments table.</td>
      <td>-2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_13_KEY</td>
      <td>nubmer(38,0)</td>
      <td>Used to join to the Segments table.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_14_KEY</td>
      <td>nubmer(38,0)</td>
      <td>Used to join to the Segments table.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_15_KEY</td>
      <td>nubmer(38,0)</td>
      <td>Used to join to the Segments table.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>TYPE</td>
      <td>number(38,0)</td>
      <td>Indicates the fact type of the row. 1 = Buyer Attribution Touchpoint 2 = Cost 3 = Buyer Touchpoint 4 = User Touchpoint 5 = Page View 6 = Session 7 = Form Submit 8 = Impression</td>
      <td>3</td>
    </tr>
    <tr>
      <td>DATE</td>
      <td>date</td>
      <td>Date the event occurred.</td>
      <td>2018-08-28</td>
    </tr>
    <tr>
      <td>TIMESTAMP</td>
      <td>timestamp_ntz</td>
      <td>Date and time the event occurred.</td>
      <td>2018-08-28 19:39:15.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the row was last modified.</p>
      </td>
      <td>
        <p>2018-08-29 00:46:47.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COST_IN_MICRO</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Cost amount in millions. User will need to divide the value by 1000000.</p>
      </td>
      <td>
        <p>27370000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IMPRESSIONS</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Number of impressions reported for the group for the day.</p>
      </td>
      <td>
        <p>340</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLICKS</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Number of clicks reported for the group for the day.</p>
      </td>
      <td>4</td>
    </tr>
    <tr>
      <td>
        <p>FIRST_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>The calculated percentage allocated to this touchpoint because it's a first touch.</p>
      </td>
      <td>0.0000000000000000000</td>
    </tr>
    <tr>
      <td>
        <p>LAST_ANON_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>The calculated percentage allocated to this touchpoint because it's a lead creation touch.</p>
      </td>
      <td>100.0000000000000000000</td>
    </tr>
    <tr>
      <td>
        <p>U_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>The calculated percentage that gets allocated to this touchpoint because it's part of a u-shaped touch.</p>
      </td>
      <td>
        <p>100.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>W_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>The calculated percentage that gets allocated to this touchpoint because it's part of a w-shaped touch.</p>
      </td>
      <td>
        <p>0.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FULL_PATH_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>The calculated percentage that gets allocated to this touchpoint because it's part of a full path model.</p>
      </td>
      <td>
        <p>0.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CUSTOM_MODEL_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>The calculated percentage that gets allocated to this touchpoint because it's part of a custom model.</p>
      </td>
      <td>
        <p>0.0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AMOUNT</p>
      </td>
      <td>
        <p>number(38,8)</p>
      </td>
      <td>
        <p>Amount of the Opportuity, from the source system.</p>
      </td>
      <td>
        <p>42000.00000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_WON</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the Opportunity has been moved to a stage which is classified as won.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_OPP_CLOSED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the Opportunity has moved to a stage which is classifed as closed.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPPORTUNITY_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Opportunity Id from the source system.</p>
      </td>
      <td>
        <p>0060Z00000nFEfEQAW</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPP_CREATED_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the Opportunity was created, from the source system.</p>
      </td>
      <td>
        <p>2018-08-31 15:45:47.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPP_CLOSE_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Close date for the Opportunity, from the source system.</p>
      </td>
      <td>
        <p>2018-12-31 07:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_CREATED_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the Contact record was created, from the source system.</p>
      </td>
      <td>2017-04-28 00:21:52.000</td>
    </tr>
    <tr>
      <td>CONTACT_ID</td>
      <td>varchar</td>
      <td>
        <p>Contact Id from the source system.</p>
      </td>
      <td>
        <p>0030Z00003ORVJmQAP</p>
      </td>
    </tr>
    <tr>
      <td>EMAIL</td>
      <td>varchar</td>
      <td>Email address for the record.</td>
      <td>personb@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>LEAD_CREATED_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the Lead record was created, from the source system.</p>
      </td>
      <td>
        <p>2017-04-28 00:21:52.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Lead Id from the source system.</p>
      </td>
      <td>
        <p>00Q3100001GMPIsEAP</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_AD</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the row contains Cost which can be summed up by Ad. (i.e. to get Ad Cost, sum rows where this column equals true.)</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_ADVERTISER</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the row contains Cost which can be summed up by Advertiser. (i.e. to get Advertiser Cost, sum rows where this column equals true.)</p>
      </td>
      <td>true</td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_AD_ACCOUNT</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the row contains Cost which can be summed up by Account. (i.e. to get Account Cost, sum rows where this column equals true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_AD_GROUP</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the row contains Cost which can be summed up by Ad Group. (i.e. to get Ad Group Cost, sum rows where this column equals true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_CAMPAIGN</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the row contains Cost which can be summed up by Campaign. (i.e. to get Campaign Cost, sum rows where this column equals true.)</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_CHANNEL</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the row contains Cost which can be summed up by Channel. (i.e. to get Channel Cost, sum rows where this column equals true.)</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_CREATIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the row contains Cost which can be summed up by Creative. (i.e. to get Creative Cost, sum rows where this column equals true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_KEYWORD</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the row contains Cost which can be summed up by Keyword. (i.e. to get Keyword Cost, sum rows where this column equals true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_PLACEMENT</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the row contains Cost which can be summed up by Placement. (i.e. to get Placement Cost, sum rows where this column equals true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_SITE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the row contains Cost which can be summed up by Site . (i.e. to get Site Cost, sum rows where this column equals true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the record was deleted, used as an audit trail.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>CURRENCY_ID</td>
      <td>number(38,0)</td>
      <td>Id value of the Currency for the record.</td>
      <td>-3253183181619994799</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_FORM_SUBMITS {#biz-forms-submits}

Captured Form Submissions.

<table>
  <tbody>
    <tr>
      <th>
        Column
      </th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the Form Submit.</p>
      </td>
      <td>
        <p>2018-08-06:01-35-21-927280.9bc63c34482f4</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The recorded cookie id at the time the Form Submit was logged.</p>
      </td>
      <td>
        <p>9bc63c34482f4de8c2e3b9d8d9f0df56</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first cookie id of the related visitor id. If the record is marked as is_duplicated = true, this field will be null.</p>
      </td>
      <td>
        <p>v_9bc63c34482f4de8c2e3b9d8d9f0df56</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The recorded Session Id at the time the Form Submit was logged. If the record is marked as is_duplicated = true, this field will be null.</p>
      </td>
      <td>
        <p>2018-08-06:01-35-24-1231230.9bc63c34482f</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the Form was submitted.</p>
      </td>
      <td>
        <p>2018-08-06 01:35:21.000</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was last modified.</p>
      </td>
      <td>
        <p>2018-08-07 23:09:52.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>URL where the Form was submitted, without query parameters.</p>
      </td>
      <td>
        <p>https://info.adobe.com/webinar-marketo-measure-impact</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>URL where the Form was submitted, including any query parameters.</p>
      </td>
      <td>
        <p>https://info.adobe.com/webinar-marketo-measure-impact?utm_source=partner&amp;mkt_tok=eyJpIjoiTnpBeE1EVml PV0UyWlRObSIsInQiOiI3MEFIek04ZVJiWm9renc1Z29RXC9kXC92YkxycFRYclE0MVhOaH Nwdml3YTZBZDdPdXh4Q0RmcnBJWXhwZTF1Z0RrbXlDVmxJNzIwNkhW</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IP_ADDRESS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The recorded IP address at the time the Form was submitted.</p>
      </td>
      <td>
        <p>174.127.184.158</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TYPE</p>
      </td>
      <td>varchar</td>
      <td>Indicates the type of Event.</td>
      <td>
        <p>FormSubmit</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>USER_AGENT_STRING</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Device and browser recorded at the time of the Form Submit.</p>
      </td>
      <td>
        <p>Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/11.1.2 Safari/605.1.15</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_SEQUENCE</p>
      </td>
      <td>varchar</td>
      <td>Indicates the order in which the Page View occurred in the Session.</td>
      <td>
        <p>4</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_RANDOM</p>
      </td>
      <td>varchar</td>
      <td>Used for internal auditing and processing.</td>
      <td>
        <p>20042b6b7af44512b43f6244d86faf4c</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DUPLICATED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Indicates if the record is considered a duplicate.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PROCESSED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Used for internal processing.</td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Email address provided on the Form, as captured from the javascript.</p>
      </td>
      <td>
        <p>personc@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_TYPE</p>
      </td>
      <td>varchar</td>
      <td>Indicates the type of Form submitted.</td>
      <td>
        <p>Chat</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_SOURCE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Indicates the method in which the Form was recognized, such as onSubmit or AjaxIntercept</p>
      </td>
      <td>
        <p>onSubmit</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_IDENTIFIER</p>
      </td>
      <td>varchar</td>
      <td>Id value for the Form.</td>
      <td>
        <p>-956012665</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Foreign Key to the Biz_Facts view.</p>
      </td>
      <td>
        <p>-6255315750913680000</p>
      </td>
    </tr>
    <tr>
      <td>CURRENT_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Foreign Key to the Url table.</td>
      <td>6255315750913680000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_IMPRESSIONS {#biz-impressions}

Impressions fired and recorded. This table requires a DoubleClick connection and Enable View Through set to True.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the Impression.</p>
      </td>
      <td>
        <p>6acd7b43290490fe5c53eed31281d09a|2020-05-18:22:20:59|0000|0|2869369052</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The recorded cookie id at the time of the Impression.</p>
      </td>
      <td>08c1063cb0a64349ad0d2d862f5cc700</td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first cookie id of the related visitor id.</p>
      </td>
      <td>v_08c1063cb0a64349ad0d2d862f5cc700</td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The recorded Session Id at the time the Impression was logged.</p>
      </td>
      <td>2018-08-06:01-35-24-1231230.9bc63c34482f</td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the Impression was served.</p>
      </td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was last modified.</p>
      </td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>URL where the Impression was served, without query parameters.</p>
      </td>
      <td>https://info.adobe.com/webinar-marketo-measure-impact</td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>URL where the Impression was served, including any query parameters.</p>
      </td>
      <td>https://info.adobe.com/webinar-marketo-measure-impact?utm_source=partner&amp;mkt_tok=eyJpIjoiTnpBeE1EVml PV0UyWlRObSIsInQiOiI3MEFIek04ZVJiWm9renc1Z29RXC9kXC92YkxycFRYclE0MVhOaH Nwdml3YTZBZDdPdXh4Q0RmcnBJWXhwZTF1Z0RrbXlDVmxJNzIwNkhW</td>
    </tr>
    <tr>
      <td>
        <p>IP_ADDRESS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The recorded IP address at the time of the Impression.</p>
      </td>
      <td>174.127.184.158</td>
    </tr>
    <tr>
      <td>
        <p>TYPE</p>
      </td>
      <td>varchar</td>
      <td>Indicates the type of Event.</td>
      <td>Impression</td>
    </tr>
    <tr>
      <td>
        <p>USER_AGENT_STRING</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Device and browser recorded at the time of the Form Submit.</p>
      </td>
      <td>
        <p>Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/11.1.2 Safari/605.1.15</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_SEQUENCE</p>
      </td>
      <td>varchar</td>
      <td>Indicates the order in which the Page View occurred in the Session.</td>
      <td>
        <p>4</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_RANDOM</p>
      </td>
      <td>varchar</td>
      <td>Used for internal auditing and processing.</td>
      <td>
        <p>20042b6b7af44512b43f6244d86faf4c</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DUPLICATED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Indicates if the record is considered a duplicate.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PROCESSED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Used for internal processing.</td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Typically the external landing page immediately before the user comes onto the website. Referred to in the CRM as "Referrer Page".</p>
      </td>
      <td>https://www.linkedin.com/</td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE-RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Typically the external landing page immediately before the user comes onto the website. A raw referrer page may contain query parameters in the URL. Referred to in the CRM as "Referrer Page - Raw".</p>
      </td>
      <td>https://www.linkedin.com/</td>
    </tr>
    <tr>
      <td>
        <p>CITY</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The resolved city from the IP address.</p>
      </td>
      <td>
        <p>Seattle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REGION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The resolved region from the IP address.</p>
      </td>
      <td>
        <p>Washington</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COUNTRY</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The resolved country from the IP address.</p>
      </td>
      <td>
        <p>United States</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ISP_NAME</p>
      </td>
      <td>varchar</td>
      <td>Expected to be null since the field is obsolete.</td>
      <td>NULL</td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Ad platform [!DNL Marketo Measure] was able to resolve from, typically one of our integration partners.</p>
      </td>
      <td>Google</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Ad Account in which the ad was resolved from.</p>
      </td>
      <td>aw.6601259029</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Account in which the ad was resolved from.</p>
      </td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Advertiser from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Advertiser from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Market Measure Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Site from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Site from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Placement from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Placement from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>roadblock</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Campaign from the Ad Account in which the Ad was resolved from.</p>
      </td>
      <td>aw.6601259029.317738075</td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Campaign from the Ad Account in which the Ad was resolved from.</p>
      </td>
      <td>Marketing Attribution</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Ad Group in the Doubleclick hierarchy for impressions</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Ad Group in the Doubleclick hierarchy for impressions</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Ad from the Ad Account in which the Ad was resolved from. This applies to Doubleclick Campaign Manager and Facebook (display).</p>
      </td>
      <td>
        <p>68035923</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad from the Ad Account in which the Ad was resolved from. This applies to Doubleclick Campaign Manager and Facebook (display).</p>
      </td>
      <td>
        <p>centurylink_banner_98121</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Creative in the Doubleclick hierarchy for Impressions.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Creative in the Doubleclick hierarchy for Impressions.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Creative in the Doubleclick hierarchy for Impressions.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Creative in the Doubleclick hierarchy for Impressions.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Creative in the Doubleclick hierarchy for Impressions.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Creative in the Doubleclick hierarchy for Impressions.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Keyword in the Doubleclick hierarchy for Impressions.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Keyword in the Doubleclick hierarchy for Impressions.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Keyword in the Doubleclick hierarchy for Impressions.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected browser that the user was on during the session.</p>
      </td>
      <td>
        <p>Chrome</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_VERSION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected version of the browser that the user was on during the session.</p>
      </td>
      <td>
        <p>58</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected platform that the user was on during the session.</p>
      </td>
      <td>
        <p>Mac</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_VERSION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected version of the platform that the user was on during the session.</p>
      </td>
      <td>
        <p>10_12</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Foreign Key to the BIZ_FACTS view.</p>
      </td>
      <td>
        <p>-2712935512233520000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE_KEY</p>
      </td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERTISER_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_KEYWORDS {#biz-keywords}

Keywords imported from any connected Ad Account.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the Keyword.</p>
      </td>
      <td>
        <p>ba.3284209.132630532.3646889365.39464932147</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>varchar</td>
      <td>The Keyword Id from the source system.</td>
      <td>
        <p>39464932147</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Ad Account from which the Keyword was imported.</p>
      </td>
      <td>fb.106851586409075</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Account from which the Keyword was imported.</p>
      </td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Keyword in the Doubleclick hierarchy for Impressions.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Keyword in the Doubleclick hierarchy for Impressions.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Ad Group for the Keyword.</p>
      </td>
      <td>
        <p>ba.3284209.132630532.3646889365</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Group for the Keyword.</p>
      </td>
      <td>
        <p>Revenue Attribution - B2B</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Campaign for the Keyword.</p>
      </td>
      <td>
        <p>ba.3284209.132630532</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Campaign for the Keyword.</p>
      </td>
      <td>
        <p>Revenue Attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Keyword is still active in the source system.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Keyword has been deleted in the source system.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was last modified.</p>
      </td>
      <td>2018-08-02 06:37:29.000</td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was first imported from the source system.</p>
      </td>
      <td>
        <p>2018-08-02 06:37:29.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Keyword, from the source system.</p>
      </td>
      <td>
        <p>[revenue attribution b2b]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Keyword needs to be updated for [!DNL Marketo Measure] tagging.</p>
        <p>(Diagnostic field, used for internal processing.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>varchar</td>
      <td>Diagnostic field, used for internal processing.</td>
      <td>
        <p>ba.3284209.132630532.3646889365</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The main object or entity for this table. In this case, "Keyword".</p>
      </td>
      <td>
        <p>Keyword</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Provider for the Keyword.</p>
      </td>
      <td>
        <p>BingAds</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The URL for the landing page.</p>
        <p>(Diagnostic field, for internal processing.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previous value for URL_CURRENT.</p>
        <p>(Diagnostic field, for internal processing.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>URL_REQUESTED</td>
      <td>varchar</td>
      <td>
        <p>The URL for the landing page with [!DNL Marketo Measure] parameters.</p>
        <p>(Diagnostic field, for internal processing.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_UPGRADED_URL</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Diagnostic field, for internal processing.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WORD</p>
      </td>
      <td>varchar</td>
      <td>The search phase the user entered.</td>
      <td>
        <p>revenue attribution b2b</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MATCH_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The type of match that was found between the search phrase and the Keyword.</p>
      </td>
      <td>
        <p>Exact</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>varchar</td>
      <td>Used for internal diagnostics.</td>
      <td>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>varchar</td>
      <td>Used for internal diagnostics.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>varchar</td>
      <td>Used for internal diagnostics.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>varchar</td>
      <td>The URL tracking template [!DNL Marketo Measure] added to the Keyword.</td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Foreign Key to the Biz_Facts view.</p>
      </td>
      <td>-2712935512233520000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_LANDING_PAGES {#biz-landing-pages}

Landing Pages imported from any connected Ad Account.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the Landing Page.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>Id for the Ad Account from which the landing page was imported.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>Name of the Ad Account from which the landing page was imported.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Advertiser for the landing page, specifically for Doubleclick.</p>
      </td>
      <td>300181641</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Advertiser for the landing page, specifically for Doubleclick.</p>
      </td>
      <td>Marketing Analytics</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>Id of the Ad Group for the landing page.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>Name of the Ad Group for the landing page.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>Id of the Campaign for the landing page.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
      <td>Name of the Campaign for the landing page.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>The last modified date of the row.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>timestamp_ntz</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_REQUESTED</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_LEADS {#biz-leads}

Leads imported from the source system.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>The Lead Id from the source system.</p>
      </td>
      <td>
        <p>00Q0Z00001MZcj8UAD</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the Lead record was last modified, from the source system.</p>
      </td>
      <td>
        <p>2018-08-27 21:52:10.000</p>
      </td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the Lead record was created, from the source system.</p>
      </td>
      <td>2018-08-27 21:52:10.000</td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Email address of the Lead, from the source system.</p>
      </td>
      <td>persona@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>WEB_SITE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Website entered for the Lead, from the source system, used for Lead2Account mapping.</p>
      </td>
      <td>
        <p>adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COMPANY</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Company name entered for the Lead, from the source system, used for Lead2Account mapping.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SOURCE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Source in which the Lead was created.</p>
      </td>
      <td>
        <p>Advertisement</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_CONVERTED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Lead has been converted to a Contact.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_OPPORTUNITY_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the related Opportunity once the Lead has been converted.</p>
      </td>
      <td>
        <p>0013100001b44aGAAQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the Lead was converted to a Contact.</p>
      </td>
      <td>
        <p>2018-08-27 07:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_CONTACT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the related Contact once the Lead has been converted.</p>
      </td>
      <td>
        <p>0030Z00003Oyp25QAB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNTID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the mapped Account. Requirements: Enable ABM</p>
      </td>
      <td>
        <p>0010Z0000236F9GQAU</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Current stage of the Lead, recognized as a custom stage which can be created in the [!DNL Marketo Measure] application.</p>
      </td>
      <td>
        <p>Demo Scheduled</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE_PREVIOUS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>All previous stages for the Lead, recognized as custom stages which can be created in the [!DNL Marketo Measure] application.</p>
      </td>
      <td>
        <p>MQL</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ODDS_OF_CONVERSION</p>
      </td>
      <td>
        <p>number(38,19)</p>
      </td>
      <td>
        <p>This feature has been deprecated. Do not use this column.</p>
      </td>
      <td>
        <p>N/A</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SCORE_MODEL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>(deprecated)</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SCORE_RESULTS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>(deprecated)</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_COOKIE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The [!DNL Marketo Measure] Cookie Id used to populate from an integration partner to map an offline event to a web session. Requirement: Enable Call Tracking: True</p>
      </td>
      <td>
        <p>08c1063cb0a64349ad0d2d862f5cc700</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the record is deleted in the source system.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Foreign Key to the Biz_Facts view.</p>
      </td>
      <td>3263982503087870000</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Custom properties that [!DNL Marketo Measure] has imported from the source system , in JSON format.</td>
      <td>{"Lead_Type__c":"Sales Created", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>IS_DUPLICATE</td>
      <td>boolean</td>
      <td>Used to de-duplicate records if both a CRM and Marketo integration are set up. If there are duplicates, the Marketo Lead is marked true.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>SOURCE_SYSTEM</td>
      <td>varchar</td>
      <td>Indicates if the record came from a CRM or a Marketo integration.</td>
      <td>Crm</td>
    </tr>
    <tr>
      <td>OTHER_SYSTEM_ID</td>
      <td>varchar</td>
      <td>Maps a person from a Marketo integration with a Lead from a CRM integration. If both a CRM and Marketo integration exist, the value is the corresponding Id.</td>
      <td>1234</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_LEAD_STAGE_TRANSITIONS {#biz-lead-stage-transitions}

Stage transitions for Leads or Contacts.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the transition.</p>
      </td>
      <td>
        <p>ST_0030Z00003FhkRXQAZ__FT-1_TP2_Person_0030Z00003FhkRXQAZ_2018-08-27:17-05-45-9474800.0d5c18c29d7b</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The provided email address for the related Lead/Contact.</p>
      </td>
      <td>
        <p>persone@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Lead associated to the transition.</p>
      </td>
      <td>
        <p>00Q3100001Fx6AlEAJ</p>
      </td>
    </tr>
    <tr>
      <td>CONTACT_ID</td>
      <td>varchar</td>
      <td>
        <p>Id for the Contact associated to the transition.</p>
      </td>
      <td>
        <p>0033100003Aq9grAAB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TOUCHPOINT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Buyer Touchpoint tied to the transition.</p>
      </td>
      <td>
        <p>TP2_Person_00Q3100001Fx6AlEAJ_2018-08-28:14-41-06-1674260.d00ceb09fbd3</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRANSITION_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record transitioned into the stage.</p>
      </td>
      <td>
        <p>2018-08-27 16:05:34.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id value of the stage for the transition.</p>
      </td>
      <td>
        <p>_bizible_FT</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the stage for the transition.</p>
      </td>
      <td>
        <p>FT</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>RANK</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>The numerical rank of the stage, as ordered in the [!DNL Marketo Measure] Stage Mapping settings.</p>
      </td>
      <td>
        <p>5</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>INDEX</p>
      </td>
      <td>
        <p>varchar(1)</p>
      </td>
      <td>
        <p>Used in internal processing for indexing and ordering boomerang stages.</p>
      </td>
      <td>
        <p>1</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_INDEX</p>
      </td>
      <td>
        <p>varchar(1)</p>
      </td>
      <td>Used in internal processing for indexing and ordering boomerang stages.</td>
      <td>
        <p>1</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PENDING</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the touchpoint is considered pending and not yet closed. This only appears for customers with full path attribution model.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_NON_TRANSITIONAL</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the the row is tied to a milestone stage transition. For example, if there are 3 stages/entries (FT, LC, MQL) and 4 touchpoints, the 1 touchpoint without a stage on it is considered "non-transitional" so the value would equal true.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PREVIOUS_STAGE_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Transition date for the previous stage, according to the stage rank.</p>
      </td>
      <td>
        <p>2017-11-28 21:26:44.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEXT_STAGE_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Transition date for the next stage, according to the stage rank.</p>
      </td>
      <td>
        <p>2017-12-11 22:39:17.000</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Last modified date of the record.</p>
      </td>
      <td>
        <p>2018-08-28 15:31:10.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the transition record is considered deleted.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_OPPORTUNITIES {#biz-opportunities}

Opportunities imported from the source system.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>The Opportunity Id from the source system.</p>
      </td>
      <td>
        <p>0060Z00000o89I4QAI</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>The last modified date of the Opportunity, from the source system.</p>
      </td>
      <td>2017-11-28 21:26:44.000</td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>The created date of the Opportunity, from the source system.</p>
      </td>
      <td>2017-11-28 21:26:44.000</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the related Account.</p>
      </td>
      <td>
        <p>001i000000qbyeoAAA</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The Opportunity Name, from the source system.</p>
      </td>
      <td>
        <p>Mareketo Measure Renewal</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_WON</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the Opportunity has moved to a stage considered won.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_CLOSED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the Opportunity has moved to a stage considered closed.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLOSE_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Anticipated or actual close date of the Opportunity, from the source system.</p>
      </td>
      <td>
        <p>2019-08-28 07:00:00.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_CUSTOM_MODEL_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>(deprecated)</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AMOUNT</p>
      </td>
      <td>
        <p>number(38,8)</p>
      </td>
      <td>
        <p>Deal amount which is expected or closed from the Opportunity, from the source system.</p>
      </td>
      <td>
        <p>8988.00000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_FROM_LEAD_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The Id of the related Lead that had converted into this Opportunity.</p>
        <p>Note that this field is not set and returns null in Snowflake for all customers.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_FROM_LEAD_EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The email of the related Lead that had converted into this Opportunity.</p>
        <p>Note that this field is not set and returns null in Snowflake for all customers.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PRIMARY_CONTACT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>If Primary Contact Role is used, the Id of the related Contact listed as the primary contact role.</p>
      </td>
      <td>
        <p>00331000038uGfhAAE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PRIMARY_CONTACT_EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>If Primary Contact Role is used, the email of the related Contact listed as the primary contact role.</p>
      </td>
      <td>
        <p>personb@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ODDS_OF_CONVERSION</p>
      </td>
      <td>
        <p>number(38,19)</p>
      </td>
      <td>
        <p>This feature has been deprecated. Do not use this column.</p>
      </td>
      <td>
        <p>N/A</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Current stage of the Opportunity, as defined in the [!DNL Marketo Measure] application.</p>
      </td>
      <td>
        <p>DM Demo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE_PREVIOUS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>A string of all stages the Opportunity has previously gone through, as defined in the [!DNL Marketo Measure] application.</p>
      </td>
      <td>
        <p>Qualified Discovery, Demo Scheduled</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the record is deleted in the source system.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Foreign Key to the Biz_Facts view.</p>
      </td>
      <td>
        <p>4609512587744160000</p>
      </td>
    </tr>
    <tr>
      <td>CURRENCY_ISO_CODE</td>
      <td>varchar</td>
      <td>ISO code for the currency, imported from the source system.</td>
      <td>USD</td>
    </tr>
    <tr>
      <td>CURRENCY_ID</td>
      <td>number(38,0)</td>
      <td>Id value of the Currency for the record.</td>
      <td>4609512587744160000</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Custom properties that [!DNL Marketo Measure] has imported from the source system , in JSON format.</td>
      <td>{"Opportunity_Location__c":"Seattle", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td><b>&#8727;</b> OPPORTUNITY_TYPE</td>
      <td>varchar</td>
      <td>Type of Opportunity, such as New Business, Renewal, etc.</td>
      <td>Renewal, Prospect</td>
    </tr>
  </tbody>
</table>
<p>
<b>&#8727;</b> <i>Only available in Marketo Measure Ultimate</i>
<p>

### BIZ_OPP_STAGE_TRANSITIONS {#biz-opp-stage-transitions}

Stage transitions for Opportunities.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the transition.</p>
      </td>
      <td>
        <p>ST_0060Z00000nEgjlQAC_0030Z00003IjojKQAR_Demo Scheduled-1_BAT2_0060Z00000nEgjlQAC_0030Z00003IjojKQAR_2018-06-01:19-51-38-1685390.beec556e7757</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Account associated with the Opportunity.</p>
      </td>
      <td>
        <p>0013100001b44nTAAQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPPORTUNITY_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Opportunity associatedto the transition.</p>
      </td>
      <td>
        <p>0060Z00000nEgjlQAC</p>
      </td>
    </tr>
    <tr>
      <td>CONTACT_ID</td>
      <td>varchar</td>
      <td>
        <p>Id for the Contact associated to the transition.</p>
      </td>
      <td>
        <p>0030Z00003IjojKQAR</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The provided email address for the related Contact.</p>
      </td>
      <td>
        <p>persone@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TOUCHPOINT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Buyer Attribution Touchpoint tied to the transition.</p>
      </td>
      <td>
        <p>BAT2_0060Z00000nEgjlQAC_0030Z00003IjojKQAR_2018-06-01:19-51-38-1685390.beec556e7757</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRANSITION_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record transitioned into the stage.</p>
      </td>
      <td>
        <p>2018-05-26 07:29:43.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the stage for the transition.</p>
      </td>
      <td>
        <p>Demo Scheduled</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id value of the stage for the transition.</p>
      </td>
      <td>
        <p>_bizible_FT</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>RANK</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>The numerical rank of the stage, as ordered in the [!DNL Marketo Measure] Stage Mapping settings.</p>
      </td>
      <td>
        <p>4</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>INDEX</p>
      </td>
      <td>
        <p>varchar(1)</p>
      </td>
      <td>
        <p>Used in internal processing for indexing and ordering boomerang stages.</p>
      </td>
      <td>1</td>
    </tr>
    <tr>
      <td>
        <p>LAST_INDEX</p>
      </td>
      <td>
        <p>varchar(1)</p>
      </td>
      <td>
        <p>Used in internal processing for indexing and ordering boomerang stages.</p>
      </td>
      <td>1</td>
    </tr>
    <tr>
      <td>
        <p>IS_PENDING</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the touchpoint is considered pending and not yet closed. This only appears for customers with full path attribution model.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_NON_TRANSITIONAL</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the the row is tied to a milestone stage transition. For example, if there are 3 stages/entries (FT, LC, MQL) and 4 touchpoints, the 1 touchpoint without a stage on it is considered "non-transitional" so the value would equal true.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PREVIOUS_STAGE_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Transition date for the previous stage, according to the stage rank.</p>
      </td>
      <td>
        <p>2015-07-16 17:41:49.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEXT_STAGE_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Transition date for the next stage, according to the stage rank.</p>
      </td>
      <td>
        <p>2018-08-27 19:40:52.000</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Last modified date of the record.</p>
      </td>
      <td>
        <p>2018-08-28 03:53:33.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the transition record is considered deleted.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_PAGE_VIEWS {#biz-page-views}

Page Views collected from web visits. Multiple page views can compose a single Session.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the Page View.</p>
      </td>
      <td>
        <p>2018-08-19:16-49-58-24340.277d79d0167849</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The recorded cookie id at the time the Page View was logged.</p>
      </td>
      <td>
        <p>277d79d01678498fea067c9b631bf6df</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first cookie of the related visitor id.</p>
      </td>
      <td>
        <p>v_277d79d01678498fea067c9b631bf6df</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The Session id correlated with the Page View.</p>
      </td>
      <td>
        <p>2018-08-19:16-49-58-24340.277d79d0167849</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the Page View occurred.</p>
      </td>
      <td>
        <p>2018-08-19 16:49:58.000</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was last modified.</p>
      </td>
      <td>
        <p>2018-08-19 16:55:37.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>URL of the Page View, without query parameters.</p>
      </td>
      <td>
        <p>https://info.adobe.com/demo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>URL of the Page View, including any query parameters.</p>
      </td>
      <td>
        <p>https://info.adobe.com/demo?hsCtaTracking=207219e9-87b6-4105-8f4b-0a3b62ae1af8%7C48060522-3aeb-4c72-8ce5-fd4b1017f069</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IP_ADDRESS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The recorded IP address at the time the Form was submitted.</p>
      </td>
      <td>
        <p>174.127.184.158</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TYPE</p>
      </td>
      <td>varchar</td>
      <td>Indicates the type of Event.</td>
      <td>
        <p>PageView</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>USER_AGENT_STRING</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Device and browser recorded at the time of the Form Submit.</p>
      </td>
      <td>
        <p>Mozilla/5.0 (X11; Linux x86_64; rv:52.0) Gecko/20100101 Firefox/52.0</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_SEQUENCE</p>
      </td>
      <td>
        <p>varchar(1)</p>
      </td>
      <td>
        <p>Indicates the order in which the Page View occurred in the Session.</p>
      </td>
      <td>
        <p>1</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_RANDOM</p>
      </td>
      <td>varchar</td>
      <td>Used for internal auditing and processing.</td>
      <td>
        <p>103532</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DUPLICATED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Indicates if the record is considered a duplicate.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>IS_PROCESSED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Used for internal processing.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>URL where the Page View originated from, without query parameters.</p>
      </td>
      <td>
        <p>http://info.adobe.com/cmos-guide-to-b2b-marketing-attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>URL where the Page View originated from, including any query parameters.</p>
      </td>
      <td>
        <p>http://info.adobe.com/cmos-guide-to-b2b-marketing-attribution?utm_source=linkedin&amp;utm_medium=Social&amp;utm_campaign=SU%20-%20CMO%20JT&amp;utm_content=CMOs%20Guide&amp;utm_term=lisu05091601</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAGE_TITLE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Title of the Page.</p>
      </td>
      <td>
        <p>The CMO's Guide to B2B Marketing Attribution Download</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Email address provided on a Form, as captured from the javascript.</p>
      </td>
      <td>personc@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Foreign Key to the Biz_Facts view.</p>
      </td>
      <td>
        <p>-6255315750913680000</p>
      </td>
    </tr>
    <tr>
      <td>CURRENT_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Foreign Key to the Url table.</td>
      <td>6255315750913680000</td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td>Foreign Key to the Url table.</td>
      <td>6255315750913680000</td>
    </tr>
    <tr>
      <td>HAS_USER_CONSENT</td>
      <td>boolean</td>
      <td>Indicates if the user has consented to tracking. False means the Page View has been collected because user consent is not required. True means the Page View has been collected and the user has given consent to be tracked.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_PLACEMENTS {#biz-placements}

Table that stores all placements downloaded from any connected ads accounts, an object from the Doubleclick integration.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the Placement.</p>
      </td>
      <td>
        <p>ba.3284209.132855866.4556709270.10426699711</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>varchar</td>
      <td>The Placement Id from the source system.</td>
      <td>10426699711</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Ad Account from which the Placement was imported.</p>
      </td>
      <td>fb. 106851586409075</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name for the Ad Account from which the Placement was imported.</p>
      </td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Advertiser for the Placement, specifically for Doubleclick.</p>
      </td>
      <td>300184624</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Advertiser for the Placement, specifically for Doubleclick.</p>
      </td>
      <td>[!DNL Marketo Measure] Analytics</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Ad Group above the Placement in any ads hierarchy.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Ad Group above the Placement in any ads hierarchy.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Campaign for the Placement.</p>
      </td>
      <td>ba.3284209.132855866</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Campaign for the Placement.</p>
      </td>
      <td>Pipeline Marketing</td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Placement is still active in the source system.</p>
      </td>
      <td>true</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Placement has been deleted in the source system.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was last modified.</p>
      </td>
      <td>2018-08-02 06:36:25.000</td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was first imported from the source system.</p>
      </td>
      <td>2018-08-02 06:36:25.000</td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Placement, from the source system.</p>
      </td>
      <td>Market</td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Placement needs to be updated for [!DNL Marketo Measure] tagging.</p>
        <p>(Diagnostic field, used by internal processing.)</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>varchar</td>
      <td>Diagnostic field, for internal processing.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The main object or entity for this table. In this case, "Placement".</p>
      </td>
      <td>Placement</td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Provider for the Placement.</p>
      </td>
      <td>BingAds</td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Foreign Key to the Biz_Facts view.</p>
      </td>
      <td>6008900572523230000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Snowflake's created date of the record</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Snowflake's modified date of the record</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Snowflake's deleted date of the record if it has been deleted</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_SEGMENTS {#biz-segments}

Segment values as defined in the [!DNL Marketo Measure] application.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the Segment.</p>
      </td>
      <td>
        <p>New Business</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Segment.</p>
      </td>
      <td>
        <p>New Business</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Foreign Key to the Biz_Facts view.</p>
      </td>
      <td>
        <p>1028715376434030000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_SEGMENT_NAMES {#biz-segment-names}

Maps the name of the custom segment to it's category value. (This maps the column names to the Category1 - 15 column headers found in the touchpoint tables.)

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
      <td>
        <p>CATEGORY</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Indicates the category the segment name is mapped to.</p>
      </td>
      <td>
        <p>CategoryOne</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was last modified.</p>
      </td>
      <td>
        <p>2022-02-28 18:12:35.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEGMENT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the segment mapped to the category.</p>
      </td>
      <td>
        <p>1028715376434030000</p>
      </td>
    </tr>
    <tr>
      <td>IS_ACTIVE</td>
      <td>boolean</td>
      <td>Indicates if the category is in use.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>boolean</td>
      <td>Indicates if the record is deleted.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_SESSIONS {#biz-sessions}

Sessions as processed from Page Views. Multiple Page Views can make up one Session, and a single visitor id can be associated to multiple Sessions.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the Session.</p>
      </td>
      <td>
        <p>2016-08-01:14-24-21-9079480.33163948f0a3</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first cookie of the related visitor id.</p>
      </td>
      <td>v_277d79d01678498fea067c9b631bf6df</td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The recorded cookie id of the Session.</p>
      </td>
      <td>277d79d01678498fea067c9b631bf6df</td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date of the Session.</p>
      </td>
      <td>
        <p>2016-08-01 14:24:21.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was last modified.</p>
      </td>
      <td>
        <p>2018-09-01 03:49:10.000</p>
      </td>
    </tr>
    <tr>
      <td>IS_FIRST_SESSION</td>
      <td>boolean</td>
      <td>Indicates if this is the first Session for the visitor id.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>
        <p>CHANNEL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Channel attirbuted to the Session, as defined by the Channel definitions set in the [!DNL Marketo Measure] application.</p>
      </td>
      <td>
        <p>Paid Search.AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAGE_TITLE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the web page.</p>
      </td>
      <td>
        <p>Salesforce Google Analytics | [!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>URL of the first Page View of the Session, without query parameters.</p>
      </td>
      <td>
        <p>http://www.adobe.com/salesforce-google-analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>URL of the first Page View of the Session, including any query parameters.</p>
      </td>
      <td>
        <p>http://www.adobe.com/salesforce-google-analytics?_bt=83558988035&amp;_bk=google%20analytics%20salesforce&amp;_bm= p&amp;gclid=CMvd5YTLo84CFUI9gQodd-kLEQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>URL where the Session originated from, without query parameters.</p>
      </td>
      <td>
        <p>https://www.google.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>URL where the Session originated from, including any query parameters.</p>
      </td>
      <td>
        <p>https://www.google.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the referrer page.</p>
      </td>
      <td>
        <p>Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEARCH_PHRASE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The value that the user entered in the browser to search for and ended up on the website.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] google salesforce</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEB_SOURCE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Used to define the source that resulted in the Session. This can be parsed out from the URL from utm_source or set to an Ad Provider if [!DNL Marketo Measure] is able to resolve an ad.</p>
      </td>
      <td>
        <p>Google AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_FORM</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Session contained a Form fill,</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_CHAT</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Session contained a web chat.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_EMAIL</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Session had an email address.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_CRM_ACTIVITY</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Sesssion came from a CRM activity record.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DEVICE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The browser and operating system of the user during the Session.</p>
      </td>
      <td>
        <p>Chrome (65.0), Windows (6.1)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The Ad platform [!DNL Marketo Measure] resolvde from, typically one of our integration partners.</p>
      </td>
      <td>
        <p>Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Ad Account which the ad was resolved from.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Account which the ad was resolved from.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Advertiser the Ad was resolved from, specifically from Doubleclick connection.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Advertiser the Ad was resolved from, specifically from Doubleclick connection.</p>
      </td>
      <td>
        <p>Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Site the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Site the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Palcement the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Placement the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>roadblock</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Campaign the Ad was resolved from.</p>
      </td>
      <td>
        <p>aw.6601259029.321586235</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Campaign the Ad was resolved from.</p>
      </td>
      <td>
        <p>Planning Your Budget Webinar</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Ad Group the Ad was resolved from. This only applies to Google Adwords.</p>
      </td>
      <td>
        <p>aw.6601259029.321586235.23182235435</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Group the Ad was resolved from. This only applies to Google Adwords.</p>
      </td>
      <td>
        <p>Salesforce - Google Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Ad resolved from. This applies to Doubleclick Campaign Manager and Facebook (display).</p>
      </td>
      <td>aw.6601259029.321586235.23182235435</td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad resolved from. This applies to Doubleclick Campaign Manager and Facebook (display).</p>
      </td>
      <td>Winter Promo - Green</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Creative the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>aw.6601259029.321586235.23182235435.83558988035</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Creative the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>Integrate GA & Salesforce</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first line of the Creative from the search Ad, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>Integrate Salesforce & Analytics To</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The second line of the Creative from the search Ad, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>Optimize for Revenue. Learn How.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The landing page that clicks through from the search Ad, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>http://www.adobe.com/salesforce-google-analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The friendly URL name that's shown on the search Ad, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>adobe.com/Salesforce-for-GA</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Keyword the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>aw.6601259029.321586235.23182235435.35934468937</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Keyword the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>google analytics salesforce</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The type of match found between the search phrase and the purchased keyword.</p>
      </td>
      <td>
        <p>Phrase</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Parsed from the URL from utm_campaign.</p>
      </td>
      <td>
        <p>SU - ABC Accounts - Paid Media Skills</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SOURCE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Parsed from the URL from utm_source.</p>
      </td>
      <td>
        <p>linkedin</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDIUM</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Parsed from the URL from utm_medium.</p>
      </td>
      <td>
        <p>Social</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TERM</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Parsed from the URL from utm_term.</p>
      </td>
      <td>
        <p>lisu07261601</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTENT</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Parsed from the URL from utm_content.</p>
      </td>
      <td>
        <p>2016 AdWords Benchmark Report</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CITY</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The resolved city from the IP address.</p>
      </td>
      <td>Vancouver</td>
    </tr>
    <tr>
      <td>
        <p>REGION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The resolved region from the IP address.</p>
      </td>
      <td>British Columbia</td>
    </tr>
    <tr>
      <td>
        <p>COUNTRY</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The resolved country from the IP address.</p>
      </td>
      <td>Canada</td>
    </tr>
    <tr>
      <td>
        <p>ISP_NAME</p>
      </td>
      <td>varchar</td>
      <td>Expected to be null since the field is obsolete.</td>
      <td>
        <p>NULL</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IP_ADDRESS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The recorded IP address at the time the Session.</p>
      </td>
      <td>
        <p>174.127.184.158</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Determines if this Session was merged with another and should be deleted.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Foreign Key to the Biz_Facts view.</p>
      </td>
      <td>
        <p>-2712935512233520000</p>
      </td>
    </tr>
    <tr>
      <td>LANDING_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERTISER_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_SITES {#biz-sites}

Sites imported from any connected Ad Account.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the Site.</p>
      </td>
      <td>aw.3284209</td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>varchar</td>
      <td>The Site Id from the source system.</td>
      <td>39464932147</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Ad Account from which the Site was imported.</p>
      </td>
      <td>aw.3284209</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Account from which the Site was imported.</p>
      </td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The Id of the advertiser for the site, specifically for Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The name of the advertiser for the site, specifically for Doubleclick.</p>
      </td>
      <td>
        <p>Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Ad Group above Site in any ads hierarchy.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Expected to be null since there is no Ad Group above Site in any ads hierarchy.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Campaign for the Site.</p>
      </td>
      <td>
        <p>ba.3284209.132630532</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Campaign for the Site.</p>
      </td>
      <td>Revue Attribution</td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Site is still active in the source system.</p>
      </td>
      <td>true</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Site has been deleted in the source system.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was last modified.</p>
      </td>
      <td>2018-08-02 06:37:29.000</td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was first imported from the source system.</p>
      </td>
      <td>2018-08-02 06:37:29.000</td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Site, from the source system.</p>
      </td>
      <td>Revenue</td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Site needs to be updated for [!DNL Marketo Measure] tagging.</p>
        <p>(Diagnostic field, used for internal processing.)</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>varchar</td>
      <td>Diagnostic field, used for internal processing.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The main object or entity for this table. In this case, "Site".</p>
      </td>
      <td>Site</td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Provider for the Site.</p>
      </td>
      <td>AdWords</td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Foreign Key to the Biz_Facts view.</p>
      </td>
      <td>
        <p>-2712935512233520000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_SITE_LINKS {#biz-site-links}

Sites Links from any connected Ads Account.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the site link</p>
      </td>
      <td>
        <p>aw.6601259029.285077795.1654234342</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td>
        <p>1654234342</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The ID of the connected ads account for the site link</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The name of the connected ads account for the site link</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The Id of the advertiser for the site link, specifically for Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The name of the advertiser for the site link, specifically for Doubleclick.</p>
      </td>
      <td>
        <p>Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The ID of the ad group for the site link</p>
      </td>
      <td>aw.6601259029.208548635.16750166675</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The name of the ad group for the site link</p>
      </td>
      <td>Brand - Core</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The ID of the campaign for the site link</p>
      </td>
      <td>
        <p>aw.6601259029.285077795</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The name of the campaign for the site link</p>
      </td>
      <td>
        <p>Brand</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the site link is still active in the ads account</p>
      </td>
      <td>
        <p>TRUE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the site link has been deleted in the ads account</p>
      </td>
      <td>
        <p>FALSE</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>The last modified date of the row</p>
      </td>
      <td>
        <p>2018-08-02 06:36:50.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>The date that the site link was first downloaded by [!DNL Marketo Measure]</p>
      </td>
      <td>
        <p>2018-08-02 06:36:50.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The name of the site link</p>
      </td>
      <td>Link A</td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the site link needs to get updated to get Marekto Measure tagging</p>
      </td>
      <td>
        <p>FALSE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>varchar</td>
      <td></td>
      <td>
        <p>aw.6601259029.285077795</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The main object or entity for this table. In this case, "SiteLink"</p>
      </td>
      <td>
        <p>SiteLink</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The name of the ads provider for the site link</p>
      </td>
      <td>
        <p>AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The URL for the landing page.</p>
        <p>(Diagnostic field, for internal processing.)</p>
      </td>
      <td>
        <p>http://adobe.com/b2b-marketing-attribution?_bt =</p>
        <p>{creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Previous value for URL_CURRENT.</p>
        <p>(Diagnostic field, for internal processing.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_REQUESTED</p>
      </td>
      <td>varchar</td>
      <td>
        <p>What the URL will be decorated with [!DNL Marketo Measure] parameters.</p>
        <p>(Diagnostic field, for internal processing.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Snowflake's created date of the record</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Snowflake's modified date of the record</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Snowflake's deleted date of the record if it has been deleted</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_STAGE_DEFINITIONS {#biz-stage-definitions}

List of stages as imported or defined in the [!DNL Marketo Measure] application.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the Stage.</p>
      </td>
      <td>
        <p>01J3100000QE753EAD</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was last modified.</p>
      </td>
      <td>
        <p>2018-08-22 17:27:27.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Stage.</p>
      </td>
      <td>
        <p>Verbal</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_INACTIVE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Indicates if the Stage is considered inactive.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_IN_CUSTOM_MODEL</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the Stage is selected to track in the custom model.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_BOOMERANG</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the Stage is selected to track as a boomerang stage.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_TRANSITION_TRACKING</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Indicates if the Stage is selected to track for transitions.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE_STATUS</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Status of the Stage, as defined in the [!DNL Marketo Measure] application Stage Mapping.</p>
      </td>
      <td>
        <p>Open</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_FROM_SALESFORCE</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Indicates if the Stage is imported from an external source system.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DEFAULT</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>Indicates if the Stage is set as a default.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>RANK</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>The numerical rank of the Stage, used to sort Stages in transitional order.</p>
      </td>
      <td>
        <p>53</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the Stage has been deleted.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_TOUCHPOINTS {#biz-touchpoints}

Buyer Touchpoints, all touchpoints associated with a Lead or Contact. This table will be empty if Lead Touchpoints or Contact Touchpoints are disabled.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the Buyer Touchpoint (BT).</p>
      </td>
      <td>
        <p>TP2_Person_00Q0Z000013e2PYUAY_2018-08-27:20-04-40-5655690.1ee8567c175a</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was last modified.</p>
      </td>
      <td>
        <p>2018-08-29 22:29:30.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>varchar</td>
      <td>Email address associated with the BT.</td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>CONTACT_ID</td>
      <td>varchar</td>
      <td>
        <p>Id for the Contact associated with the BT.</p>
      </td>
      <td>0030Z00003K5bpKQAR</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Account associated with the BT.</p>
      </td>
      <td>
        <p>0013100001lSLScAAO</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Lead associated with the BT.</p>
      </td>
      <td>
        <p>00Q0Z000013e2PYUAY</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>UNIQUE_ID_PERSON</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The parent person record that relates to a Lead or Contact.</p>
      </td>
      <td>
        <p>Person_00Q0Z000013e2PYUAY</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>USER_TOUCHPOINT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the User Touchpoint which generated the BT.</p>
      </td>
      <td>
        <p>person@adobe.com_2018-08-29:18-14-53-8102030.10df92cbb414</p>
      </td>
    </tr>
    <tr>
      <td>VISITOR_ID</td>
      <td>varchar</td>
      <td>Id for the visitor associated with the BT.</td>
      <td>v_277d79d01678498fea067c9b631bf6df</td>
    </tr>
    <tr>
      <td>
        <p>TOUCHPOINT_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date of the touchpoint.</p>
      </td>
      <td>
        <p>2018-08-27 20:04:40.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MARKETING_TOUCH_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The type of activity, Web Visit, Web Form, Web Chat, Phone Call, [CRM] Campaign, or [CRM] Activity. Referred to in the CRM as "Touchpoint Type."</p>
      </td>
      <td>
        <p>Web Form</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CHANNEL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The channel the touchpoint falls into, as defined in the custom channel definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Marketing Channel - Path."</p>
      </td>
      <td>Social.LinkedIn</td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY1</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The segment value for the 1st Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments".</p>
      </td>
      <td>ABC</td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY2</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The segment value for the 2nd Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments".</p>
      </td>
      <td>
        <p>Yes</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY3</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The segment value for the 3rd Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments".</p>
      </td>
      <td>
        <p>Other</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY4</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The segment value for the 4th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments".</p>
      </td>
      <td>
        <p>Partner</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY5</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The segment value for the 5th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments".</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY6</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The segment value for the 6th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments".</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY7</p>
      </td>
      <td>varchar</td>
      <td>The segment value for the 7th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY8</p>
      </td>
      <td>varchar</td>
      <td>The segment value for the 8th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY9</p>
      </td>
      <td>varchar</td>
      <td>The segment value for the 9th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY10</p>
      </td>
      <td>varchar</td>
      <td>The segment value for the 10th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY11</p>
      </td>
      <td>varchar</td>
      <td>The segment value for the 11th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY12</p>
      </td>
      <td>varchar</td>
      <td>The segment value for the 12th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY13</p>
      </td>
      <td>varchar</td>
      <td>The segment value for the 13th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY14</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The segment value for the 14th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments".</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CATEGORY15</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The segment value for the 15th Category the touchpoint falls into, as defined in the segment definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Segments".</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected browser that the user was on during the session.</p>
      </td>
      <td>Chrome</td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_VERSION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected version of the browser that the user was on during the session.</p>
      </td>
      <td>
        <p>68</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected platform that the user was on during the session.</p>
      </td>
      <td>
        <p>Windows</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_VERSION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected version of the platform that the user was on during the session.</p>
      </td>
      <td>10_12</td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first landing page of the session which resulted in a touchpoint. Referred to in the CRM as "Landing Page".</p>
      </td>
      <td>
        <p>https://info.adobe.com/definitive-guide-to-pipeline-marketing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first landing page of the session that resulted in a touchpoint. A raw landing page will contain all query parameters in the URL. Referred to in the CRM as "Landing Page - Raw".</p>
      </td>
      <td>
        <p>https://info.adpbe.com/definitive-guide-to-pipeline-marketing?utm_source=linkedin&amp;utm_medium=Social&amp;utm_campaign=SU_COM_Demand_ Skills&amp;utm_content=DGPM&amp;utm_term=lisu03151846&amp;_bl=66452504</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Typically the external landing page immediately before the user comes onto the website. Referred to in the CRM as "Referrer Page".</p>
      </td>
      <td>https://www.linkedin.com/</td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Typically the external landing page immediately before the user comes onto the website. A raw referrer page may contain query parameters in the URL. Referred to in the CRM as "Referrer Page - Raw".</p>
      </td>
      <td>
        <p>https://www.linkedin.com/feed</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first form recorded in a session which resulted in a touchpoint. Subsequent form submissions will not show up in the Touchpoints table, but rather in the Form_Submits table. Referred to in the CRM as "Form URL".</p>
      </td>
      <td>
        <p>https://info.adobe.com/demo</p>
      </td>
    </tr>
    <tr>
      <td>FORM_PAGE_RAW</td>
      <td>varchar</td>
      <td>The first form recorded in a session which resulted in a touchpoint. Subsequent form submissions will not show up in the Touchpoints table, but rather in the Form_Submits table. A raw form page may contain query parameters in the URL. Referred to in the CRM as "Form URL - Raw".</td>
      <td>https://info.adobe.com/demo?hsCtaTracking=98adcc2f-afe2-40c4-9d79-40dcc41663ee%7C3cfaa909-39cb-4f5d-93eb-be05de6b0180</td>
    </tr>
    <tr>
      <td>
        <p>FORM_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the form submission occurred.</p>
      </td>
      <td>
        <p>2017-06-20 01:06:41.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CITY</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected city the user was in during the session.</p>
      </td>
      <td>
        <p>New York</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REGION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected region the user was in during the session.</p>
      </td>
      <td>
        <p>New York</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COUNTRY</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected country the user was in during the session.</p>
      </td>
      <td>
        <p>United States</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDIUM</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Used to define the medium which resulted in the touchpoint. This can either be parsed out from the URL from utm_medium. Or, if [!DNL Marketo Measure] is able to resolve an ad, it may be values such as "cpc" or "display."</p>
      </td>
      <td>
        <p>Social</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEB_SOURCE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Used to define the source which resulted in the touchpoint. This can be parsed out from the URL from utm_source, generically set as "CRM Campaign" if it was synced from the CRM, or if [!DNL Marketo Measure] is able to resolve an ad, it may be values such as "Google AdWords" or "Facebook." Referred to in the CRM as "Touchpoint Source".</p>
      </td>
      <td>
        <p>LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEARCH_PHRASE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The value which the user entered in the browser to search for and ended up on the website. Depending on the keyword buys, this may or may not match the keywords purchased from the Paid Search platform.</p>
      </td>
      <td>
        <p>markeot measure attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Ad platform [!DNL Marketo Measure] was able to resolve from, typically one of our integration partners.</p>
      </td>
      <td>
        <p>LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Ad Account in which the ad was resolved from.</p>
      </td>
      <td>
        <p>li.502664737</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Account in which the ad was resolved from.</p>
      </td>
      <td>
        <p>MM SC 2016_14605342_3/7-3/31/16</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Advertiser from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Advertiser from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Marketo Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Site from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Site from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Placement from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Placement from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>roadblock</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Campaign from the Ad Account in which the Ad was resolved from.</p>
      </td>
      <td>
        <p>li.502664737.138949954</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Campaign from the Ad Account in which the Ad was resolved from.</p>
      </td>
      <td>
        <p>SU - COM Accounts - Demand Skills</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Ad Group from the Ad Account in which the Ad was resolved from. This only applies to Google Adwords.</p>
      </td>
      <td>aw.6601259029.317738075.23105327435</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Group from the Ad Account in which the Ad was resolved from. This only applies to Google AdWords.</p>
      </td>
      <td>Marketing Attribution - General</td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Ad from the Ad Account in which the Ad was resolved from. This applies to Doubleclick Campaign Manager and Facebook (display).</p>
      </td>
      <td>dc.6114.8882972.25272734.492579576</td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad from the Ad Account in which the Ad was resolved from. This applies to Doubleclick Campaign Manager and Facebook (display).</p>
      </td>
      <td>Budget Webinar - sidebar</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Creative from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>li.502664737.138949954.66452504</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Creative from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>lisu03151846</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first line of the Creative from the search Ad, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>Lead gen is done</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The second line of the Creative from the search Ad, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>Download the definitive guide to pipeline marketing: https://lnkd.in/e9xYj5M</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The landing page that clicks through from the search Ad, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>https://image-store.slidesharecdn.com/d29165c0-1e0b-4ffc-a494-d2c77e7cd4a6-large.jpeg</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The friendly URL name that's shown on the search Ad, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>marektomeasure.com/guide</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Keyword purchased from the Paid Search buy, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>__GAId__lisu03151846</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Keyword purchased from the Paid Search buy, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search)</p>
      </td>
      <td>
        <p>lisu03151846</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The type of match found between the search phrase and the purchased keyword.</p>
      </td>
      <td>
        <p>Broad</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_FIRST_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not this touchpoint is treated as the first touch of the opportunity journey.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_LEAD_CREATION_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not this touchpoint is treated as the lead creation touch of the opportunity journey.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_OPP_CREATION_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not this touchpoint is treated as the opportunity creation touch of the opportunity journey.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_CLOSED_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not this touchpoint is treated as the closed touch of the opportunity journey.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>STAGES_TOUCHED</td>
      <td>varchar</td>
      <td>This field has been deprecated. Use the Stage_Transitions tables for stage information.</td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>IS_FORM_SUBMISSION_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not this touchpoint had a form fill during the session.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_IMPRESSION_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not this touchpoint is treated as the first impression touch of the opportunity journey</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>The calculated percentage allocated to this touchpoint because it's a first touch (See Is_First_Touch).</p>
      </td>
      <td>
        <p>100</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_ANON_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>The calculated percentage allocated to this touchpoint because it's a lead creation touch (See Is_Lead_Creation_Touch).</p>
      </td>
      <td>
        <p>100</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>U_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>The calculated percentage allocated to this touchpoint because it's part of a u-shaped touch (See Is_First_Touch and Is_Lead_Creation_Touch).</p>
      </td>
      <td>
        <p>100</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>W_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>The calculated percentage allocated to this touchpoint because it's part of a w-shaped touch (See Is_First_Touch, Is_Lead_Creation_Touch, and Is_Opp_Creation_Touch). Expected to be 0 since this is a BT.</p>
      </td>
      <td>
        <p>0</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FULL_PATH_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>The calculated percentage allocated to this touchpoint because it's part of a full path model (See Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch, Is_Closed_Touch). Expected to be 0 since this is a BT.</p>
      </td>
      <td>
        <p>0</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_MODEL_PERCENTAGE</td>
      <td>number(22,19)</td>
      <td>The calculated percentage allocated to this touchpoint because it's part of a custom model (See Is_First_Touch,  Is_Lead_Creation_Touch, Is_Opp_Creation_Touch, Is_Closed_Touch). Expected to be 0 since this is a BT.</p>
      </td>
      <td>0</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether this touchpoint is deleted.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td>
        <p>Foreign Key to the Biz_Facts view.</p>
      </td>
      <td>
        <p>-9004910726709710000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ROW_KEY</p>
      </td>
      <td>
        <p>number(38,0)</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>LANDING_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>FORM_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERISER_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_URLS {#biz-urls}

Aggregation of URLs from landing pages, referrer pages, and page views.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>The full URL,.</td>
      <td>https://www.adobe.com/blog/strategic-marketing-plangoals</td>
    </tr>
    <tr>
      <td>SCHEME</td>
      <td>varchar</td>
      <td>The secure communication of the web page over the network.</td>
      <td>https</td>
    </tr>
    <tr>
      <td>HOST</td>
      <td>varchar</td>
      <td>The domain of the URL, with any subdomains.</td>
      <td>www.adobe.com</td>
    </tr>
    <tr>
      <td>PAGE_TITLE</td>
      <td>varchar</td>
      <td>Title of the page.</td>
      <td>The CMO's Guide to B2B Marketing Attribution Download</td>
    </tr>
    <tr>
      <td>PATH</td>
      <td>varchar</td>
      <td>The part of the URL that points to a specific location on the host.</td>
      <td>/blog/strategic-marketing-plangoals</td>
    </tr>
    <tr>
      <td>PORT</td>
      <td>varchar</td>
      <td>The port from an internet host, optional in a URL.</td>
      <td>584</td>
    </tr>
    <tr>
      <td>ROW_KEY</td>
      <td>number(38,0)</td>
      <td>Foreign Key to the Biz_Facts view.</td>
      <td>5686109553536636820</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_USER_TOUCHPOINTS {#biz-user-touchpoints}

All Touchpoints created from any event tied to an email.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>
        <p>A unique Id for the User Touchpoint.</p>
      </td>
      <td>
        <p>person@adobe.com_2018-01-05:16-47-02-8803320.ddf67c101f58</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was last modified.</p>
      </td>
      <td>
        <p>2018-09-05 23:30:53.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EMAIL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Email address associated with the User Touchpoint.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Session which created the User Touchpoint.</p>
      </td>
      <td>
        <p>2018-01-05:16-47-02-8803320.ddf67c101f58</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_MEMBER_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Campaign Member which created the User Touchpoint.</p>
      </td>
      <td>
        <p>00v0Z00001VTgv1QAD</p>
      </td>
    </tr>
    <tr>
      <td>CRM_ACTIVITY_ID</td>
      <td>varchar</td>
      <td>Id for the Activity which created the User Touchpoint.</td>
      <td>1678625515</td>
    </tr>
    <tr>
      <td>
        <p>CRM_EVENT_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Event which created the User Touchpoint.</p>
      </td>
      <td>
        <p>00U0Z00000pCZmyUAG</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CRM_TASK_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>TId for the Task which created the User Touchpoint.</p>
      </td>
      <td>
        <p>00T0Z00004Qbd1jUAB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IMPRESSION_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id for the Impression which created the User Touchpoint.</p>
      </td>
      <td>00T0Z00004Qbd1jUAB</td>
    </tr>
    <tr>
      <td>IS_FIRST_KNOWN_TOUCH</td>
      <td>boolean</td>
      <td>Whether or not this touchpoint is treated as the first touch of the opportunity journey.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>VISITOR_ID</td>
      <td>varchar</td>
      <td>The first cookie id of the related visitor id.</td>
      <td>v_36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>TOUCHPOINT_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the User Touchpoint occured.</p>
      </td>
      <td>
        <p>2018-01-05 16:47:02.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MARKETING_TOUCH_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The type of activity, Web Visit, Web Form, Web Chat, Phone Call, [CRM] Campaign, or [CRM] Activity. Referred to in the CRM as "Touchpoint Type."</p>
      </td>
      <td>
        <p>Web Form</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CHANNEL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The channel the touchpoint falls into, as defined in the custom channel definitions within the [!DNL Marketo Measure] App. Referred to in the CRM as "Marketing Channel - Path."</p>
      </td>
      <td>
        <p>Social.LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected browser that the user was on during the session.</p>
      </td>
      <td>
        <p>Firefox</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BROWSER_VERSION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected version of the browser that the user was on during the session.</p>
      </td>
      <td>
        <p>33</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected platform that the user was on during the session.</p>
      </td>
      <td>
        <p>Mac</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_VERSION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected version of the platform that the user was on during the session.</p>
      </td>
      <td>
        <p>10_12</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first landing page of the session which resulted in a touchpoint. Referred to in the CRM as "Landing Page".</p>
      </td>
      <td>
        <p>https://www.adobe.com/blog/budget-and-planning-maturity-model-b2b-marketing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first landing page of the session that resulted in a touchpoint. A raw landing page will contain all query parameters in the URL. Referred to in the CRM as "Landing Page - Raw".</p>
      </td>
      <td>
        <p>https://www.adobe.com/blog/budget-and-planning-maturity-model-b2b-marketing?utm_source=feedburner&amp;utm_medium=feed&amp;utm_campaign=Feed%3A+ marketo+%maeasure%27s+Pipeline+Marketing+Blog%29</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Typically the external landing page immediately before the user comes onto the website. Referred to in the CRM as "Referrer Page".</p>
      </td>
      <td>
        <p>https://www.google.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Typically the external landing page immediately before the user comes onto the website. A raw referrer page may contain query parameters in the URL. Referred to in the CRM as "Referrer Page - Raw".</p>
      </td>
      <td>
        <p>https://www.google.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first form recorded in a session which resulted in a touchpoint. Subsequent form submissions will not show up in the Attribution_Touchpoints table, but rather in the Form_Submits table. Referred to in the CRM as "Form URL".</p>
      </td>
      <td>
        <p>http://info.adobe.com/adwords-for-lead-generation</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE_RAW</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first form recorded in a session which resulted in a touchpoint. Subsequent form submissions will not show up in the Attribution_Touchpoints table, but rather in the Form_Submits table. A raw form page may contain query parameters in the URL. Referred to in the CRM as "Form URL - Raw".</p>
      </td>
      <td>
        <p>http://info.adobe.com/adwords-for-lead-generation?utm_source=linkedin&amp;utm_medium=paid&amp;utm_content=sfskill&amp;utm _campaign=Content%20-%20AdWords%20Guide</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the form submission occurred.</p>
      </td>
      <td>
        <p>2015-06-03 17:49:10.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CITY</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected city the user was in during the session.</p>
      </td>
      <td>
        <p>Oakland</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REGION</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected region the user was in during the session.</p>
      </td>
      <td>
        <p>California</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COUNTRY</p>
      </td>
      <td>varchar</td>
      <td>
        <p>From the javascript and IP address, the detected country the user was in during the session.</p>
      </td>
      <td>
        <p>United States</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDIUM</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Used to define the medium which resulted in the touchpoint. This can either be parsed out from the URL from utm_medium. Or, if [!DNL Marketo Measure] is able to resolve an ad, it may be values such as "cpc" or "display."</p>
      </td>
      <td>
        <p>paid</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEB_SOURCE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Used to define the source which resulted in the touchpoint. This can be parsed out from the URL from utm_source, generically set as "CRM Campaign" if it was synced from the CRM, or if [!DNL Marketo Measure] is able to resolve an ad, it may be values such as "Google AdWords" or "Facebook." Referred to in the CRM as "Touchpoint Source".</p>
      </td>
      <td>
        <p>linkedin</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEARCH_PHRASE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The value which the user entered in the browser to search for and ended up on the website. Depending on the keyword buys, this may or may not match the keywords purchased from the Paid Search platform.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Ad platform [!DNL Marketo Measure] was able to resolve from, typically one of our integration partners.</p>
      </td>
      <td>
        <p>Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Ad Account in which the ad was resolved from.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Account in which the ad was resolved from.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Account</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Advertiser from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Advertiser from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Site from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Site from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Placement from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Placement from the Ad Account in which the Ad was resolved from. This only applies to Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>roadblock</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Campaign from the Ad Account in which the Ad was resolved from.</p>
      </td>
      <td>
        <p>aw.6601259029.208548635</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Campaign from the Ad Account in which the Ad was resolved from.</p>
      </td>
      <td>
        <p>Brand</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Ad Group from the Ad Account in which the Ad was resolved from. This only applies to Google Adwords.</p>
      </td>
      <td>
        <p>aw.6601259029.208548635.16750166675</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad Group from the Ad Account in which the Ad was resolved from. This only applies to Google AdWords.</p>
      </td>
      <td>
        <p>Brand - Core</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Ad from the Ad Account in which the Ad was resolved from. This applies to Doubleclick Campaign Manager and Facebook (display).</p>
      </td>
      <td>dc.6114.8882972.25272734.492579576</td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Ad from the Ad Account in which the Ad was resolved from. This applies to Doubleclick Campaign Manager and Facebook (display).</p>
      </td>
      <td>Budget Webinar - sidebar</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Creative from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>aw.6601259029.208548635.16750166675.195329631298</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Creative from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Official Site</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The first line of the Creative from the search Ad, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>Revenue Planning & Attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The second line of the Creative from the search Ad, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>Learn why 250+ companies choose [!DNL Marketo Measure] for marketing attribution. Get a demo!</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The landing page that clicks through from the search Ad, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>http://info.adobe.com/demo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The friendly URL name that's shown on the search Ad, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>adobe.com/demo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Id of the Keyword purchased from the Paid Search buy, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search).</p>
      </td>
      <td>
        <p>aw.6601259029.208548635.16750166675.46267805426</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>varchar</td>
      <td>
        <p>Name of the Keyword purchased from the Paid Search buy, pulled from the Ad Account in which the Ad was resolved from. This applies to Google AdWords and Bing Ads (search)</p>
      </td>
      <td>
        <p>[marketo]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>varchar</td>
      <td>
        <p>The type of match found between the search phrase and the purchased keyword.</p>
      </td>
      <td>
        <p>Exact</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_FORM_SUBMISSION_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not this touchpoint had a form fill during the session.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_IMPRESSION_TOUCH</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not this touchpoint is treated as the first impression touch of the opportunity journey.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolean</p>
      </td>
      <td>
        <p>Whether or not the touchpoint is deleted.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>ROW_KEY</td>
      <td>number(38,0)</td>
      <td>Foreign Key to the Biz_Facts view.</td>
      <td>-5269090762570690000</td>
    </tr>
    <tr>
      <td>LANDING_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>FORM_PAGE_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERISER_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>number(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

### BIZ_WEB_HOST_MAPPINGS {#biz-web-host-mappings}

Mapping table to map [!DNL Marketo Measure] Session Id to Adobe ECID and Munckin Id.

<table>
  <tbody>
    <tr>
      <th>Column</th>
      <th>Data Type</th>
      <th>Description</th>
      <th>Sample Data</th>
    </tr>
    <tr>
       <td>ID</td>
      <td>varchar</td>
      <td>A unique Id for the mapping record.</td>
      <td>
        <p>0d643578c0c74753eff91abe668ed328|2020-06-17:19:03:36|0002|0|568668</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>varchar</td>
      <td>The [!DNL Marketo Measure] recorded cookie id.</td>
      <td>0d643578c0c74753eff91abe668ed328</td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>varchar</td>
      <td>The first cookie id of the related visitor id.</td>
      <td>v_0d643578c0c74753eff91abe668ed328</td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>varchar</td>
      <td>The [!DNL Marketo Measure] Session id.</td>
      <td>2018-08-06:01-35-24-1231230.9bc63c34482f</td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>Date the mapping was recorded.</td>
      <td>
        <p>2020-06-17 19:03:36.000</p>
      </td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>
        <p>Date the record was last modified.</p>
      </td>
      <td>
        <p>2020-06-17 19:03:36.000</p>
      </td>
    </tr>
    <tr>
      <td>CURRENT_PAGE</td>
      <td>varchar</td>
      <td>URL of the Page View, without query parameters.</td>
      <td>
        <p>https://learn.atest.com/simplify-retention-starter-kit.html</p>
      </td>
    </tr>
    <tr>
      <td>CURRENT_PAGE_RAW</td>
      <td>varchar</td>
      <td>URL of the Page View, including any query parameters.</td>
      <td>
        <p>https://learn.atest.com/simplify-retention-starter-kit.html?x=nGfrBF&amp;utm_medium=cpc&amp;utm_source=intensify</p>
      </td>
    </tr>
    <tr>
      <td>IP_ADDRESS</td>
      <td>varchar</td>
      <td>The recorded IP address.</td>
      <td>
        <p>159.203.142.127</p>
      </td>
    </tr>
    <tr>
      <td>TYPE</td>
      <td>varchar</td>
      <td>Indicates the type of Event.</td>
      <td>
        <p>HostMapping</p>
      </td>
    </tr>
    <tr>
      <td>USER_AGENT_STRING</td>
      <td>varchar</td>
      <td>Device and browser recorded at the time of the Page View.</td>
      <td>
        <p>Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.130 Safari/537.36</p>
      </td>
    </tr>
    <tr>
      <td>CLIENT_SEQUENCE</td>
      <td>varchar</td>
      <td>Indicates the order in which the Page View occurred in the Session.</td>
      <td>2</td>
    </tr>
    <tr>
      <td>CLIENT_RANDOM</td>
      <td>varchar</td>
      <td>Used for internal auditing and processing.</td>
      <td>566868</td>
    </tr>
    <tr>
      <td>IS_DUPLICATED</td>
      <td>boolean</td>
      <td>Indicates if the record is considered a duplicate.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>IS_PROCESSED</td>
      <td>boolean</td>
      <td>Used for internal processing.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>MAPPING_TYPE</td>
      <td>varchar</td>
      <td>The type of Id which is mapped to the [!DNL Marketo Measure] cookie Id.</td>
      <td>Adobe_OrgId_Ecid</td>
    </tr>
    <tr>
      <td>MAPPING_ORD_ID</td>
      <td>varchar</td>
      <td>Adobe IMS Org Id.</td>
      <td>8CC867C25245ADC30A490D4C</td>
    </tr>
    <tr>
      <td>MAPPING_COOKIE_ID</td>
      <td>varchar</td>
      <td>Adobe ECID for the given Org Id.</td>
      <td>09860926390077352923264316157493772857</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was created in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was last modified in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Date the record was marked as deleted in Snowflake.</td>
      <td>2020-01-01 01:01:00.000</td>
    </tr>
  </tbody>
</table>

## Sample Queries {#sample-queries}

**How many Buyer Touchpoints (BTs) were there for each channel/subchannel last month?**

```
--Note: This query can quickly be modified to show Buyer Attribution Touchpoint (BAT) counts by switching the biz_touchpoints table to the biz_attribution_touchpoints table.
 
select trim(split(ch.name,'.')[0])  as channel
      ,trim(split(ch.name,'.')[1])  as subchannel
      ,count(bt.id)                 as buyer_touchpoint_count
  from biz_user_touchpoints     ut
       left outer join
       biz_touchpoints          bt
        on bt.user_touchpoint_id    = ut.id
       and bt._deleted_date         is null
       left outer join
       biz_channels             ch
        on ut.channel               = ch.id
       and ch._deleted_date         is null
 where ut._deleted_date is null
   and ut.touchpoint_date between add_months(date_trunc(month,current_date),-1) and last_day(dateadd(month,-1,current_date))
group by 1,2
```

**How much Attributed Revenue for each channel was closed in the past month, for the full path attribution model?**

```
--Note: This query does not perform any currency conversion.  If your data contains multiple currencies, you will need to add in logic to perform the conversion to the desired currency using the biz_conversion_rates table.
 
select trim(split(ch.name,'.')[0])  as channel
      ,sum(opp.amount*(bat.full_path_percentage/100))   as attributed_revenue
  from biz_user_touchpoints         ut
       inner join
       biz_attribution_touchpoints  bat
        on bat.user_touchpoint_id   = ut.id
       and bat._deleted_date        is null
       inner join
       biz_opportunities            opp
        on bat.opportunity_id       = opp.id
       and opp._deleted_date        is null
       and opp.is_closed            = true
       and opp.is_won               = true
       and opp.close_date between add_months(date_trunc(month,current_date),-1) and last_day(dateadd(month,-1,current_date))
       left outer join
       biz_channels                 ch
        on ut.channel               = ch.id
       and ch._deleted_date         is null
 where ut._deleted_date is null
group by 1
```

**What is the entire journey for one person?  (Show all Touchpoints for a single email address.)**

```
select ut.touchpoint_date
      ,ut.marketing_touch_type
      ,listagg(distinct ifnull(sdl.stage_name,sdo.stage_name),',')           as touchpoint_position
  from biz_user_touchpoints         ut
       left outer join
       biz_touchpoints              bt
        on bt.user_touchpoint_id    = ut.id
       and bt._deleted_date         is null
       left outer join
       biz_attribution_touchpoints  bat
        on bat.user_touchpoint_id   = ut.id
       and bat._deleted_date        is null
       left outer join
       biz_lead_stage_transitions   lst
        on lst.touchpoint_id        = bt.id
       and lst._deleted_date        is null
       and lst.is_pending           = false
       and lst.is_non_transitional  = false
       left outer join
       biz_stage_definitions        sdl
        on lst.stage_id             = sdl.id
       and sdl._deleted_date        is null
       left outer join
       biz_opp_stage_transitions    ost
        on ost.touchpoint_id        = bat.id
       and ost._deleted_date        is null
       and ost.is_pending           = false
       and ost.is_non_transitional  = false
       left outer join
       biz_stage_definitions        sdo
        on ost.stage_id             = sdo.id
       and sdo._deleted_date        is null
 where ut._deleted_date     is null
   and ut.email             = [email address]
group by 1,2
order by 1
```

**Show all Buyer Attribution Touchpoints (BATs) and their Attributed Revenue for a single opportunity.**

>[!NOTE]
>
>This query returns attributed revenue for the w shape model. Change the model by updating the field in the attributed revenue calculation.  

``` 
select bat.id
      ,bat.touchpoint_date
      ,bat.email
      ,opp.amount*(bat.w_shape_percentage/100)             as attributed_revenue
      ,listagg(osd.stage_name,', ')                        as touchpoint_position
  from biz_opportunities               opp
       inner join
       biz_attribution_touchpoints     bat
        on bat.opportunity_id      = opp.id
       and bat._deleted_date       is null
       left outer join
       biz_opp_stage_transitions       ost
        on ost.touchpoint_id       = bat.id
       and ost._deleted_date       is null
       and ost.is_pending          = false
       and ost.is_non_transitional = false
       left outer join
       biz_stage_definitions            osd
        on ost.stage_id             = osd.id
       and osd._deleted_date        is null
 where opp._deleted_date    is null
   and opp.id               = [opportunity id]
group by 1,2,3,4
order by touchpoint_date
```

[Back to top](#data-warehouse-schema)
