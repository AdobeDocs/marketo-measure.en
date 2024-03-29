---
unique-page-id: 18874562
description: PostLC Touchpoints and Lead Engagement - Marketo Measure - Product Documentation
title: PostLC Touchpoints and Lead Engagement
exl-id: 3ee5c571-195e-46c7-b150-fedcbc3614cb
feature: Touchpoints
---
# PostLC Touchpoints and Lead Engagement {#postlc-touchpoints-and-lead-engagement}

[!DNL Marketo Measure] Post-Lead Creation (PostLC) touchpoints are available for customers using multi-touch attribution models (W-Shape and above). When a Lead or Contact returns to your website and continues to fill out forms, these form submissions register as PostLC touchpoints. These touchpoints allow you to see what content is driving Leads to continue to engage with your site, long after their first conversion. PostLC touchpoints share attribution credit with all the intermediary touchpoints within an Opportunity; 10% attribution credit is allotted to intermediary touchpoints, and is distributed equally among all touches.

![](assets/1.png)

You can adjust the number of PostLC touchpoints that are displayed in [!DNL SFDC]. Typically we recommend pushing up to five PostLC touchpoints; each touchpoint takes up 1 KB in [!DNL SFDC].

>[!NOTE]
>
>Instructions for how to adjust PostLC touchpoint settings can be found at the end of this article.

PostLC touchpoints are dynamic. As a Lead or Contact continues to submit PostLC forms, [!DNL Marketo Measure] updates the PostLC touchpoints in your CRM to show you their most recent form submissions. Specifically, if you've set a limit of 5 PostLC touchpoints, [!DNL Marketo Measure] always push the five _most recent_ touchpoints to your CRM.  In this example, this account has set their PostLC limit to four touchpoints. This Lead has already reached maximum number of PostLC touchpoints that it can have in your CRM. The last PostLC touch was on 2/6/2018. If this person were to fill out another form the following day, [!DNL Marketo Measure] will remove the first PostLC touchpoint from 11/9/2017 to add the latest touchpoint from 2/7/2018.

![](assets/2.png)

>[!NOTE]
>
>[!DNL Marketo Measure] only updates PostLC touchpoints on the Lead or Contact, and does not update PostLC attribution touchpoints on an Opportunity. All relevant PostLC touchpoints on a Contact are included in the Opportunity.

## How to Change PostLC Touchpoint Settings {#how-to-change-postlc-touchpoint-settings}

To adjust the PostLC touchpoint settings for your Leads or Contacts, follow the instructions below.

**Leads**

1. Log in to your [!DNL Marketo Measure] account at [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} and go to [!UICONTROL Settings].

1. Under CRM, Select **[!UICONTROL Leads]**.

1. Input the number of postLC touchpoints you'd like to push to your Leads and click **[!UICONTROL Save]**.

   ![](assets/3.png)

**Contacts**

1. Log in to your [!DNL Marketo Measure] account at [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} and go to [!UICONTROL Settings].

1. Under CRM, Select **[!UICONTROL Contacts]**.

1. Input the number of postLC touchpoints you'd like to push to your Contacts and click **[!UICONTROL Save]**.

   ![](assets/4.png)
