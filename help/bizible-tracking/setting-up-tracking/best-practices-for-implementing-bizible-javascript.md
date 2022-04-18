---
description: Best Practices for Implementing Marketo Measure JavaScript - Measure - Product Documentation
title: Best Practices for Implementing Marketo Measure JavaScript
exl-id: 0359ad27-81e8-4902-a23a-49a5646a44d0
---
# Best Practices for Implementing Marketo Measure JavaScript {#best-practices-for-implementing-marketo-measure-javascript}

## Overview {#overview}

The Bizible JavaScript tracks your web visitors digital marketing interactions and is key to Bizible’s ability to create online Touchpoint data. Having the Bizible JavaScript deployed correctly and comprehensively across your entire site(s) will ensure that the session data collected produces accurate touchpoint data.

Inconsistencies in the deployment of the Bizible JavaScript will cause breaks in the session data which can result in the following:

* Incorrect channel/subchannel attribution
* Loss of source data
* High levels of erroneous Direct traffic
* Inconsistent reporting

Bizible JavaScript is a foundational piece of your Bizible account and key to your success!

## Best Practice {#best-practice}

When it comes to implementing and managing your Bizible JavaScript, keep the following best practices in mind.

* Confirm all your domains are listed in your Bizible account
  * If you have concerns regarding your domains please contact Support
* Deploy JavaScript across ALL pages.
  * Placing JavaScript on only certain pages will cause breaks in your session data which will cause incorrect Bizible data
* For a form on your site that you do not want to create touchpoints from, make sure to add the Bizible Exclude Script
  * This exclusions script will ensure that the Bizible session data will not be disrupted and that the source data remains in place
    * Examples of common forms to suppress are:
      * Customer Logins
      * Forgot Password forms
      * Unsubscribe forms
      * Career application forms
* Review the “Additional Considerations” and “Forms to Pay Extra Attention To” sections of the Adding Bizible Script resource listed below to check for any scenarios that might need special handling

## Best Practice for Maintenance {#best-practice-for-maintenance}

While the setup of the Bizible JavaScript is covered during initial implementation, changes to your site or the team that manages it can result in disruptions in Bizible’s tracking. We recommend that you confirm the Bizible JavaScript is deployed correctly and comprehensively once a year. In addition, if your organization has any type of change protocol documentation for the website, ensure that there is a portion explaining that Bizible JavaScript should be retained/added to all new pages.

Other reasons to that might trigger a review your JavaScript setup include...

* Turnover in your marketing team
* Changes and updates to your site structure
* Site migrations
* Changes to your domain
* Acquistion's of other companies and their web properties

>[!MORELIKETHIS]
>
>* [Adding Bizible JavaScript](/help/bizible-tracking/setting-up-tracking/adding-bizible-script.md)
>* [Adding Bizible Script via GTM](/help/bizible-tracking/setting-up-tracking/adding-bizible-script-via-google-tag-manager.md)
>* [Adding Bizible JS to Pardot](/help/bizible-tracking/setting-up-tracking/adding-bizible-script-to-different-form-providers/adding-bizible-javascript-to-pardot.md)
>* [Adding Bizible JS to Lightbox Forms](/help/bizible-tracking/setting-up-tracking/adding-bizible-script-to-different-form-providers/adding-bizible-script-to-lightbox-forms.md)
>* [Adding Bizible JS to Sitecore Pages](/help/bizible-tracking/setting-up-tracking/adding-bizible-script-to-different-form-providers/adding-bizible-script-to-sitecore-pages.md)
>* [Adding Bizible JS to Uberflip Forms](/help/bizible-tracking/setting-up-tracking/adding-bizible-script-to-different-form-providers/adding-bizible-script-to-uberflip-forms.md)
>* [Adding Bizible JS to Act-On Forms](/help/bizible-tracking/setting-up-tracking/adding-bizible-script-to-different-form-providers/adding-bizible-to-act-on-forms.md)
>* [Adding Bizible to Hubspot](/help/bizible-tracking/setting-up-tracking/adding-bizible-script-to-different-form-providers/adding-bizible-to-hubspot.md)
>* [Adding Bizible to Marketing Landing Pages](/help/bizible-tracking/setting-up-tracking/adding-bizible-script-to-different-form-providers/adding-bizible-to-marketo-landing-pages.md)
>* [AJAX Form Handling](/help/bizible-tracking/setting-up-tracking/adding-bizible-script-to-different-form-providers/ajax-form-handling.md)
>* [Connecting Bizible to Unbounce Script Manager](/help/bizible-tracking/setting-up-tracking/adding-bizible-script-to-different-form-providers/connecting-bizible-to-unbounce-script-manager.md)
>* [IFrame Forms and Bizible](/help/bizible-tracking/setting-up-tracking/adding-bizible-script-to-different-form-providers/iframe-forms-and-bizible.md)
>* [Excluding Bizible Script from Specific Forms](/help/bizible-tracking/setting-up-tracking/excluding-bizible-from-specific-forms.md)
