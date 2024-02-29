---
unique-page-id: 27656441
description: Drift Integration FAQ - [!DNL Marketo Measure]
title: Drift Integration FAQ
exl-id: ae5706b1-1f6c-4201-8585-0d7c587746e1
feature: Integration
---
# Drift Integration FAQ {#drift-integration-faq}

As a part of the [!DNL Marketo Measure] integration with Drift, her are some of the most frequently asked questions. If there are any questions not outlined below, reach out to the Adobe Account Team (your Account Manager) or [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

**How is the integration enabled?**

Drift Chat tracking for [!DNL Marketo Measure] is enabled by default. If you want to disable it (and not create Touchpoints from Drift Chats by default), add an additional attribute added to your [!DNL Marketo Measure] Javascript implementation, bolded below:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" id="bizible-settings" data-chatEnabled="false"></script>`

For those using [!DNL Google Tag Manager] to load the [!DNL Marketo Measure] Script, if you want to exclude your Drift Chats from being Touchpoint-eligible, add to following `<span>` right after your [!DNL Marketo Measure] Script:

`<span id="bizible-settings" data-chatEnabled="false"></span>`

**What does the integration do?**

The integration now allows [!DNL Marketo Measure] to track when an end user provides their email address in a Drift chat. From there we create touchpoints from these interactions with a Touchpoint Type of "Web Chat." This integration allows marketers to understand the performance of their chat interactions, along with the channels/subchannels/campaigns that drive people to interact with these chats.

**What if I track Drift via campaign sync rules?**

If there are any campaign sync rules in place to create touchpoints for Drift chat interactions, ensure you stop adding those particular end users into the corresponding CRM Campaign. Otherwise once the feature bit is enabled, create a CRM Campaign touchpoint and digital touchpoint for one Drift chat interaction.

**What if I track Drift via CRM Campaigns?**

If there are CRM campaigns in place to create touchpoints for Drift chat interactions, a Touchpoint End Date must be set on those specific campaigns (the Touchpoint End Date should be the date the Web Chat Integration feature bit is enabled).

**What if I track Drift via Activities?**

If there are activity rules in place to create touchpoints for Drift chat interactions, an additional piece of logic must be added to the rules. Add logic using the Task Created Date field to prevent duplication of touchpoints from being created (IE CrmTask.CreatedDate is Less Than the date in which the feature bit was enabled). See screenshot below for example.

![](assets/activity-rule-drift.png)
