---
description: Explanation of Touchpoint Positions and Generation Across BTs and BATs - Bizible - Product Documentation
title: Explanation of Touchpoint Positions and Generation Across BTs and BATs
exl-id: 4903f917-a366-4767-a126-5216d2377399
---
# Explanation of Touchpoint Positions and Generation Across BTs and BATs {#explanation-of-touchpoint-positions-and-generation-across-bts-and-bats}

**Generation of Touchpoint Positions & Flow Through the Buyers Journey**

Understanding the Bizible Touchpoint positions and how they are triggered is crucial to successfully reporting with Bizible data. You will want to have a clear understanding of what your prospects did as they moved through the buyer's journey and in turn what that will look like in the Touchpoint data. For more context on this topic, we recommend reviewing the [Touchpoint Generation & Mapping](/help/configuration-and-setup/getting-started-with-marketo-measure/touchpoint-generation-and-mapping.md) article.

Bizible has a variety of Touchpoint position that are triggered by various steps in the buyer’s journey. When reporting on Bizible data there are two sets of Touchpoint data, Bizible Touchpoints (BTs) and Bizible Attribution Touchpoints (BATs). You may notice that these sets of data have slightly different positions as they relate to different objects. For more context on this topic, we recommend reviewing the [Difference Between Bizible Touchpoints (BTs) & Bizible Attribution Touchpoints (BATs)](/help/configuration-and-setup/getting-started-with-marketo-measure/difference-between-marketo-measure-touchpoints-and-marketo-measure-attribution-touchpoints.md) article.

**Bizible Touchpoints (BTs)**: These are the touchpoints associated to an individual person and their journey and will be unique to that individual. The following out of the box reports are built off Bizible Touchpoint data.

* Bizible 101: Leads By ID
* Bizible 101: Leads By Channel
* Bizible 101: Lead/Contact By ID
* Bizible 101: Lead/Contact By Channel

The following outlines the Bizible Touchpoint positions which describes where an individual is in their journey and what actions, they took to earn that position.

<table> 
 <tbody>
  <tr>
   <th>Bizible Touchpoint (BTs) Position</th> 
   <th>Touchpoint Type (action that can trigger touchpoint)</th> 
   <th>Description of Touchpoint</th> 
  </tr>
  <tr>
   <td>First Touch (FT)</td> 
   <td>Web Visit</td> 
   <td>The very first marketing interaction an individual has with your brand</td> 
  </tr>
  <tr>
   <td>Lead Creation (LC)</td> 
   <td>Form Fill <strong>OR</strong> Campaign/Program Inclusion</td> 
   <td>The very first form fill an individual has (typically a form submission but could also be a Campaign/Program inclusion)</td> 
  </tr>
  <tr>
   <td>Post LC</td> 
   <td>Form Fill <strong>OR</strong> Campaign/Program Inclusion</td> 
   <td>Any form an individual completes after their LC (or an subsequent Campaign/Program inclusion)</td> 
  </tr>
 </tbody>
</table>

**Bizible Attribution Touchpoints (BATS)**: These are the touchpoints that are associated to an Opportunity and its journey. These touchpoints will be connected to revenue as they are connected to the Opportunity and its Contacts. The following out of the box reports are built off Bizible Attribution Touchpoint data.

* Bizible 101: Opportunities By ID
* Bizible 101: Opportunities By ID Channel

<table> 
 <tbody>
  <tr>
   <th>Bizible Attribution Touchpoint (BATs) Position</th> 
   <th>Touchpoint Type (action that can trigger touchpoint)</th> 
   <th>Description of Touchpoint</th> 
  </tr>
  <tr>
   <td>First Touch (FT)</td> 
   <td>Web Visit</td> 
   <td>The very first marketing interaction a contact had with your brand</td> 
  </tr>
  <tr>
   <td>Lead Creation (LC)</td> 
   <td>Form Fill <strong>OR</strong> Campaign/Program Inclusion</td> 
   <td>The very first form fill a contact had (typically a form submission but could also be a Campaign/Program inclusion)</td> 
  </tr>
  <tr>
   <td>Opportunity Creation</td> 
   <td>Form Fill <strong>OR</strong> Web Visit <strong>OR</strong> Campaign/Program Inclusion</td> 
   <td>The marketing interaction closest to when the Opp is Created</td> 
  </tr> 
  <tr>
   <td>Closed Won/Lost</td> 
   <td>Form Fill <strong>OR</strong> Web Visit <strong>OR</strong> Campaign/Program Inclusion</td> 
   <td>The marketing interaction closest to when the Opp is Closed (Won or Lost)</td> 
  </tr>
  <tr>
   <td>Middle Touches</td> 
   <td>Form Fill <strong>OR</strong> Campaign/Program Inclusion</td> 
   <td>When a contact fills out an online form and it doesn’t coincide with milestone touchpoint</td> 
  </tr>
 </tbody>
</table>

Bizible has these two sets of Touchpoint data to create a clear understanding of an individual person's journey as well as the Opportunities. These two Touchpoint data sets give you a clear map of what happened from top of funnel to bottom of funnel.

The following example shows the flow of data from Bizible Touchpoints (BTs) to Bizible Attribution Touchpoints (BATs). In this example Person A and Person B are both a part of the same Opportunity which has a Created Date of 3/7/2020 and a Close Date of 5/6/2020.

**Person A** Bizible Touchpoint Data Set

* First Touch (FT) – Paid Search.AdWords – 9/1/2019
* Lead Creation (LC) – Organic Search.Google – 11/20/2019
* Post LC (form fill) - Webinar – 3/4/2020

**Person B** Bizible Touchpoint Data Set

* First Touch (FT) – Paid Social.Facebook – 8/26/2019
* Lead Creation (LC) – Organic Search.Yahoo – 2/20/2020
* Post LC (form fill) - Email – 5/1/2020

**Opportunities** Bizible Attribution Touchpoint data would read as follows…

* First Touch (FT) – Paid Social.Facebook – 8/26/2019
  * (from **Person B** because they have the true _First Touch_ for the Account/Opp)
* Lead Creation (LC) – Organic Search.Google – 11/20/2019
  * (from **Person A** because they have the true _Lead Creation_ for the Account/Opp)
* Opportunity Creation (OC) - Webinar – 3/4/2020
  * (the Post LC touchpoint from **Person A** would be the _OC Touchpoint_ because it was the most recent interaction we have to the Opportunity being created on 3/7/2020)
* Closed Won - Email – 5/1/2020
  * (the Post LC touchpoint from **Person B** would be the _Closed Won Touchpoint_ because it was the most recent interaction we have to the Opportunity being closed on 5/6/2020)
