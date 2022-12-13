---
unique-page-id: 18874720
description: How Bid Management Tools Affect [!DNL Marketo Measure] - [!DNL Marketo Measure] - Product Documentation
title: How Bid Management Tools Affect [!DNL Marketo Measure]
exl-id: 67c00ad9-8b12-4238-8a1f-2d2f5ed04423
---
# How Bid Management Tools Affect [!DNL Marketo Measure] {#how-bid-management-tools-affect-marketo-measure}

Learn how bid management platforms affect the [!DNL Marketo Measure] ability to track AdWords and BingAds, along with how to set up tracking templates with our parameters to ensure everything tracks correctly.

Kenshoo and Marin are great tools that allow marketers to track, manage and optimize their ad campaigns with different search engines. In order for [!DNL Marketo Measure] parameters to be appended to these ad URLs, you will need to set up a tracking template with our [!DNL Marketo Measure] parameters. It is not possible to connect your ad platforms to your [!DNL Marketo Measure] account and enable autotagging as it causes the [!DNL Marketo Measure] tagging system to compete with Kenshoo/Marin's tagging system. This results in our parameters to be altered and incorrectly appended. To circumvent this, tracking templates with [!DNL Marketo Measure] parameters need to be set up within Kenshoo and Marin.

## For [!DNL Adwords] Accounts {#for-adwords-accounts}

Setup a tracking template as follows:

* Click the **[!UICONTROL Campaigns]** tab.
* Click the **[!UICONTROL Shared library]** link in the side navigation bar.
* Click **URL options**.
* Next to "Tracking template," click **Edit**.
* Fill in the URL:

   * If ALL of your ad URLs have a "?" in them, use this URL:
      * `{lpurl}&_bk={keyword}&_bt={creative}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`
   * If NONE of your ad URLs have a "?" in them, use this URL:
      * `{lpurl}?_bk={keyword}&_bt={creative}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`


## For [!DNL Bing Ads] Accounts {#for-bing-ads-accounts}

Setup a tracking template as follows:

* Click the **[!UICONTROL Campaigns]** tab.
* Click the **[!UICONTROL Shared library]** link in the side navigation bar.
* Click **URL options**.
* Next to "Tracking template," click **Edit**.
* Fill in the URL:

   * If ALL of your ad URLs have a "?" in them, use this URL:
      * `{lpurl}&_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`
   * If NONE of your ad URLs have a "?" in them, use this URL:
      * `{lpurl}?_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`
