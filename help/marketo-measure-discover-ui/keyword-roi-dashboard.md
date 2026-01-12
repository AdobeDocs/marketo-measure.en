---
description: Keyword ROI Dashboard - [!DNL Marketo Measure] - Product
title: Keyword ROI Dashboard
feature: Reporting
exl-id: 9c85a3ad-1806-4e30-b0fb-686760aea587
---
# Keyword ROI Dashboard {#keyword-roi-dashboard}

The Keyword ROI Dashboard provides detailed insights into the performance of Paid Search campaigns. It delivers a comprehensive analysis of keyword-level costs, attributed revenue, and the new leads and opportunities generated, ensuring a clear understanding of keyword ROI.

Questions the dashboard answers:

* What is the ROI for each keyword in Google Adwords, Linkedin, and Bing Ads?
* How do costs and attributed revenue break down by individual keywords?
* How many leads and opportunities were created from each keyword?

## Dashboard Components {#dashboard-components}

### Keyword ROI Summary Table {#keyword-roi-summary-table}

Table displaying attributed revenue, costs, and ROI segmented by individual keywords for a detailed breakdown.

Drill down into specific keywords to view the opportunities influenced by each.

**Columns:**

* **Keyword**
* **Campaign**
* **Ad Account ID**
* **Ad Account Name**
* **Ad Group ID**
* **Ad Group Name**
* **Cost**: Total costs from connected data sources. 
* **Attributed Revenue**: The total revenue contribution, based on the chosen attribution model, from Opportunities with touchpoints that closed within the filtered date period
* **Realized Attributed Revenue**: The total revenue contribution, based on the chosen attribution model, from Opportunities with touchpoints within the filtered date period, regardless of when they were closed.
* **Unrealized Attributed Pipeline Revenue**: Pipeline revenue linked to touchpoints (Open Opportunities) created within the filtered date period.
* **Simple ROI**: Attributed revenue divided by costs in the filtered date period.
* **Realized ROI**: Realized attributed revenue divided by costs in the filtered date period.

### Leads & Opportunities by Keyword Table {#leads-and-opportunities-by-keyword-table}

Table displaying new leads, opportunities, and associated costs segmented by individual keywords for a detailed breakdown.

Drill down into specific keywords to view the opportunities influenced by each.

**Columns:**

* **Keyword**
* **Campaign**
* **Ad Account ID**
* **Ad Account Name**
* **Ad Group ID**
* **Ad Group Name**
* **Cost**
* **New Leads**: Total number of new Leads generated, including both touched and untouched Leads.
* **Cost per New Lead**: The average cost per new Lead, derived from the total cost divided by the total number of new Leads.
* **New Opportunities**: Total number of new Opportunities generated, including both touched and untouched Opportunities.
* **Cost per New Opportunity**: The average cost per new Opportunity, derived from the total cost divided by the total number of new Opportunities.

## Filter Pane {#filter-pane}

This dashboard is equipped with the following settings and filters:

* Date 
  * Based on:
    * Created Date: News Leads, new Opportunities
    * Cost incurred date: cost
    * Closed date: attributed revenue (simple ROI), deals
    * Touchpoint date: touchpoints from realized attributed revenue (realized ROI)
* Attribution Model
* Keyword
* Campaign
