---
unique-page-id: 18874688
description: CRM Campaign Costs - [!DNL Marketo Measure] - Product Documentation
title: CRM Campaign Costs
exl-id: d967cabe-b9f1-4ea1-a81b-e4484c703ecf
---
# CRM Campaign Costs {#crm-campaign-costs}

Most [!DNL Marketo Measure] customers use CRM campaigns to track offline marketing activities. Marketers who utilize these campaigns will also monitor costs within the CRM, so this feature makes it easier on marketers by allowing [!DNL Marketo Measure] to read those costs and apply them to the reported Marketing Spend within [!DNL Marketo Measure]. To date, customers have had to manually enter costs for each campaign per month, but with the necessary information provided to us, [!DNL Marketo Measure] can automate this process so marketers can spend more time analyzing their spend and ROI.

## Availability {#availability}

This feature is available for all [!DNL Salesforce] and Dynamics customers.

## How It Works {#how-it-works}

[!DNL Marketo Measure] first looks for Campaigns that have been "enabled" for touchpoints, so there is either a matching Campaign Sync rule that was created, or the Enable Buyer Touchpoints value is "Include All Campaign Members" or "Include 'Responded' Campaign Members." In addition, [!DNL Marketo Measure] need to import the correct values and know how to distribute the costs, so we require that the following fields contain a value:

**[!DNL Salesforce]**: ActualCost, StartDate, EndDate

**[!DNL Microsoft Dynamics]**: totalactualcost, actualstart, actualend

If any of the 3 fields are missing a value, [!DNL Marketo Measure] will not import the costs. You can correct this by updating the Campaign record in the CRM. Also important to note that we will not import the costs if it is explicitly set to $0 because [!DNL Salesforce] treats blank and $0 as the same.

In order for [!DNL Marketo Measure] to determine the distribution of a campaign across months, we use the start and end date of the campaign and distribute the amount evenly per day.

![](assets/1.jpg)

So in this example, we have a campaign that lasts 109 days, so with a total cost of $18,000, the spend per day comes to ~$165.14.

Based on the number of days per month, we get these monthly totals, as you can see in the table:

Jul 2018: ($18,000/109) x 31 = $5,119.27

Aug 2018: ($18,000/109) x 31 = $5,119.27

Sep 2018: ($18,000/109) x 30 = $4,954.13

Oct 2018: ($18,000/109) x 17 = $2,807.34

## Historical Reported Spend {#historical-reported-spend}

Don't worry! If you've entered spend for Campaigns that we've tracked in the past that were mapped to a CRM Campaign, we will not override any of the costs you've entered. If the same campaign in the CRM gets modified, we will still ignore it and give priority to the changes you had previously made in the CSV upload.

If you would prefer that we take the CRM Campaign cost moving forward, what you can do is change the value in the CSV to $0 which will nullify the entry. Then, the next time that we run our jobs to import the costs, we will scan for any records that have previously been edited and will pull that in.

## Campaigns with No Touchpoints {#campaigns-with-no-touchpoints}

Many marketers choose to report marketing spend on CRM Campaigns that didn't happen to generate any touchpoints, or knowingly have no Campaign Members for the purposes for tracking spend. As long as the 3 fields are populated (start date, end date, cost) and the campaign is enabled for touchpoints, [!DNL Marketo Measure] will still pull that cost in regardless of whether or not there are touchpoints associated to it.

This could be helpful for tracking spend on excess Marketing costs or tools to roll that up into your ROI calculations.

## Marketo Program Sync {#marketo-program-sync}

If you bring in Marketo Programs into the CRM as Campaigns, you'll want to ensure you have the Start Date, End Date, and Period Cost mapping set up to the required CRM fields. Since there is no mapping to the Enable Buyer Touchpoints field, you will still need to enable these campaigns so that we know to pull the costs for them.

## Editing the Costs {#editing-the-costs}

Once a Campaign is imported from the CRM, it will be treated similar to an API Ads Provider and will not appear in the CSV to make any cost changes.

Any changes to the cost or distribution must be done in the CRM so that we can point to a single point of truth.

## FAQ {#faq}

**I've made a change to my campaign - when should I expect to see the changes in the Marketing Spend table or in my reporting?**

3-4 hours

**I have the start date, end date, and cost filled out but why are my costs are still not showing up in [!DNL Marketo Measure]?**

Please check that you either have the Enable Buyer Touchpoint value set to "Include All Campaign Members" or at least "Include 'Responded' Campaign Members, or that you have created a custom Campaign Sync rule that includes this Campaign. If you've confirmed this and still do not see the Campaign, please reach out to [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} so we can check that your Campaigns are importing properly.

**I need to change the distribution of my Campaign so that I can weight it heavier in certain months. How do I do that?**

The distribution of the costs is purely based on an even distribution from the start date to the end date. Unfortunately, we can't change it so that your costs have a different weighting aside from the dates set. You can control this by adjusting the start and end date of your campaign since each day in the month matters.

**I have costs set up on my Parent Campaign - how do the Children Campaigns get allocated the cost from the Parent Campaign?**

Actually, the way that costs will be pulled in will be directly from a single campaign, regardless of any Parent or Child relationship. We advise that the cost go on the Children Campaigns, along with the dates of the campaign, then use the Parent as the umbrella campaign where the Parent Campaign would not get enabled for touchpoints.

**How do I change the cost for a month in [!DNL Marketo Measure]?**

Because we rely on the CRM as the single source of truth, all changes need to be made in the CRM. Once the Campaign has been imported by [!DNL Marketo Measure], the Campaign values are not editable in [!DNL Marketo Measure] or in the CSV file.

**In what scenario would a Campaign appear in the Marketing Spend table, then no longer appear?**

We will continue to require that all three key fields have a value: Start Date, End Date, and Cost. Our default behavior is that we only import Campaigns with a value greater than $0. Ideally, we would import Campaigns where there is an explicit $0 and not import those that are left blank, but the Salesforce API imports them both as $0 regardless of the value. In addition, if the Enable Buyer Touchpoint value changes from "Include All" or "Include 'Responded'" to "Exclude All," we will remove the Campaign and the Cost from the Marketing Spend table.

**What cost would take priority if a row was already downloaded from the CRM and I entered another row in the CSV with the same campaign Id?**

Although you may be able to successfully upload the file, [!DNL Marketo Measure] will not use that row because we already have a campaign Id with the same value that was automatically pulled from the integration.

**How would you suggest we bring it costs from our Digital Campaigns that we set up in the CRM?**

Because our [!DNL Marketo Measure] javascript is already tracking web activity from your site, we would advise against syncing any campaigns that track Campaign Members from web forms or other site activities since it will double count the touches. Because of that, you may want to continue using the CSV Upload option in Marketing Spend to track those online/digital costs if we aren't already integrated with that platform (i.e. Twitter, Adroll).
