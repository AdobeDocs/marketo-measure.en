---
description: Engagement Dashboard - [!DNL Marketo Measure] - Product
title: Engagement Dashboard
feature: Reporting
exl-id: dc8bcbe4-d470-4cd3-a2d9-804fdebe7121
---
# Engagement Dashboard {#engagement-dashboard}

The Engagement Dashboard meticulously tracks user engagement metrics. It showcases touchpoints, the number of people engaged, and the average touchpoints per person. Utilize the time series bar chart for a monthly, quarterly, or yearly view, and the bar chart for detailed Channel, Subchannel, and Campaign insights. This tool is essential for understanding engagement patterns and fine-tuning your engagement strategies.

We track every customer interaction as User Touchpoints (UTs), the "raw" collected data points, which serve as the foundation for engagement metrics on our dashboard. Not all UTs evolve into Buyer Touchpoints (BTs) or Buyer Attribution Touchpoints (BATs), as these are selected outcomes for attributing specific customer interactions to revenue-related activities. It's important to note that suppression rules do not affect UTs or the engagement dashboard.

* **User Touchpoints**: Touchpoints created from all engagements. 
* **Buyer Touchpoints**: Touchpoints selected for Lead and Contact attribution. BTs are not linked to Opportunities and have no associated revenue.
* **Buyer Attribution Touchpoints**: Touchpoints selected for Opportunity attribution. BATs have revenue implications as they are linked to Opportunities.

Using only BTs or BATs to measure engagement would understate the true extent of customer interactions since engagement is broader than just attribution.

Questions the dashboard answers:

* How many people were engaged? What is the average number of touches per engaged person?
* How does the number of touchpoints compare to People Touched within a specific Channel/Subchannel/Campaign?
* How many touchpoints were there by a given channel or subchannel? How did it change over time?

>[!NOTE]
>
>Account and Opportunity engagement metrics are scheduled for release in the first half of 2024.

## Dashboard Components {#dashboard-components}

### KPI Tiles {#kpi-tiles}

* Touchpoints: The total number of raw touchpoints generated.
  * Buyer Touchpoints and Buyer Attribution Touchpoints are attribution outcomes that are created by selecting specific touchpoints for credit. Not all touchpoints are selected as BTs and BATs.
* People Touched: The total number of people who have any touchpoints.
* Touchpoints per Person: Average number of touchpoints per person who have been touched.

### Touchpoints and People Touched Over Time {#touchpoints-and-people-touched-over-time}

The time series bar chart displays the number of touchpoints, People Touched, and touchpoints per person for each month, quarter, and year.

* use the drill-down and up functionalities to categorize the data by Month, Quarter, or Year.
* Hover over a bar or line to reveal detailed information.

Questions the chart answers:

* How has the number of touchpoints and People Touched evolved over time?
* How do the touchpoints per person compare from one quarter/month to the next?

![](assets/engagement-dashboard-1.png)

### Touchpoints/People Touched by Channel {#touchpoints-people-touched-by-channel}

Bar chart displaying touchpoints or People Touched segmented by Channel/Subchannel/Campaign.

* use the drill-down and up functionalities to categorize the data by Subchannel and Campaign.
* Hover over each bar to view the touchpoints or People Touched.

Questions the chart answers:

* Which Channel/Subchannel/Campaign drove the most engagement?
* How does the number of touchpoints compare to People Touched within a specific Channel/Subchannel/Campaign?

![](assets/engagement-dashboard-2.png)

## Filter Pane {#filter-pane}

This dashboard is equipped with the following settings and filters:

* Date (based on Touchpoint Date)
* Channel, Subchannel
* Campaign
