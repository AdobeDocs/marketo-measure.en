---
description: Marketo Measure 101 Reports Overview - Measure - Product Documentation
title: Marketo Measure 101 Reports Overview
exl-id: 83977b81-8055-47fd-8a6b-5ef32d280269
---
# Marketo Measure 101 Reports Overview {#marketo-measure-101-reports-overview}

All Bizible customers using Bizible and Salesforce have access to the ‘Bizible Touchpoints Reports' folder within their SFDC instance. This folder contains a number of pre-built reports that can help you get started on reporting with Bizible touchpoint data.

![](assets/bizible-101-reports-overview-1.png)

While many of these reports have specific reporting goals already established, there are six “_Bizible 101…_” represented by three key report types that cover a majority of reporting needs.

* Leads with Bizible Touchpoints
* Bizible Persons with Bizible Touchpoints
* Bizible Attribution Touchpoints with Opportunities

![](assets/bizible-101-reports-overview-2.png)

These reports provide you with the basic fields and infrastructure needed for any Bizible related report that you want to create. We encourage all customers, new and old, to begin with these reports when exploring marketing attribution questions. Below you will find an explanation of each of the six “_Bizible 101…_” reports.

_If you cannot find the Bizible Touchpoints Report folder or the six “_Bizible 101…_” reports within that folder, please reach out to support for assistance._

**Leads with Bizible Touchpoints** | The following two variations, report on Leads and their Bizible Touchpoints. Although they use the same base report type, they are grouped by different metrics, Lead ID vs Marketing Channel, to provide two key views of the data. This report type is designed for top of funnel reporting and is ideal when looking to explore how your Leads are engaging with your marketing efforts. Before any customization, the two reports below display the following:

**Bizible 101: Leads by Channel** | A high-level view of how your Marketing Channels are influencing the creation of Leads and their additional engagements.
**Bizible 101: Leads by ID** | This displays the Leads story and is a much more granular report, showing each individual Lead and their related Bizible Touchpoints.

**Leads/Contacts with Bizible Touchpoints** | These reports are commonly referred to as the Bizible Persons reports. They use Bizible’s custom object the _Bizible Person_ as opposed to the Lead object in the reports mentioned above.

The Bizible Person Object relates the Lead and Contact objects together. Out of the box, Salesforce does not provide the option to create reports using the Lead and Contact object in the same report. By relating to the Lead and Contact Object using a person’s unique identifier, their email, the Bizible Person can report on both Lead and Contact related Bizible Touchpoints within the same report. This report type is ideal when looking to validate any of your Bizible Account Settings as it is the most inclusive level of touchpoint reporting.

The following two report variations use the same report type, but are grouped by different metrics, Person ID (email) vs Marketing Channel. These are top of funnel/middle of funnel reports that are great when looking to explore how your Leads and Contacts are engaging with your marketing efforts. Before any customization, the two reports below display the following:

**Bizible 101: Lead/Contacts by Channel** | A high-level view of how your Marketing Channels are influencing the creation of Leads or Contacts and their additional engagements. This report is ideal when looking to understand total engagement across your Marketing Channels and which Marketing Channels are driving net new names within your Salesforce instance.
**Bizible 101: Lead/Contacts by ID** | This displays each Bizible Person’s story and is a much more granular report, showing each individual and their Bizible Touchpoints, regardless of if the touchpoint occurred when they were a Lead or as a Contact.

**Opportunities with Bizible Attribution Touchpoints** | The last two “_Bizible 101…_” reports are bottom of the funnel reports which display the Bizible Attribution Touchpoint data related to Opportunities. The key differentiator for these reports is that they are built off of _Bizible Attribution Touchpoints_ which relate to the Opportunity and Opportunity level data such as revenue. Whenever you are looking to report on Opportunities or attributed revenue, this report type should be used. The two reports below use the same report type, however, they are grouped by different metrics, Opportunity ID vs Marketing Channel. Before any customization, the two reports below display the following:

**Bizible 101: Opportunities by Channel** | A high-level view of how your Marketing Channels are influencing and driving attributed revenue across your Opportunities.
**Bizible 101: Opportunities by ID** | This granular report version shows you the complete journey of your Opportunities. In this report you can see every Bizible Attribution Touchpoint associated to an Opportunity and its attributed revenue through the various attribution models.

It's considered a best practice to treat the “_Bizible 101…_” reports as templates for your reporting needs. Starting with one of the reports above will save you time and ensure that you are working with the correct fields related to Bizible data. Always make sure you “Save As” any time you make customizations to the “_Bizible 101…_” templates in order to retain the original variation of the report.

The "Bizible Touchpoint Reports" folder is designed to help you get started on your Bizible reporting, for actionable reports you will need to customize those reports so that they are tailored to your reporting needs. You'll need to add necessary filters to ensure the records within the report (and their related touchpoints) are aligned with your reporting goal.

Once you’re familiar with the “_Bizible 101…_” reports, you may want to recreate them from custom report types for more custom reporting needs. Creating the [Bizible Custom Report Types](/help/bizible-salesforce-reporting/new-report-types/creating-custom-bizible-report-types.md) will allow you to pull in custom fields that you might commonly use in other CRM reports. This will help you take you Bizible reporting to the next level!
