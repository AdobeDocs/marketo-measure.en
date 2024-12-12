---
unique-page-id: 18874646
description: Difference Between Buyer Touchpoints and Buyer Attribution Touchpoints - [!DNL Marketo Measure]
title: Difference Between Buyer Touchpoints and Buyer Attribution Touchpoints
exl-id: 19109271-7b59-44c0-b1ff-e3b0bba9f5ce
feature: Touchpoints
---
# Difference Between Buyer Touchpoints and Buyer Attribution Touchpoints {#difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints}

Learn what defines a Buyer Touchpoint (BT) and Buyer Attribution Touchpoint (BAT), the differences between the two, and answer commonly asked questions.

The key distinguisher between Buyer Touchpoints and Buyer Attribution Touchpoints is their relationship with [!DNL Salesforce] Objects. BTs relate to the Lead, Contact, and Case Objects, but not the Opportunity object. Meaning there is never revenue associated to Buyer Touchpoints.

While the Buyer Attribution Touchpoint Object are related to the Contact, Account, and Opportunity Objects, but not the Lead Object; the  Buyer Attribution Touchpoints are not tied to Leads. The BAT Object is where you will see revenue tied to specific marketing interactions.

Difference between BT and BAT:

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <td>Buyer Touchpoint (BT)</td> 
   <td>Buyer Attribution Touchpoint (BAT)</td> 
  </tr> 
  <tr> 
   <td> 
    <ul> 
     <li>Relates to the Lead, Contact, and Case Objects</li> 
     <li>Does not relate to the Opportunity Object</li> 
     <li>Revenue is not associated to a Buyer Touchpoint</li> 
    </ul></td> 
   <td> 
    <ul> 
     <li>Relates to the Contact, Account, and Opportunity Objects</li> 
     <li>Does not relate to the Lead Object</li> 
     <li>Since a Buyer Attribution Touchpoint is associated to an Opportunity, all BATs have revenue associated to them</li> 
    </ul></td> 
  </tr> 
 </tbody> 
</table>

## FAQ {#faq}

**When does a Buyer Touchpoint become a Buyer Attribution Touchpoint?**

A BT becomes a BAT once this BT is associated to a Contact that has an associated Opportunity. One important thing to understand is that one specific marketing interaction can be a BT and BAT.

**Can a Buyer Touchpoint have a Touchpoint Position of Opportunity Creation (OC)?**

A Buyer Touchpoint will only have a Touchpoint Position of either First Touch (FT), Lead Creation (LC), or Form submission (intermediary touchpoints). Since BTs aren't related to Opportunities, it's not possible for a BT to have a Touchpoint Position of Opportunity Creation or Closed.

**How is Buyer Touchpoint data used?**

Typically customers use Buyer Touchpoint data to understand Top of the Funnel & Middle of the Funnel engagement. Meaning [!DNL Marketo Measure] users know who's submitting forms, who's viewing their site, what blog post is performing well, what AdWords ad is driving leads to converts, and so on. Buyer Touchpoint data is great for understanding the engagement of your Leads & Contacts.

**What does a Buyer Touchpoint look like in Salesforce?**

Here's a screenshot of a BT in [!DNL Salesforce]:

![](assets/buyer-touchpoints-and-buyer-attribution-touchpoints-1.png){width="600" zoomable="yes"}

**What does a Buyer Attribution Touchpoint look like in Salesforce?**

Here's a screenshot of a BAT in [!DNL Salesforce]:

![](assets/buyer-touchpoints-and-buyer-attribution-touchpoints-2.png){width="600" zoomable="yes"}
