---
description: ROI Dashboard - [!DNL Marketo Measure] - Product
title: ROI Dashboard
feature: Reporting
exl-id: 878db6e0-3ac7-4f4c-b993-bd7a1cfa0638
---
# ROI Dashboard {#roi-dashboard}

The ROI Dashboard provides marketers with a granular view of returns on investment across channels, subchannels, and campaigns. It meticulously breaks down cost and revenue patterns, while also spotlighting metrics like cost-per-lead, deal, and opportunity, ensuring a comprehensive understanding of marketing attribution.

**Questions the board answers**

* What were the ROI values for each channel, subchannel, and campaign?
* How did the costs and revenues distribute across each channel, subchannel, and campaign?
* What was the cost-per-lead, cost-per-deal, and cost-per-opportunity?

## Dashboard Components {#dashboard-components}

### KPI Tiles {#kpi-tiles}

* **Cost**: Total costs from connected data sources and manually uploaded costs.
* **Attributed Revenue**: The total revenue contribution, based on the chosen attribution model, from Opportunities with touchpoints that closed within the filtered date period.
* **Realized Attributed Revenue**: The total revenue contribution, based on the chosen attribution model, from Opportunities with touchpoints within the filtered date period, regardless of when they were closed.
* **Total New Leads**: Total number of new Leads generated, including both touched and untouched Leads.
* **Cost per New Lead**: The average cost per new Lead, derived from the total cost divided by the total number of new Leads.
* **Total New Opportunities**: Total number of new Opportunities generated, including both touched and untouched Opportunities.
* **Cost per New Opportunity**: The average cost per new Opportunity, derived from the total cost divided by the total number of new Opportunities.
* **Total Deals**: The number of "Closed Won" Opportunities, including Opportunities without touchpoints.
* **Simple ROI**: Attributed revenue divided by costs in the filtered date period.
* **Realized ROI**: Realized attributed revenue divided by costs in the filtered date period.

![](assets/roi-dashboard-1.png)

### Cost and Revenue by Channel Graph {#cost-and-revenue-by-channel-graph}

Bar chart illustrating cost and revenue, designed to offer a comparative perspective on their magnitude relative to various channels, subchannels, and campaigns.

* use the drill-down and up functionalities to categorize the data by Subchannel and Campaign.
* Hover over each bar to view the Simple and Realized ROIs.

**Questions the chart answers**

* What were the ROI values for each channel, subchannel, and campaign?
* Are there any outlier channels or subchannels with unusually high or low costs relative to their revenue?

![](assets/roi-dashboard-2.png)

### Realized vs Simple ROI Over Time {#realized-vs-simple-roi-over-time}

Time series line chart displaying the comparison between Realized and Simple ROI, tracking their progression over time.

* Hover over a section on the graph to view the Simple and Realized ROIs.

**Questions the chart answers**

* How does the Realized ROI compare to the Simple ROI over specific time periods?
* How does the trend of Realized ROI relate to any significant marketing events during the same period?

![](assets/roi-dashboard-3.png)

### Cost Over Time Graph {#cost-over-time-graph}

Stacked bar chart displaying Total Costs, segmented by associated Channels for each Month/Quarter/Year.

* use the drill-down and up functionalities to categorize the data by Month, Quarter, or Year.
* Hover over a bar segment or the space between bars to reveal detailed information.

**Questions the chart answers**

* How does the combined cost of all channels compare from one quarter/month to the next?
* How have costs for a specific channel evolved over time?

![](assets/roi-dashboard-4.png)

### Cost by Channel Graph {#cost-by-channel-graph}

Bar chart displaying marketing spend segmented by Channel/Subchannel/Campaign.

* use the drill-down and up functionalities to categorize the data by Channel/Subchannel/Campaign.

**Questions the chart answers**

* Which subchannels or campaigns within a primary channel have the highest allocation?
* Which marketing avenues (channel, subchannel, or campaign) seem underfunded compared to others?

![](assets/roi-dashboard-5.png)

### ROI Summary Table {#roi-summary-table}

Table displaying attributed revenue, costs, and ROI segmented by individual channels for a detailed breakdown.

* Click the "+" icon beside each Channel to reveal the breakdown by Subchannel and Campaign.

**Columns**

* Channel/Subchannel/Campaign
* Cost
* Attributed Revenue
* Realized Attributed Revenue
* Simple ROI
* Realized ROI
* Unrealized Attributed Pipeline Revenue: Pipeline revenue linked to touchpoints (Open Opportunities) created within the filtered date period.

### Marketing Spend Table {#marketing-spend-table}

Table displaying costs, new Leads, Opportunities, and deals closed segmented by individual channels for a detailed breakdown.

* Click the "+" icon beside each Channel to reveal the breakdown by Subchannel and Campaign.

**Columns**

* Channel/Subchannel/Campaign
* Cost
* New Leads
* Cost per New Lead 
* New Opportunities
* Cost per New Opportunity 
* Deals
* Cost per Deal

## Filter Pane {#filter-pane}

This dashboard is equipped with the following settings and filters:

* Date 
  * Based on:
    * Created Date: News Leads, new Opportunities
    * Cost incurred date: cost
    * Closed date: attributed revenue (simple ROI), deals
    * Touchpoint date: touchpoints from realized attributed revenue (realized ROI)
* Attribution Model
* Channel, Subchannel
* Campaign

>[!MORELIKETHIS]
>
>* [Discover Dashboard Basics](/help/marketo-measure-discover-ui/dashboards/discover-dashboard-basics.md){target="_blank"}
>* [Dashboard Data Visibility Policy](/help/marketo-measure-discover-ui/dashboards/dashboard-data-visibility-policy.md){target="_blank"}

