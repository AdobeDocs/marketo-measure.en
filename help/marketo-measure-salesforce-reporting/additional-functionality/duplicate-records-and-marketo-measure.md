---
unique-page-id: 18874572
description: Duplicate Records and Marketo Measure - Marketo Measure - Product Documentation
title: Duplicate Records and Marketo Measure
exl-id: e340100c-120a-4771-946d-336a1458da4e
---
# Duplicate Records and Marketo Measure {#duplicate-records-and-marketo-measure}

Marketo Measure leverages the email address as our unique identifier when matching data to a related Lead or Contact in the CRM. When Marketo Measure finds multiple Leads or Contacts with the same email address, we will surface the same data on all records. The impact of this comes when you are reporting on the Leads or Contacts with Marketo Measure and can incorrectly inflate the amount of unique people who have Buyer Touchpoints.
  
What does this look like in Marketo Measure Reporting?

*Example report: Marketo Measure Persons with Buyer Touchpoints.*

![](assets/1-1.png)
  
You can see for the Marketo Measure Person ID of kelsey@adobe.com that there is both a Lead and Contact that exists with that email address. You will find that in this report, there are 2 First Touches reported, 2 Lead Creation Touches, and 2 PostLC interaction reported. These duplicate records share the same touchpoint date and touchpoint information which could lead to the conclusion that they are 2 different people despite being the same person.
  
**Recommendation**

* In order to maximize the return in your reports, we recommend leveraging a de-duping tool within your CRM to ensure that you are only creating net new, unique records. This can be done with your Marketing Automation tool or a separate software installed within your CRM. Marketo Measure does not dedupe records automatically and does not offer this service through our software.
* An alternative option would be to manually merge records as you identify duplicates. This process can be time consuming and tedious, but the output of accurate reporting is worth the time investment.
