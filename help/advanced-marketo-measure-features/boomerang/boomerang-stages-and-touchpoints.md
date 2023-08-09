---
unique-page-id: 18874558
description: Boomerang Stages and Touchpoints - [!DNL Marketo Measure] - Product Documentation
title: Boomerang Stages and Touchpoints
exl-id: e58169a3-3637-4878-8a0e-1920d873ff52
feature: "Boomerang, Touchpoints"
---
# Boomerang Stages and Touchpoints {#boomerang-stages-and-touchpoints}

>[!AVAILABILITY]
>
>The Boomerang feature is only enabled for Tier 3 customers. To request a higher account tier, please contact the Adobe Account Team (your account manager).

[!DNL Marketo Measure] has released our Boomerang Stage feature! The Boomerang Stage feature was created to provide greater visibility into the customer's journey for [!DNL Marketo Measure] customers with long sales cycles. This feature allows marketers to create touchpoints for all stage transitions that occur in the Opportunity journey, like when a contact MQLs, then moves to SAL, and then reverts back to the MQL stage. When contacts "re-enter the MQL stage" or "re-MQL's", we consider the MQL to be a boomerang stage. The Boomerang Stage feature functions alongside the [!DNL Marketo Measure] Custom Stages.

## What This Feature Does {#what-this-feature-does}

* Creates a "boomerang" touchpoint for all stage transitions that occur in an opportunity's journey
* Tracks repeat transitions between any custom stage (ex. when a Contact MQLs, moves to SAL, and then goes back to the MQL stage)
* Allows you to specify how many and which set of stage transitions you would like included in the Opportunity (ex. The first 10 MQLs OR the last 5 MQLs)
* If you are a Custom Model user, you are able to determine the attribution weighting and percentage credit you'd like to allocate to each of these stages (ex. designate attribution weight to the first or last MQL occurrence, or distribute attribution weighting evenly amongst all occurrences)

>[!NOTE]
>
>[Instructions on how to set up Boomerang Stages](/help/advanced-marketo-measure-features/boomerang/setting-up-boomerang-stages.md).

## What Boomerang Stages and Touchpoints Look like in Your CRM {#what-boomerang-stages-and-touchpoints-look-like-in-your-crm}

Without Boomerang stages (the "before"), you will only see the most recent MQL or most recent SQL touchpoint associated to a Lead/Contact record.

![](assets/1.png)

With Boomerang Stages and touchpoints, you will see touchpoints that occur for each stage transition. The naming convention for these boomerang touchpoints will be as follows:

**[Stage Name]-00.**

Using the example below, this [!DNL Marketo Measure] account has included MQL and SQL in their boomerang stages, and have chosen to display 2 boomerang touchpoints per stage.

![](assets/2.png)

**MQL-01** is the first MQL stage transition.

The numerical value in the touchpoint position will denote the order in which the stage transition occurred. The last boomerang touchpoint be stamped as:

MQL-02 **(Last)**

## How Boomerang Stages Change Your Existing Data {#how-boomerang-stages-change-your-existing-data}

Boomerang Stages will impact:

**Attribution by channel**

* Since [!DNL Boomerang Stages] will create more touchpoints, this will change how attribution is distributed among the touchpoints that currently exist in your data. As a result, this may mean that revenue values will shift between marketing channels. Please take this into consideration before implementing [!DNL Boomerang stages], or contact your account manager for more information.

**Any reports that use "equals [Touchpoint Position]"**

* Boomerang stages will introduce new touchpoint positions to your data. [!DNL Marketo Measure] is changing the format of the Touchpoint Position to include the occurrence of the stage, like "MQL-01" or "MQL-05 (Last)." Using this example, Boomerang Stages will impact any reports that are using "Touchpoint Position is equal to MQL." To adjust these reports the filter should be using the "contains" operator instead.

## FAQ {#faq}

**How many boomerang stages can I include in my attribution model?**

You can select up to 15 stages.

**Q: How many "boomerang" touchpoints can I have per stage?**

You can select up to 10 boomerang touchpoints per stage.

**Q: Why are we only limited to 10 boomerangs per stage?**

[!DNL Marketo Measure] has to place a limit on the number of stages in order to keep processing times under control. If you choose to include all 15 Boomerang Stages in your attribution model, and 10 boomerang touchpoints per stage, you could potentially have over 150 touchpoints per Lead/Contact record.

**Q: I have Data Warehouse. Do I get all of the data or does the Boomerang Stages cap apply to me as well?**

The cap will apply to Data Warehouse and CRMs because of the processing limits that [!DNL Marketo Measure] has in place. Data Warehouse will also see the limit of 10 touchpoints per stage.

**Q: What is the benefit of using Boomerang Stages with Custom Modeling?**

Using [!UICONTROL Boomerang] Stages with Custom Modelling will allow you to assign attribution weighting to [!UICONTROL Boomerang] touchpoints, which will allocate revenue credit to these stages.

Without custom modeling, [!DNL Marketo Measure] will create touchpoints for each boomerang and stage transition but will not assign any attribution credit to these touchpoints. The only boomerang touchpoints that will receive attribution credits are form submission touchpoints. Without custom model, [!DNL Boomerang] touchpoints are considered the same as a 'middle touch' and receive attribution credit accordingly.
