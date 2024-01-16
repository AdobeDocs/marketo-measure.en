---
description: '[!DNL Marketo Measure] Ultimate Data Integrity Requirement - [!DNL Marketo Measure] - Product Documentation'
title: '[!DNL Marketo Measure] Ultimate Data Integrity Requirement'
feature: Integration, Tracking, Attribution
exl-id: 8ad001d0-e9fe-46f5-b808-d6203a55a229
---
# [!DNL Marketo Measure] Ultimate Data Integrity Requirement {#marketo-measure-ultimate-data-integrity-requirement}

[!DNL Marketo Measure] validates the incoming AEP datasets to ensure the data is sufficient and coherent for the purpose of attribution. Failing to meet the data integrity requirement will cause the dataset to be rejected by the [!DNL Marketo Measure] system. This document details the data integrity requirement, provides query examples for data inspection, and recommends a solution for required fields with a null value.

## Entity Object {#entity-object}

<table style="table-layout:auto">
  <tr>
    <th>XDM Class</th>
    <th>XDM Field Group</th>
    <th>XDM Path</th>
    <th>XDM Type</th>
    <th>Data Source Field</th>
    <th>Required?</th>
    <th>Notes</th>
  </tr>
  <tbody>
    <tr>
      <td colspan="7"><strong>Account</strong> (Account for Salesforce, Company and/or Named Account for Marketo)</td>
    </tr>
    <tr>
      <td rowspan="6">XDM Business Account</td>
      <td></td>
      <td>accountKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - 123@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceID</td>
      <td>string</td>
      <td>ID</td>
      <td>Yes</td>
      <td>E.g. - 123</td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>date-time</td>
      <td>CreatedDate</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>date-time</td>
      <td>ModifiedDate</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>XDM Business Account Details</td>
      <td>accountName</td>
      <td>string</td>
      <td>Name</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td colspan="7"><strong>Campaign</strong> (Campaign for Salesforce, Program for Marketo)</td>
    </tr>
    <tr>
      <td rowspan="8">XDM Business Campaign</td>
      <td></td>
      <td>campaignKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - 55555@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceID</td>
      <td>string</td>
      <td>ID</td>
      <td>Yes</td>
      <td>E.g. - 55555</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>date-time</td>
      <td>CreatedDate</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>date-time</td>
      <td>ModifiedDate</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>campaignName</td>
      <td>string</td>
      <td>Name</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>campaignType</td>
      <td>string</td>
      <td>CampaignType</td>
      <td>No</td>
      <td>For channel mapping</td>
    </tr>
    <tr>
      <td></td>
      <td rowspan="5">XDM Business Campaign Details</td>
      <td>channelName</td>
      <td>string</td>
      <td>ChannelName</td>
      <td>No</td>
      <td>For channel mapping</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignStartDate</td>
      <td>date-time</td>
      <td>StartDate</td>
      <td>No</td>
      <td>For campaign cost</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignEndDate</td>
      <td>date-time</td>
      <td>EndDate</td>
      <td>No</td>
      <td>For campaign cost</td>
    </tr>
    <tr>
      <td></td>
      <td>actualCost.amount</td>
      <td>number</td>
      <td>Cost</td>
      <td>No</td>
      <td>For campaign cost</td>
    </tr>
    <tr>
      <td></td>
      <td>actualCost.currencyCode</td>
      <td>
        <p>string</p>
        <p>^[A-Z]{3}$</p>
      </td>
      <td>CurrencyIsoCode</td>
      <td>No</td>
      <td>For campaign cost</td>
    </tr>
    <tr>
      <td colspan="7"><strong>Campaign Member</strong> (Campaign Member for Salesforce, Program Memberships for Marketo)</td>
    </tr>
    <tr>
      <td rowspan="14">XDM Business Campaign Members</td>
      <td></td>
      <td>campaignMemberKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - 987654321@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignMemberKey.sourceID</td>
      <td>string</td>
      <td>ID</td>
      <td>Yes</td>
      <td>E.g. - 987654321</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignMemberKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignMemberKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>date-time</td>
      <td>CreatedDate</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>date-time</td>
      <td>ModifiedDate</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - 333@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceID</td>
      <td>string</td>
      <td>Lead ID or Contact ID</td>
      <td>Yes</td>
      <td>
        <p>E.g. - 333, depending on the data source table, this is either Lead ID or Contact ID.</p>
        <p>Foreign key to Lead or Contact</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - 55555@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceID</td>
      <td>string</td>
      <td>Campaign ID</td>
      <td>Yes</td>
      <td>
        <p>E.g. - 55555.</p>
        <p>Foreign key to Campaign</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td rowspan="4">XDM Business Campaign Member Details</td>
      <td>b2b.personType</td>
      <td>string</td>
      <td>"Lead" or "Contact</td>
      <td>Yes</td>
      <td>Depending on the data source table, this should be set to either "Lead" or "Contact". We recommend setting it to "Contact" for most use cases</td>
    </tr>
    <tr>
      <td></td>
      <td>memberStatus</td>
      <td>string</td>
      <td>Status</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>hasResponded</td>
      <td>boolean</td>
      <td>HasResponded</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>firstRespondedDate</td>
      <td>date-time</td>
      <td>FirstRespondedDate</td>
      <td>No</td>
      <td></td>
    </tr>
    <tr>
      <td colspan="7"><strong>Person</strong> (Contact or Lead for Salesforce, Persons for Marketo)</td>
    </tr>
    <tr>
      <td>XDM Individual Profile</td>
      <td rowspan="11">XDM Business Person Details</td>
      <td>b2b.personKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>e.g. - 333@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.personKey.sourceID</td>
      <td>string</td>
      <td>ID</td>
      <td>Yes</td>
      <td>e.g. - 333, depending on the data source table, this is either Lead ID or Contact ID</td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.personKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.personKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>workEmail.address</td>
      <td>
        <p>string</p>
        <p>email</p>
      </td>
      <td>Email</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.personStatus</td>
      <td>string</td>
      <td>Status</td>
      <td><mark>Yes for Lead personType only</mark></td>
      <td>Only required if b2b.personType is "Lead"</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>date-time</td>
      <td>CreatedDate</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>date-time</td>
      <td>ModifiedDate</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.isConverted</td>
      <td>boolean</td>
      <td>IsConverted</td>
      <td><mark>Yes for Lead personType only</mark></td>
      <td>Only required if b2b.personType is "Lead"</td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.personType</td>
      <td>string</td>
      <td>"Lead" or "Contact</td>
      <td>Yes</td>
      <td>Depending on the data source table, this should be set to either "Lead" or "Contact". We recommend setting it to "Contact" for most use cases</td>
    </tr>
    <tr>
      <td></td>
      <td>extendedWorkDetails.jobTitle</td>
      <td>string</td>
      <td></td>
      <td>No</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td rowspan="4">XDM Business Person Components</td>
      <td>personComponents.sourceAccountKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>No</td>
      <td>
        <p>E.g. - 123@999-abc-888.Marketo.</p>
        <p>The set of sourceAccountKey fields is only "required" for true Contact records, defined as person records linked to Account. Missing it won't cause the dataset to be rejected but the attribution results will be off.</p>
        <p>personComponents is an array but Marketo Measure only takes the first element personComponents[0]</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>personComponents.sourceAccountKey.sourceID</td>
      <td>string</td>
      <td>Account ID</td>
      <td>No</td>
      <td>
        <p>E.g. - 123.</p>
        <p>Foreign key to Account</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>personComponents.sourceAccountKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>No</td>
      <td>e.g. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>personComponents.sourceAccountKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>No</td>
      <td>E.g. - Marketo</td>
    </tr>
    <tr>
      <td colspan="7"><strong>Opportunity</strong> (Opportunity for Salesforce, Opportunities for Marketo)</td>
    </tr>
    <tr>
      <td rowspan="13">XDM Business Opportunity</td>
      <td></td>
      <td>opportunityKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>e.g. - 77777@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceID</td>
      <td>string</td>
      <td>ID</td>
      <td>Yes</td>
      <td>E.g. - 77777</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>date-time</td>
      <td>CreatedDate</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>date-time</td>
      <td>ModifiedDate</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>e.g. - 123@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceID</td>
      <td>string</td>
      <td>Account ID</td>
      <td>Yes</td>
      <td>
        <p>E.g. - 123.</p>
        <p>Foreign key to Account</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityName</td>
      <td>string</td>
      <td>Name</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityStage</td>
      <td>string</td>
      <td>Stage</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityType</td>
      <td>string</td>
      <td></td>
      <td>No</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td rowspan="5">XDM Business Opportunity Details</td>
      <td>isWon</td>
      <td>boolean</td>
      <td>IsWon</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>isClosed</td>
      <td>boolean</td>
      <td>IsClosed</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>expectedCloseDate</td>
      <td>date</td>
      <td>CloseDate</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityAmount.amount</td>
      <td>number</td>
      <td>Amount</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityAmount.currencyCode</td>
      <td>
        <p>string</p>
        <p>^[A-Z]{3}$</p>
      </td>
      <td>CurrencyIsoCode</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td colspan="7"><strong>Opportunity Contact Role (Needed only if plan to use Opportunity Contact Role as the buying group for attribution)</strong></td>
    </tr>
    <tr>
      <td rowspan="16">XDM Business Opportunity Person Relation</td>
      <td></td>
      <td>personKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>e.g. - 333@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceID</td>
      <td>string</td>
      <td>Contact ID</td>
      <td>Yes</td>
      <td>
        <p>e.g. - 333.</p>
        <p>Foreign key to Contact</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>isPrimary</td>
      <td>boolean</td>
      <td>IsPrimary</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>e.g. - 77777@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceID</td>
      <td>string</td>
      <td>Opportunity ID</td>
      <td>Yes</td>
      <td>
        <p>e.g. - 77777.</p>
        <p>Foreign key to Opportunity</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityPersonKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>e.g. - 222222@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityPersonKey.sourceID</td>
      <td>string</td>
      <td>ID</td>
      <td>Yes</td>
      <td>e.g. - 222222</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityPersonKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityPersonKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>personRole</td>
      <td>string</td>
      <td>Role</td>
      <td>No</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>date-time</td>
      <td>CreatedDate</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>date-time</td>
      <td>ModifiedDate</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td colspan="7"><strong>Conversion Rate (Needed only if use multiple currencies; Only one Conversion Rate dataset can be activated to Marketo Measure)</strong></td>
    </tr>
    <tr>
      <td rowspan="7">Conversion</td>
      <td></td>
      <td>extSourceSystemAudit.externalKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>e.g. - 8888@0x012345.Salesforce</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.externalKey.sourceId</td>
      <td>string</td>
      <td>ID</td>
      <td>Yes</td>
      <td>e.g. - 8888</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.externalKey.sourceInstanceId</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - 0x012345</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.externalKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - Salesforce</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>date-time</td>
      <td>CreatedDate</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>date-time</td>
      <td>ModifiedDate</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>isDeleted</td>
      <td>boolean</td>
      <td></td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td rowspan="5">Currency Conversion Rate Details</td>
      <td>conversionRate</td>
      <td>number</td>
      <td>ConversionRate</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>endDate</td>
      <td>date</td>
      <td>NextStartDate</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>startDate</td>
      <td>date</td>
      <td>StartDate</td>
      <td>Yes</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>sourceISOCode</td>
      <td>string</td>
      <td>ISOCode</td>
      <td>Yes</td>
      <td>E.g. EUR</td>
    </tr>
    <tr>
      <td></td>
      <td>targetISOCode</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>The default currency code set in Marketo Measure, e.g. USD</td>
    </tr>
  </tbody>
</table>

## ExperienceEvent {#experienceevent}

<table style="table-layout:auto">
  <tr>
    <th>XDM Class</th>
    <th>XDM Field Group</th>
    <th>XDM Path</th>
    <th>XDM Type</th>
    <th>Data Source Field</th>
    <th>Required?</th>
    <th>Notes</th>
  </tr>
  <tbody>
    <tr>
      <td colspan="7"><strong>Activity</strong></td>
    </tr>
    <tr>
      <td rowspan="3">XDM ExperienceEvent</td>
      <td></td>
      <td>_id</td>
      <td>string</td>
      <td>ID</td>
      <td>Yes</td>
      <td>Yes</td>
    </tr>
    <tr>
      <td></td>
      <td>eventType</td>
      <td>string</td>
      <td>ActivityType</td>
      <td>Yes</td>
      <td>Yes</td>
    </tr>
    <tr>
      <td></td>
      <td>timestamp</td>
      <td>date-time</td>
      <td>Activity Date</td>
      <td>Yes</td>
      <td>Yes</td>
    </tr>
    <tr>
      <td></td>
      <td>Person Identifier</td>
      <td>personKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - 333@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>personKey.sourceID</td>
      <td>string</td>
      <td>Lead ID or Contact ID</td>
      <td>Yes</td>
      <td>
        <p>E.g. - 333, depending on the data source table, this is either Lead ID or Contact ID.</p>
        <p>Foreign key to Lead or Contact</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>personKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>personKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Yes</td>
      <td>E.g. - Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>Add To Campaign</td>
      <td>leadOperation.addToCampaign.campaignKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Yes for leadOperation.addToCampaign type only</td>
      <td>E.g. - 55555@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.addToCampaign.campaignKey.sourceId</td>
      <td>string</td>
      <td>Campaign ID</td>
      <td>Yes for leadOperation.addToCampaign type only</td>
      <td>
        <p>E.g. - 55555.</p>
        <p>Foreign key to Campaign</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.addToCampaign.campaignKey.sourceInstanceId</td>
      <td>string</td>
      <td></td>
      <td>Yes for leadOperation.addToCampaign type only</td>
      <td>E.g. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.addToCampaign.campaignKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Yes for leadOperation.addToCampaign type only</td>
      <td>E.g. - Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>Status in Campaign Progression Changed</td>
      <td>leadOperation.campaignProgression.campaignKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Yes for leadOperation.campaignProgression type only</td>
      <td>E.g. - 55555@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.campaignProgression.campaignKey.sourceId</td>
      <td>string</td>
      <td>Campaign ID</td>
      <td>Yes for leadOperation.campaignProgression type only</td>
      <td>
        <p>E.g. - 55555.</p>
        <p>Foreign key to Campaign</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.campaignProgression.campaignKey.sourceInstanceId</td>
      <td>string</td>
      <td></td>
      <td>Yes for leadOperation.campaignProgression type only</td>
      <td>E.g. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.campaignProgression.campaignKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Yes for leadOperation.campaignProgression type only</td>
      <td>E.g. - Marketo</td>
    </tr>
  </tbody>
</table>

## ExperienceEvent Type Supported {#experienceevent-type-supported}

<table style="table-layout:auto">
  <tr>
    <th>Event Type</th>
    <th>XDM Event Type</th>
    <th>Description</th>
  </tr>
  <tbody>
    <tr>
      <td>New Lead</td>
      <td>leadOperation.newLead</td>
      <td>Use to record the creation and details of a new marketing lead</td>
    </tr>
    <tr>
      <td>Convert Lead</td>
      <td>leadOperation.convertLead</td>
      <td>Use when a marketing lead is converted into a sales-qualified contact that is assigned to a sales user</td>
    </tr>
    <tr>
      <td>Interesting Moment</td>
      <td>leadOperation.interestingMoment</td>
      <td>Use for tracking high value activities by potential customers</td>
    </tr>
    <tr>
      <td>Fill Out Form</td>
      <td>web.formFilledOut</td>
      <td>Use to capture details when a person fills out a form on a web page</td>
    </tr>
    <tr>
      <td>Unsubscribe Email</td>
      <td>directMarketing.emailUnsubscribed</td>
      <td>Use to capture details when a person unsubscribes from an email</td>
    </tr>
    <tr>
      <td>Open Email</td>
      <td>directMarketing.emailOpened</td>
      <td>Use to capture details when a person opens a marketing email</td>
    </tr>
    <tr>
      <td>Click Email</td>
      <td>directMarketing.emailClicked</td>
      <td>Use to capture details when a person clicks a link in a marketing email</td>
    </tr>
    <tr>
      <td>Change Status in Progression</td>
      <td>leadOperation.statusInCampaignProgressionChanged</td>
      <td>Use to capture details when a lead's status in a campaign changes</td>
    </tr>
    <tr>
      <td>Add to Engagement Program (Add to Nurture)</td>
      <td>leadOperation.addToCampaign</td>
      <td>Use to add a person to the specific campaign.</td>
    </tr>
  </tbody>
</table>

Use the "Interesting Moment" event type for event types not supported in the table above. Add a custom field to indicate the sub-type "Interesting Moment".

## Query Examples for Data Inspection {#query-examples-for-data-inspection}

The following is a list of query examples for inspecting ingested datasets in AEP data lake. To use them against your datasets, replace the table name in the query examples below with your actual dataset table name.

We expect all counts to be 0.

For personType field, we expect there are only "Lead" or "Contact" values, and there is no null value.

For all "Contact" person records, we expect there is an Account foreign key.

For "Lead" person records, an Account foreign key does not exist and is not required. If you choose to ingest "Lead" person records as "Contact" person records (which is recommended), an Account foreign key on such person records is not required.

### XDM Business Account {#xdm-business-account}

```
select 'account source id', count(*) from salesforce_account where accountKey.sourceId is null
union all
select 'account source type', count(*) from salesforce_account where accountKey.sourceType is null
union all
select 'account source instance id', count(*) from salesforce_account where accountKey.sourceInstanceId is null
union all
select 'account source key', count(*) from salesforce_account where accountKey.sourceKey is null
union all
select 'account name', count(*) from salesforce_account where accountName is null
union all
select 'created date', count(*) from salesforce_account where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_account where extSourceSystemAudit.lastUpdatedDate is null;
```

### XDM Business Campaign {#xdm-business-campaign}

```
select 'campaign source id', count(*) from salesforce_campaign where campaignKey.sourceId is null
union all
select 'campaign source type', count(*) from salesforce_campaign where campaignKey.sourceType is null
union all
select 'campaign source instance id', count(*) from salesforce_campaign where campaignKey.sourceInstanceId is null
union all
select 'campaign source key', count(*) from salesforce_campaign where campaignKey.sourceKey is null
union all
select 'campaign name', count(*) from salesforce_campaign where campaignName is null
union all
select 'created date', count(*) from salesforce_campaign where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_campaign where extSourceSystemAudit.lastUpdatedDate is null;
```

### XDM Business Campaign Member {#xdm-business-campaign-member}

```
select 'campaign member source id', count(*) from salesforce_campaign_member where campaignMemberKey.sourceId is null
union all
select 'campaign member source type', count(*) from salesforce_campaign_member where campaignMemberKey.sourceType is null
union all
select 'campaign member source instance id', count(*) from salesforce_campaign_member where campaignMemberKey.sourceInstanceId is null
union all
select 'campaign member source key', count(*) from salesforce_campaign_member where campaignMemberKey.sourceKey is null
union all
select 'campaign source id', count(*) from salesforce_campaign_member where campaignKey.sourceId is null
union all
select 'campaign source type', count(*) from salesforce_campaign_member where campaignKey.sourceType is null
union all
select 'campaign source instance id', count(*) from salesforce_campaign_member where campaignKey.sourceInstanceId is null
union all
select 'campaign source key', count(*) from salesforce_campaign_member where campaignKey.sourceKey is null
union all
select 'person source id', count(*) from salesforce_campaign_member where personKey.sourceId is null
union all
select 'person source type', count(*) from salesforce_campaign_member where personKey.sourceType is null
union all
select 'person source instance id', count(*) from salesforce_campaign_member where personKey.sourceInstanceId is null
union all
select 'person source key', count(*) from salesforce_campaign_member where personKey.sourceKey is null
union all
select distinct 'person type', b2b.personType from salesforce_campaign_member
union all
select 'member status', count(*) from salesforce_campaign_member where memberStatus is null
union all
select 'has responded', count(*) from salesforce_campaign_member where hasResponded is null
union all
select 'created date', count(*) from salesforce_campaign_member where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_campaign_member where extSourceSystemAudit.lastUpdatedDate is null;
```

### XDM Business Person {#xdm-business-person}

```
select 'person source id', count(*) from marketo_person where b2b.personKey.sourceId is null
union all
select 'person source type', count(*) from marketo_person where b2b.personKey.sourceType is null
union all
select 'person source instance id', count(*) from marketo_person where b2b.personKey.sourceInstanceId is null
union all
select 'person source key', count(*) from marketo_person where b2b.personKey.sourceKey is null
union all
select 'email', count(*) from marketo_person where workEmail.address is null
union all
select 'Lead - person status', count(*) from marketo_person where b2b.personType = 'Lead' and b2b.personStatus is null
union all
select 'Lead - is converted', count(*) from marketo_person where b2b.personType = 'Lead' and b2b.isConverted is null
union all
select distinct 'person type', b2b.personType from marketo_person
union all
select 'created date', count(*) from marketo_person where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from marketo_person where extSourceSystemAudit.lastUpdatedDate is null;
```

```
select 'person source id', count(*) from salesforce_contact where b2b.personKey.sourceId is null
union all
select 'person source type', count(*) from salesforce_contact where b2b.personKey.sourceType is null
union all
select 'person source instance id', count(*) from salesforce_contact where b2b.personKey.sourceInstanceId is null
union all
select 'person source key', count(*) from salesforce_contact where b2b.personKey.sourceKey is null
union all
select 'email', count(*) from salesforce_contact where workEmail.address is null
union all
select 'Lead - person status', count(*) from salesforce_contact where b2b.personType = 'Lead' and b2b.personStatus is null
union all
select 'Lead - is converted', count(*) from salesforce_contact where b2b.personType = 'Lead' and b2b.isConverted is null
union all
select distinct 'person type', b2b.personType from salesforce_contact
union all
select 'account source id', count(*) from salesforce_contact where b2b.personType = 'Contact' and personComponents[0].sourceAccountKey.sourceId is null
union all
select 'account source type', count(*) from salesforce_contact where b2b.personType = 'Contact' and personComponents[0].sourceAccountKey.sourceType is null
union all
select 'account source instance id', count(*) from salesforce_contact where b2b.personType = 'Contact' and personComponents[0].sourceAccountKey.sourceInstanceId is null
union all
select 'account source key', count(*) from salesforce_contact where b2b.personType = 'Contact' and personComponents[0].sourceAccountKey.sourceKey is null
union all
select 'created date', count(*) from salesforce_contact where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_contact where extSourceSystemAudit.lastUpdatedDate is null;
```

### XDM Business Opportunity {#xdm-business-opportunity}

```
select 'opportunity source id', count(*) from salesforce_opportunity where opportunityKey.sourceId is null
union all
select 'opportunity source type', count(*) from salesforce_opportunity where opportunityKey.sourceType is null
union all
select 'opportunity source instance id', count(*) from salesforce_opportunity where opportunityKey.sourceInstanceId is null
union all
select 'opportunity source key', count(*) from salesforce_opportunity where opportunityKey.sourceKey is null
union all
select 'account source id', count(*) from salesforce_opportunity where accountKey.sourceId is null
union all
select 'account source type', count(*) from salesforce_opportunity where accountKey.sourceType is null
union all
select 'account source instance id', count(*) from salesforce_opportunity where accountKey.sourceInstanceId is null
union all
select 'account source key', count(*) from salesforce_opportunity where accountKey.sourceKey is null
union all
select 'opportunity name', count(*) from salesforce_opportunity where opportunityName is null
union all
select 'opportunity stage', count(*) from salesforce_opportunity where opportunityStage is null
union all
select 'is won', count(*) from salesforce_opportunity where isWon is null
union all
select 'is closed', count(*) from salesforce_opportunity where isClosed is null
union all
select 'expected close date', count(*) from salesforce_opportunity where expectedCloseDate is null
union all
select 'opportunity amount', count(*) from salesforce_opportunity where opportunityAmount.amount is null
union all
select 'currency code', count(*) from salesforce_opportunity where opportunityAmount.currencyCode is null
union all
select 'created date', count(*) from salesforce_opportunity where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_opportunity where extSourceSystemAudit.lastUpdatedDate is null;
```

### XDM ExperienceEvent {#xdm-experienceevent}

```
select 'id', count(*) from marketo_activity where _id is null
union all
select 'event type', count(*) from marketo_activity where eventType is null
union all
select 'timestamp', count(*) from marketo_activity where timestamp is null
union all
select 'person source id', count(*) from marketo_activity where personKey.sourceId is null
union all
select 'person source type', count(*) from marketo_activity where personKey.sourceType is null
union all
select 'person source instance id', count(*) from marketo_activity where personKey.sourceInstanceId is null
union all
select 'person source key', count(*) from marketo_activity where personKey.sourceKey is null
union all
select 'addToCampaign campaign id', count(*) from marketo_activity where eventType = 'leadOperation.addToCampaign' and leadOperation.addToCampaign.campaignKey.sourceId is null
union all
select 'addToCampaign campaign type', count(*) from marketo_activity where eventType = 'leadOperation.addToCampaign' and leadOperation.addToCampaign.campaignKey.sourceType is null
union all
select 'addToCampaign campaign instance id', count(*) from marketo_activity where eventType = 'leadOperation.addToCampaign' and leadOperation.addToCampaign.campaignKey.sourceInstanceId is null
union all
select 'addToCampaign campaign key', count(*) from marketo_activity where eventType = 'leadOperation.addToCampaign' and leadOperation.addToCampaign.campaignKey.sourceKey is null
union all
select 'statusInCampaignProgressionChanged campaign id', count(*) from marketo_activity where eventType = 'leadOperation.campaignProgression.campaignKey.sourceKey' and leadOperation.campaignProgression.campaignKey.sourceId is null
union all
select 'statusInCampaignProgressionChanged campaign type', count(*) from marketo_activity where eventType = 'leadOperation.campaignProgression.campaignKey.sourceKey' and leadOperation.campaignProgression.campaignKey.sourceType is null
union all
select 'statusInCampaignProgressionChanged campaign instance id', count(*) from marketo_activity where eventType = 'leadOperation.campaignProgression.campaignKey.sourceKey' and leadOperation.campaignProgression.campaignKey.sourceInstanceId is null
union all
select 'statusInCampaignProgressionChanged campaign key', count(*) from marketo_activity where eventType = 'leadOperation.campaignProgression.campaignKey.sourceKey' and leadOperation.campaignProgression.campaignKey.sourceKey is null;
```

```
select 'id', count(*) from salesforce_task where _id is null
union all
select 'event type', count(*) from salesforce_task where eventType is null
union all
select 'timestamp', count(*) from salesforce_task where timestamp is null
union all
select 'person source id', count(*) from salesforce_task where personKey.sourceId is null
union all
select 'person source type', count(*) from salesforce_task where personKey.sourceType is null
union all
select 'person source instance id', count(*) from salesforce_task where personKey.sourceInstanceId is null
union all
select 'person source key', count(*) from salesforce_task where personKey.sourceKey is null;
```

### Conversion {#conversion}

```
select 'conversion rate', count(*) from currency_conversion_rate where conversionRate is null
union all
select 'end date', count(*) from currency_conversion_rate where endDate is null
union all
select 'start date', count(*) from currency_conversion_rate where startDate is null
union all
select 'source ISO Code', count(*) from currency_conversion_rate where sourceISOCode is null
union all
select 'target ISO Code', count(*) from currency_conversion_rate where targetISOCode is null
union all
select 'source id', count(*) from currency_conversion_rate where extSourceSystemAudit.externalKey.sourceId is null
union all
select 'source type', count(*) from currency_conversion_rate where extSourceSystemAudit.externalKey.sourceType is null
union all
select 'source instance id', count(*) from currency_conversion_rate where extSourceSystemAudit.externalKey.sourceInstanceId is null
union all
select 'source key', count(*) from currency_conversion_rate where extSourceSystemAudit.externalKey.sourceKey is null
union all
select 'created date', count(*) from salesforce_contact where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_contact where extSourceSystemAudit.lastUpdatedDate is null;
```

## Recommended Solution for Required Fields with a NULL Value {#recommended-solution-for-required-fields-with-a-null-value}

We recommend using a calculated field in field mapping to default the field to a non-NULL value. The following are two examples:

* If opportunityName of some opportunity records are null, create and use the following calculated field in field mapping
   * `iif(name != null && name != "", name, "Unknown")`

* If leadOperation.campaignProgression.campaignID of some experienceevent records are null, create and use the following calculated field in field mapping
   * `iif(leadOperation.campaignProgression.campaignID != null && leadOperation.campaignProgression.campaignID != "" , to_object("sourceType", "Marketo", "sourceInstanceID", "123-abc-321", "sourceID", leadOperation.campaignProgression.campaignID, "sourceKey", concat(leadOperation.campaignProgression.campaignID,"@123-abc-321.Marketo")), iif(eventType == "leadOperation.statusInCampaignProgressionChanged", to_object("sourceType", "Marketo", "sourceInstanceID", "123-abc-321", "sourceID", "Unknown", "sourceKey", "Unknown@123-abc-321.Marketo"), null))`
