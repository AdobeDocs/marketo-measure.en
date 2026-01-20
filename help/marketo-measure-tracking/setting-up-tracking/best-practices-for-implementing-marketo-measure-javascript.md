---
description: Best Practices for Implementing [!DNL Marketo Measure] JavaScript - [!DNL Marketo Measure]
title: Best Practices for Implementing [!DNL Marketo Measure] JavaScript
exl-id: 0359ad27-81e8-4902-a23a-49a5646a44d0
feature: Tracking
---
# Best Practices for Implementing [!DNL Marketo Measure] JavaScript {#best-practices-for-implementing-marketo-measure-javascript}

## Overview {#overview}

The [!DNL Marketo Measure] JavaScript tracks your web visitors digital marketing interactions and is key to the [!DNL Marketo Measure] ability to create online Touchpoint data. Having the [!DNL Marketo Measure] JavaScript deployed correctly and comprehensively across your entire site(s) will ensure that the session data collected produces accurate touchpoint data.

Inconsistencies in the deployment of the [!DNL Marketo Measure] JavaScript will cause breaks in the session data which can result in the following:

* Incorrect channel/subchannel attribution
* Loss of source data
* High levels of erroneous Direct traffic
* Inconsistent reporting

[!DNL Marketo Measure] JavaScript is a foundational piece of your [!DNL Marketo Measure] account and key to your success!

## Best Practice {#best-practice}

When it comes to implementing and managing your [!DNL Marketo Measure] JavaScript, keep the following best practices in mind.

* Confirm all your domains are listed in your [!DNL Marketo Measure] account
   * If you have concerns regarding your domains contact Support
* Deploy JavaScript across ALL pages.
   * Placing JavaScript on only certain pages will cause breaks in your session data which will cause incorrect [!DNL Marketo Measure] data
* For a form on your site that you do not want to create touchpoints from, make sure to add the [!DNL Marketo Measure] Exclude Script
   * This exclusions script will ensure that the [!DNL Marketo Measure] session data will not be disrupted and that the source data remains in place
      * Examples of common forms to suppress are:
         * Customer Logins
         * Forgot Password forms
         * Unsubscribe forms
         * Career application forms
* Review the "Additional Considerations" and "Forms to Pay Extra Attention To" sections of the Adding [!DNL Marketo Measure] Script resource listed below to check for any scenarios that might need special handling

## Best Practice for Maintenance {#best-practice-for-maintenance}

While the setup of the [!DNL Marketo Measure] JavaScript is covered during initial implementation, changes to your site or the team that manages it can result in disruptions in [!DNL Marketo Measure] tracking. We recommend that you confirm the [!DNL Marketo Measure] JavaScript is deployed correctly and comprehensively once a year. In addition, if your organization has any type of change protocol documentation for the website, ensure that there is a portion explaining that [!DNL Marketo Measure] JavaScript should be retained/added to all new pages.

Other reasons to that might trigger a review your JavaScript setup include...

* Turnover in your marketing team
* Changes and updates to your site structure
* Site migrations
* Changes to your domain
* Acquistion's of other companies and their web properties
