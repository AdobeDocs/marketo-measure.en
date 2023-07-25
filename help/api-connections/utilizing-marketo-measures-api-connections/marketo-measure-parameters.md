---
unique-page-id: 18874608
description: "[!DNL Marketo Measure] Parameters - [!DNL Marketo Measure] - Product Documentation"
title: "[!DNL Marketo Measure] Parameters"
exl-id: d66b9864-0d7e-455a-ae20-cca555f4d8c8
---
# [!DNL Marketo Measure] Parameters {#marketo-measure-parameters}

## [!DNL Marketo Measure] Parameters Explained {#marketo-measure-parameters-explained}

To gain further insight from the use of UTMs, [!DNL Marketo Measure] appends custom parameters to your ads in [!DNL Google] AdWords, Bing Ads and [!DNL Facebook] Ads. [!DNL Marketo Measure] integrates with these platforms to automate most of the setup process. If you select to use auto-tagging, [!DNL Marketo Measure] will automatically append its parameters to the URLs of your ads. [!DNL Marketo Measure] will also automatically download your marketing costs from the platforms and load them into the [!DNL Marketo Measure] app.

Example of a URL without parameters:

`http://adobe.com/landing-page?myParam=foo`

Example of a URL with [!DNL Marketo Measure] parameters:

`http://adobe.com/landing-page?myParam=foo&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## AdWords Parameters {#adwords-parameters}

* `_bk={keyword}`
   * Represents the keyword the person used in the search engine.
   * It is similar to the UTM term parameter.

* `_bt={creative}`
   * Represents the creative ID or name.
   * It is similar to the UTM content parameter.

* `_bm={matchtype}`
   * Represents how closely the keyword was matched.
   * Keyword match types help control which searches trigger your ad. For example, you could use broad match to show your ad to a wide audience or you could use exact match to hone in on specific groups of customers.
   * The three match types are: broad, fuzzy and exact.

>[!TIP]
>
>For more information on match types, [here's a relevant AdWords article](https://support.google.com/adwords/answer/2497836?hl=en){target="_blank"}.

* `_bn={network}`
   * Represents the ad network type - [display or search](https://support.google.com/adwords/answer/1752334?hl=en){target="_blank"}.
   * This is similar to the UTM Source parameter.

* `_bg={adgroupID}`
   * Represents the ID of the Ad Group the ad belongs to

>[!NOTE]
>
>We do not support Redirect URL parameters.

## Bing Ads Parameters {#bing-ads-parameters}

* `_bt={adid}`
* `utm_medium=cpc`
* `utm_source=bing`
* `utm_term={keyword}`

## Facebook Parameters {#facebook-parameters}

* `_bf ={creative}`
   * This represents the creative ID or name
