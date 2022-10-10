---
unique-page-id: 18874572
description: Duplicate Records and [!DNL Marketo Measure] - [!DNL Marketo Measure] - Product Documentation
title: Duplicate Records and [!DNL Marketo Measure]
exl-id: e340100c-120a-4771-946d-336a1458da4e
---
# Duplicate Records and [!DNL Marketo Measure] {#duplicate-records-and-marketo-measure}

>[!NOTE]
>
>You may see instructions specifying "[!DNL Marketo Measure]" in our documentation, but still see "Bizible" in your CRM. We are working to have that updated and the rebranding will be reflected in your CRM soon.

[!DNL Marketo Measure] leverages the email address as our unique identifier when matching data to a related Lead or Contact in the CRM. When [!DNL Marketo Measure] finds multiple Leads or Contacts with the same email address, we will surface the same data on all records. The impact of this comes when you are reporting on the Leads or Contacts with [!DNL Marketo Measure] and can incorrectly inflate the amount of unique people who have Buyer Touchpoints.
  
What does this look like in [!DNL Marketo Measure] Reporting?

_Example report: [!DNL Marketo Measure] Persons with Buyer Touchpoints._

![](assets/1-1.png)
  
You can see for the [!DNL Marketo Measure] Person ID of kelsey@adobe.com that there is both a Lead and Contact that exists with that email address. You will find that in this report, there are 2 First Touches reported, 2 Lead Creation Touches, and 2 PostLC interaction reported. These duplicate records share the same touchpoint date and touchpoint information which could lead to the conclusion that they are 2 different people despite being the same person.
  
**Recommendation**

* In order to maximize the return in your reports, we recommend leveraging a de-duping tool within your CRM to ensure that you are only creating net new, unique records. This can be done with your Marketing Automation tool or a separate software installed within your CRM. [!DNL Marketo Measure] does not dedupe records automatically and does not offer this service through our software.
* An alternative option would be to manually merge records as you identify duplicates. This process can be time consuming and tedious, but the output of accurate reporting is worth the time investment.
