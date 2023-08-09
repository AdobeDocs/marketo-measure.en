---
unique-page-id: 18874730
description: Account Based Marketing Overview - [!DNL Marketo Measure] - Product Documentation
title: Account Based Marketing Overview
exl-id: 2ead69c0-66da-439d-a0ba-25c73c4b308c
feature: "Account-based Marketing"
---
# Account Based Marketing Overview {#account-based-marketing-overview}

Below is a brief overview of ABM, the components of the [!DNL Marketo Measure] ABM feature, and how to add it to your [!DNL Salesforce] page layout. To read more about ABM, check out [this page](https://www.marketo.com/account-based-marketing/){target="_blank"}.

To navigate directly to the instructions for setting up ABM within your [!DNL Salesforce] instance, please [click here](/help/advanced-marketo-measure-features/account-based-marketing/account-based-marketing-overview.md#setting-up-abm-page-layout-in-salesforce){target="_blank"}.

## What is ABM {#what-is-abm}

Account based marketing, ABM, is a marketing strategy in which you target and sell to companies and accounts as a whole, not just as individuals. [!DNL Marketo Measure] helps Marketing and Sales teams execute successful ABM strategies with its lead-to-account mapping functionality and Predictive Engagement Score.

In order for our Account Based Marketing model to begin to populate in your CRM, [!DNL Marketo Measure] needs the following criteria to be met:

* Your CRM needs at least 25 Accounts that have at least one Closed Won Opportunity on them, so we can better gauge the commonalities of a "successful" Account/Opportunity to your business.
* The other side of the coin, your CRM needs at least 25 Accounts without any Closed Won Opportunities (all opps must either be in our "Open" stage category, or in a "Closed Lost" category - this helps us gauge what makes a lower grade Account in your organization.

>[!NOTE]
>
>The above "bad" accounts need to be open for at least 12 months without accumulating a Closed Won opp; that's our basic guideline for whether or not an Opp has gone stale for the model's purposes.

## Lead-to-Account Mapping {#lead-to-account-mapping}

Lead-to-account mapping is a crucial part of an effective ABM approach. With lead-to-account mapping, prospects, or leads, are grouped into the same company account as they engage with your brand. This allows you to target and sell to individuals from the same company in a consistent manner. There is no additional [!DNL Salesforce] configuration needed in order to begin benefitting from this feature. The [!DNL Marketo Measure] Lead to Account Mapping five different matching methods:

* Lead Website to Account Website
* Lead Email Domain to Account Website Domain
* Lead Company Name to Account Name
* Lead Company to Account Website Domain
* Matching the Domain on the Lead's Email Address to the Account via the Contact's Email Address

>[!NOTE]
>
>Each Lead is attempted to be matched to an Account in the preferential order of methods above. Once a match is made, the AccountId is immediately set on the Lead and won't be matched using another method. If the Lead already has a valid AccountId, the Lead is skipped.

## Predictive Engagement Score {#predictive-engagement-score}

The [!DNL Marketo Measure] Predictive Engagement Score, or PES, is a dynamic value that illustrates how engaged a particular account is with your marketing efforts. This score is helpful for segmenting accounts to target. It is a valuable tool for identifying accounts to target more effectively and efficiently.

There are many components that go into the algorithm that calculates the PES. Recency and age has a large influence on score changes, along with last touchpoint activity or page views. Adding new contacts to an account also impacts PES. Below is a list of some PES inputs:

* Total number of page views from the account
* Average number of page views
* Average number of persons in the account
* Age of last page view
* Average age of page views
* Number of persons in the account
* Specific important pages and if there has been a visit in the past 30/60/90 days
* If the account has a closed lost/won deal
* How likely it will be closed lost/won

>[!NOTE]
>
>You may notice a grade of "N/A" or "-" (the dash symbol) in your Predictive Engagement Score for some Accounts.

_A grade of "N/A" simply means that we do not have sufficient data yet on that account for our model to generate a true grade - with more data, a grade will be given eventually._
_A grade of "-" (the dash symbol) means that this account has yet to be processed by our ABM process, due to time constraints, occasionally missed processes, etc. If you believe an Account should have a grade, based on other similar accounts or timeframes, please reach out and let [!DNL Marketo Measure] know._

## Setting up ABM Page Layout in [!DNL Salesforce] {#setting-up-abm-page-layout-in-salesforce}

To begin using the PES, you simply need to add the PES field and Related List to the appropriate page layouts in [!DNL Salesforce].

1. Navigate to **[!UICONTROL Setup]** > **[!UICONTROL Customize]** > **[!UICONTROL Accounts]** > **[!UICONTROL Page Layout]**. Then select the page layout you'd like to edit.
1. Go to [!UICONTROL Fields] and move the field "Predictive Engagement Score" into your Account Information section.

   ![](assets/1.png)

1. Finally, go to [!UICONTROL Related Lists] and move the "Leads" Related List into your page layout.

   ![](assets/2.png)

1. Next, navigate to **[!UICONTROL Setup]** > **[!UICONTROL Customize]** > **[!UICONTROL Leads]** > **[!UICONTROL Page Layout]** and select the appropriate page layouts you would like to edit.
1. Click **[!UICONTROL Fields]** and add the [!UICONTROL Account] field where you see fit on the page.

   ![](assets/3.png)

You're all set!

