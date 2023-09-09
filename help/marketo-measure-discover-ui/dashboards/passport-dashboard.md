---
description: Passport Dashboard - [!DNL Marketo Measure] - Product
title: Passport Dashboard
hide: yes
hidefromtoc: yes
feature: Reporting
---
# Passport Dashboard {#passport-dashboard}

The Passport dashboard offers marketers a dynamic view of Leads, Contacts, and Opportunities as they transition through various stages within a specified period. By filtering for a specific date, users can also obtain a snapshot of records for that day.

>[!NOTE]
>
>This dashboard is currently in Beta. During this transitional phase, both the current and new dashboards will be accessible. The current dashboard will be deprecated once we've fully transitioned and ensured optimal functionality.

**Questions the board answers:**

* How many leads, contacts, or opportunities existed in each non-terminal stage on any chosen day?
* Throughout a specified period, how many distinct Leads or Contacts progressed through each transient stage?
   * _Example_: If Lead A was in stage 1 on 1/1/2023 and advanced to stage 5 by 3/31/2023, the Q1 2023 Passport analysis would count Lead A in stages 1 through 5.
* How many unique opportunities passed through each transient stage during a given time frame?

## Dashboard Components {#dashboard-components}

### Opportunities in Stage by Stage Name {#opportunities-in-stage-by-stage-name}

* Each stage shows the number of Opportunities with touchpoints that have passed through them in a given timeframe.
  * If an opportunity progresses through multiple stages within that span, it's counted in every stage it passes. 
* Terminal stages such as "Closed Won" and "Closed Lost" are excluded.
* Both start and end dates are inclusive.

![](assets/passport-dashboard-1.png)

### Leads or Contacts in Stage by Stage Name {#leads-or-contacts-in-stage-by-stage-name}

* Each stage shows the number of Leads or Contacts with touchpoints that have passed through them in a given timeframe.
  * Whether to display "Lead" or "Contact" is determined by the preference set in: Settings > Attribution Settings > Default Dashboard Object.
  * If a Lead or Contact progresses through multiple stages within that span, it's counted in every stage it passes. 
* Terminal stages such as "Closed Won" and "Closed Lost" are excluded.
* Both start and end dates are inclusive.

![](assets/passport-dashboard-2.png)

## Filter Pane {#filter-pane}

This dashboard is equipped with the following settings and filters:

* Date (based on Transition Date)
* Attribution Model
* Channel, Subchannel
* Campaign
* Segments

>[!MORELIKETHIS]
>
>[Discover Dashboard Basics](/help/marketo-measure-discover-ui/dashboards/discover-dashboard-basics.md){target="_blank"}
