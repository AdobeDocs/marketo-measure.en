---
unique-page-id: 18874560
description: Why You Should Never Delete Touchpoints - [!DNL Marketo Measure] - Product Documentation
title: Why You Should Never Delete Touchpoints
exl-id: e74c14ff-0399-4ee9-b732-6686823ff5c7
---
# Why You Should Never Delete Touchpoints {#why-you-should-never-delete-touchpoints}

If you find that there is a touchpoint on an Opportunity that is being assigned attribution credit incorrectly, please reach out to your Account Manager to determine next steps. In these situations, we recommend using Buyer's touchpoint suppression feature to remove the touchpoint from SFDC and the ROI dashboard. Your account manager can help create these rules. Please do not manually delete these touchpoints yourself.

The [!DNL Marketo Measure] processing system will not register that a touchpoint has been manually deleted from SFDC. As of today, there is no trigger that signals to our system to adjust data. [!DNL Marketo Measure] will not automatically push another touchpoint to replace the one that was deleted, nor will it reassign the touchpoint position or attribution to the subsequent touchpoint.

When a touchpoint is deleted, it creates a hole in the attribution data. Typically, this will manifest in the attribution touchpoints on an Opportunity. In the image below, the touchpoint that would have received the Opportunity Creation touch had been deleted. As a result, this opportunity is missing the OC touchpoint and the attribution percentage for this Opp will not add up to 100%.

![](assets/1.png)

If touchpoints have been deleted from your SFDC, please reach out to [[!DNL Marketo Support]](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} to request a reimport of your data.
