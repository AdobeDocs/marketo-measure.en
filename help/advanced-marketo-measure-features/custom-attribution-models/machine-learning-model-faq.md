---
unique-page-id: 18874775
description: Machine Learning Model FAQ - Marketo Measure - Product Documentation
title: Machine Learning Model FAQ
exl-id: 2fc142b2-8ac4-4c48-a8f1-398e29ccfe97
---
# Machine Learning Model FAQ {#machine-learning-model-faq}

Marketo Measure's Machine Learning model uses your touchpoint data to calculate how much attribution weighting should be assigned to each stage. This is determined by how important each stage was in driving deals to close.

What do the attribution percentages from the Machine Learning Model tell me about each stage?

The attribution percentages of each stage reflects the potential impact of your marketing efforts. A higher percentage means that marketing can directly influence the movement of the funnel at that point. A lower attribution percentage means that stages are less important for your team to monitor.

How is the Machine Learning Model calculated?

Marketo Measure calculates the importance of each custom stage by using the touchpoint data from your account. The criteria used to determine the importance of each stage are:

* Model Accuracy: If we build a predictive model with the touchpoint data to predict whether we will win a deal eventually, how accurate will the model be? Higher predictive accuracy means that the details of this stage correlates more with whether a deal will close
* Conversion Rate: If Leads or Opportunities at this certain stage convert to the next stage at a high rate, this suggests that the marketing activities that occurred at this stage didn't matter very much. Conversely, if a certain stage converts to the next stage at a low rate, this can suggest that the marketing activities that occurred at this stage were influential in driving the conversion.
* Touchpoint Uniqueness Weight: If a stage occurs as a standalone transition, meaning there weren't any other stage transitions that occurred at the same time, this stage could receive a higher attribution weight. Conversely, if a touchpoint for a stage is shared with other stages (e.g. the touchpoint shares the First Touch, Lead Conversion, and Opportunity Conversion stages) this stage could receive a lower attribution weighting.

The final weight for a custom stage is calculated as such:

**_Model Percentage = Model Accuracy x Conversion Rate x Touchpoint Uniqueness Weight_**

At the end, all the custom stage weights are normalized and converted to % as shown below.

Why am I not seeing any numbers in the Machine Learning column?

When the Custom Attribution Model is enabled for your account, it generally takes between 3-7 days for our model to run and build these numbers, based off of your historical data.

How often is the Machine Learning Model updated?

We re-run the model every 7 days.

Why does the Model always set Middle Touches to 10%?

Assigning 10% attribution credit to [!UICONTROL Middle Touches] is a standard setting across all of our attribution models.

When should I change my attribution distribution?

Please reach out to your account manager to discuss the implications of changing your attribution percentages, and which stages to include in your custom model. Each [!DNL Salesforce] and sales process is unique, and we want to ensure that your custom model is accurately modeled.

That being said, we've identified some general trends across our customers:

One trend we've noticed is that it's not always beneficial to include more stages in your model. For example, when customers have added multiple Opportunity stages towards the bottom of the funnel, these stages tend to receive very low attribution percentage values. Low percentage values indicate a high conversion rate, which typically means that that these stages aren't as impactful at driving deals to close. Some customers ultimately decide to not include these stages in the funnel. If you decide to remove a stage from your attribution model, the machine model will recalculate and redistribute the percentages.

We've also noticed that there is a high conversion rate from Lead Creation to [!UICONTROL Marketing Qualified] stages, and consequently, the [!UICONTROL Marketing Qualified] stage could receive a lower percentage attribution weighting. Depending on your business and sales cycle, it may be beneficial to remove this stage from the custom model.

Please keep in mind if you'd like to track marketing activities through a specific stage transition but you do not want this stage to receive attribution credit, you can include this stage in your model and assign 0% attribution credit to that stage.
