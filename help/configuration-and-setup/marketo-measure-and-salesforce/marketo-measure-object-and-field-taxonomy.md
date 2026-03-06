---
unique-page-id: 18874584
description: "[!DNL Marketo Measure] Object and Field Taxonomy - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Object and Field Taxonomy"
exl-id: 67f1cac8-e2b4-45cc-b1c9-58bf4e1a760d
feature: Salesforce
---
# [!DNL Marketo Measure] Object and Field Taxonomy {#marketo-measure-object-and-field-taxonomy}

Below is a flow chart that represents how [!DNL Marketo Measure] Custom Objects relate to [!DNL Salesforce] Standard Objects.

![](assets/1-2.png)

For the full-sized image, [click here](assets/bizible-object-and-field-taxonomy-graph-full.png).

Definitions of the [!DNL Marketo Measure] fields that live in each object [can be found here](/help/introduction-to-marketo-measure/overview-resources/glossary-of-marketo-measure-fields.md).

## FAQ {#faq}

**What is the logic in the arrows?**

Each arrow describes the relationship between an object and the other. For example, you see that the [!DNL Marketo Measure] Person populates fields on the standard [!DNL Salesforce] Lead Object. If it's pointing to it, then it means that it's populating the receiving end of the arrow.

**What is the [!DNL Marketo Measure] Person?**

It's a Custom [!DNL Marketo Measure] Object in [!DNL Salesforce] that links Buyer Touchpoints to Leads and Contacts.

**What is the [!DNL Bizible].JS?**

It's our custom JavaScript that we utilize to track web information that a person has on a specific site.

**What is the Marketing ROI Dashboard?**

It's a custom marketing channels dashboard that lives in the [!DNL Marketo Measure] app. It can be accessed by going to your [!DNL Marketo Measure] tab in [!DNL Salesforce].
