---
description: Passport Dashboard - [!DNL Marketo Measure] - Product
title: Passport Dashboard
feature: Reporting
---
# Passport Dashboard {#passport-dashboard}

The Passport dashboard offers marketers a dynamic view of Leads, Contacts, and Opportunities as they transition through various stages within a specified period. By filtering for a specific date, users can also obtain a snapshot of records for that day.

Questions the board answers:

* How many leads, contacts, or opportunities existed in each non-terminal stage on any chosen day?
* Throughout a specified period, how many distinct Leads or Contacts progressed through each transient stage?
   * _Example_: If Lead A was in stage 1 on 1/1/2023 and advanced to stage 5 by 3/31/2023, the Q1 2023 Passport analysis would count Lead A in stages 1 through 5.
* How many unique Opportunities passed through each transient stage during a given time frame?

<table style="table-layout:auto"> 
<tbody>
<tr> 
   <th>Component</th> 
   <th>Description</th>
   <th>Date Type</th>
   <th>Drill Through Fields</th>
   <th>Filters</th>
  </tr>
  <tr>
    <td>Opportunities</td>
    <td><li>Each stage shows the number of Opportunities with BATs that have passed through them in a given timeframe.</li>
<ul style="padding-left: 30px;"><li>If an Opportunity progresses through multiple stages within that span, they're counted in every stage it passed.</li></ul>
<li>Terminal stages such as "Closed Won" and "Closed Lost" are excluded.</li>
<li>Both start and end dates are inclusive.</li>
<br/><img src="assets/passport-dashboard-1.png" width="600"></td>
    <td rowspan="2">Transition date</td>
    <td></td>
    <td rowspan="2"><li>Date</li>
<li>Channel</li>
<li>Subchannel</li>
<li>Campaign</li>
<li>Segments</li></td>
  </tr>
  <tr>
    <td>Leads/Contacts</td>
    <td><li>Each stage shows the number of Leads or Contacts with BTs that have passed through them in a given timeframe.</li>
<ul style="padding-left: 30px;"><li>Whether to display "Lead" or "Contact" is determined by the preference set in: Settings > Attribution Settings > Default Dashboard Object.</li></ul>
<li>Terminal stages such as "Closed Won" and "Closed Lost" are excluded.</li>
<li>Both start and end dates are inclusive.</li>
<br/><img src="assets/passport-dashboard-2.png" width="600"></td>
    <td><li>Lead/Contact Id</li>
<li>Lead/Contact Email</li>
<li>Created date</li>
<li>Current Stage</li>
<li>Transition In Date</li>
<li>Transition Out Date</li></td>
  </tr>
</tbody>
</table>
