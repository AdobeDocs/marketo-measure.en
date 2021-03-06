---
unique-page-id: 18874678
description: Understanding Marketo Measure AdWords Tagging - Marketo Measure - Product Documentation
title: Understanding Marketo Measure AdWords Tagging
exl-id: c6658766-d3a8-46ed-b2d2-826eb61ce269
---
# Understanding Marketo Measure AdWords Tagging {#understanding-marketo-measure-adwords-tagging}

In order to track your ads at a very granular level, the Ad Destination URLs must be unique. To accomplish this, Marketo Measure's autotagging automatically adds tracking parameters to the Ad Destination URLs of your AdWords ads. Let's take a look at an example below.
  
The following URL will not provide any granular data:

* `http://example.com/landing-page?myParam=foo`

However, the same URL will provide granular data because of the Marketo Measure parameters:

* `http://example.com/landing-page?myParam=foo&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## How Marketo Measure's Auto-tagging Works {#how-marketo-measures-auto-tagging-works}

**If Marketo Measure finds a Tracking Template:**

* Marketo Measure will add its parameters to the Tracking Template.
* If a third-party redirect is found in a Tracking Template such as Kenshoo or Marin, Marketo Measure will take no action. Instead, you must [add Marketo Measure parameters to the third-party tool in your account](/help/api-connections/utilizing-marketo-measures-api-connections/how-bid-management-tools-affect-marketo-measure.md){target="_blank"}.

However, if no Tracking Template is found, Marketo Measure will:

* Scan all Ad Destination URLs for our Marketo Measure Parameters.
* If found, you're good to go.
* If not found, Marketo Measure will append its parameters to the end of the Ad Destination URLs. For new ads, Marketo Measure will append its parameters to the Ad Destination URL within two hours of creation.
* It is important to have a tracking template in place before enabling auto-tagging so that Marketo Measure can attach to it and prevent an ad history reset.

Marketo Measure recommends using an Account-Level, Campaign-Level, or Ad Group-Level Tracking template, as it allows for the addition and subtraction of parameters for all ads without the risk of Ad History interruptions or deletion.

## Tracking Templates {#tracking-templates}

As explained by Google AdWords, a tracking template is the URL that is used to reach a landing page. The tracking information collected is used to understand your ad traffic. [Click here](https://support.google.com/adwords/answer/7197008?hl=en){target="_blank"} for more information from Google.

Marketo Measure recommends using an Account Level, Campaign Level, or Ad Group Level Tracking template, as it allows for the addition and subtraction of parameters for all ads without the risk of Ad History interruptions or deletion.

There are two tracking templates Marketo Measure recommends using. Please use the following to determine which version is appropriate for you:

* If all of your ad URLs have a ??????? in them, use this URL:

`{lpurl}&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

* If none of your ad URLs have a ??????? in them, use this URL:

`{lpurl}?_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## Setting up a Tracking Template at the Account Level {#setting-up-a-tracking-template-at-the-account-level}

1. Log-in to your Google AdWords Account.

1. Click **All campaigns** and then **Settings** in the expanding window.

   ![](assets/1.png)

1. Click **Account Settings** at the top and then **Tracking Template**. Enter the Marketo Measure Tracking Template.

   ![](assets/2-1.png)

1. Click **Save**.

## Setting up a Tracking Template at the Campaign Level {#setting-up-a-tracking-template-at-the-campaign-level}

1. Click **All campaigns** and then **Campaigns** in the expanding window.

   ![](assets/3.png)

1. Select all applicable campaigns or **Select All**, click **Edit**, and then click **Change Tracking Templates**.

   ![](assets/4-1.png)

1. Enter the Marketo Measure Tracking Template and click **Apply**.

## Setting up a Tracking Template at the Ad Group Level: {#setting-up-a-tracking-template-at-the-ad-group-level}

1. Click **All campaigns** and then **Ad Groups** in the expanding window.

   ![](assets/5-1.png)

1. Select all applicable Ad Groups or Select All, click **Edit** and then click **Change Tracking Templates**.

1. Enter the Marketo Measure Tracking Template and click **Apply**.

   ![](assets/6-1.png)

## FAQ {#faq}

**Q: What permissions does the connected user need?**

A: userinfo.email

**Q: How long can it take to import spend data?**

A: 6 hours

**Q: How long can it take to import ad data?**

A: 4 hours

>[!NOTE]
>
>Once the changes are made, you are done. Feel free to reach out to [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} if there are any questions during setup.

[Click here](https://support.google.com/adwords/answer/6076199?hl=en#tracking){target="_blank"} for instructions from Google on creating Account-Level Tracking Templates.
