---
unique-page-id: 18874710
description: Touchpoint Removal and Touchpoint Suppression - [!DNL Marketo Measure] - Product Documentation
title: Touchpoint Removal and Touchpoint Suppression
exl-id: 201af648-6525-4a80-a7e5-3cbeeb1670b6
feature: Touchpoints
---
# Touchpoint Removal and Touchpoint Suppression {#touchpoint-removal-and-touchpoint-suppression}

Learn how to remove or suppress Touchpoints that meet specific criteria from your CRM. This can be helpful for freeing up data space if you are having [!DNL Salesforce] data storage limits.
  
There is one key difference between Touchpoint Removal rules and Touchpoint Suppression rules:

* Touchpoint Removal - [!DNL Marketo Measure] will purge (ie remove) any Touchpoints from your CRM that fit the rule criteria. The data _can_ be reported on within the [!DNL Marketo Measure] ROI Dashboard, but no longer in the CRM.
* Touchpoint Suppression - Similar to Touchpoint Removal, but the data CANNOT be reported on within the ROI Dashboard.

Before getting started with creating Touchpoint removal/suppression rules, it's a good idea to share your implementation plan with your marketing and sales operations team. You should already have an idea as to which types or values you want removed. Some of the common use cases are:

* Delete Touchpoints from closed lost opportunities
* Delete Touchpoints from very old leads
* Delete Touchpoints from unqualified leads

Once the rules are saved, [!DNL Marketo Measure] will clean up and redistribute your attribution model. This means the milestones and positions will change, and your channel's attribution credit will change! This will modify your data, so contact your Success Manager if you need assistance.
  
`1)` There are two sections for removal/suppression settings. You have the option of setting it up for Buyer Touchpoints (Leads and Contacts) or Buyer Attribution Touchpoints (Contacts, Opportunities, and Accounts).  
  
Start with adding a rule and selecting the Field that will define your criteria.  
  
Choose from a list of Operators that will relate to the next set of values, which you'll add in the next column.
  
![](assets/1-1.png)

>[!TIP]
>
>To add multiple values in a field, use the "matches any" operator with commas separating each value.

>[!TIP]
>
>To account for a blank or NULL value in a field, simply leave the Value box empty. This will take into account scenarios such as evaluating against a Touchpoint with no Form URL.

>[!NOTE]
>
>Formula fields cannot be used within your rules and will not appear in the picklist. Because formulas calculate in the background and do not modify a record, [!DNL Marketo Measure] cannot detect whether a record fits a rule or not.

`2)` Add rules within the same group to utilize "AND" logic in your statement.
Or, add new statements outside of the group to utilize "OR" logic in your statement.
  
![](assets/2.png)
  
`3)` If your rules get complex and you need to recreate groups and make small changes to each statement, use the Clone option to make things simpler.
  
![](assets/3.png)
  
If you make a mistake, don't worry. You can delete individual rows of your statement or full groups, too.
  
![](assets/4.png)
  
`4)` Set up rules for the Buyer Attribution Touchpoints if you want them applied to both objects. Our flexibility allows you to set rules for one object or both objects and may choose to set them up for both if they apply.
  
![](assets/5.png)

To finish, Save and Process your rules. If you're making a lot of changes, be sure to Save your changes along the way. [!DNL Marketo Measure] won't actually start removing your Touchpoints until you click the **Save and Process** button.

| **Operator** |**Use Case** |
|---|---|
| Is Equal To |Single value - exact match |
| Contains |Single value - contains value |
| Matches Any |Multiple values - Exact Match |
| Matches Any (Contains) |Multiple values - &#42;value&#42;, &#42;value, &#42;value&#42; |

For customers using Dynamics who want to set up Suppression rules based off of Status and/or Statecode, we require the following formatting when setting up the rule: `[Object].Statecode` is equal/not equal to `[Status Value]`. For example, if the Statecode within Dynamics reads "1" on a Contact, and the Status reads "Inactive", and you wanted to suppress all such Contacts, the following format would be incorrect for your Suppression rule: Contact.Statecode is equal to 1. Instead, you'd want to use the following format - since Statecode and Status operate as a pair, [!DNL Marketo Measure] reads the value from Status in our querying: Contact.Statecode is equal to Inactive.
