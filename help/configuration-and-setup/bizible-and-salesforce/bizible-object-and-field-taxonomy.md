---
unique-page-id: 18874584
description: Marketo Measure Object and Field Taxonomy - Measure - Product Documentation
title: Marketo Measure Object and Field Taxonomy
exl-id: 67f1cac8-e2b4-45cc-b1c9-58bf4e1a760d
---
# Marketo Measure Object and Field Taxonomy {#marketo-measure-object-and-field-taxonomy}

Below is a flow chart that represents how Bizible's Custom Objects relate to Salesforce Standard Objects.

![](assets/1-2.png)

For the full-sized image, [click here](assets/bizible-object-and-field-taxonomy-graph-full.png).  
  
Definitions of the Bizible fields that live in each object [can be found here](/help/introduction-to-bizible/overview-resources/glossary-of-bizible-fields.md).

## FAQ {#faq}

**What is the logic in the arrows?**

Each arrow describes the relationship between an object and the other. For example, you'll see that the Bizible Person populates fields on the standard Salesforce Lead Object. If it's pointing to it, then it means that it's populating the receiving end of the arrow.

**What is the Bizible Person?**

It's a Custom Bizible Object in Salesforce that links Bizible Touchpoints to Leads and Contacts.

**What is the Bizible.JS?**

It's our custom JavaScript that we utilize to track web information that a person has on a specific site.

**What is the Marketing ROI Dashboard?**

It's a custom marketing channels dashboard that lives in the Bizible app. It can be accessed by going to your Bizible tab in Salesforce.
