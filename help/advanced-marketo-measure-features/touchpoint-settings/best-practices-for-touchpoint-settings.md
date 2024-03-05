---
description: Best Practices for Touchpoint Settings - [!DNL Marketo Measure]
title: Best Practices for Touchpoint Settings
exl-id: 01e314a6-e33d-45cd-aaa3-c212afec07d1
feature: Touchpoints
---
# Best Practices for Touchpoint Settings {#best-practices-for-touchpoint-settings}

## Overview {#overview}

The [!UICONTROL Touchpoint Settings] section of your [!DNL Marketo Measure] app allows you to set rules that will suppress or remove touchpoints from your [!DNL Marketo Measure] data and related systems. These rules can help you to isolate certain sets of data that do not need to be represented in your Buyer touchpoint data or that you don't want to receive attribution credit without disturbing your tracking and data collection.

**Touchpoint Removal** means [!DNL Marketo Measure] will purge (i.e. remove) any Touchpoints from your CRM that fit the rule criteria. The data can be reported on within the [!DNL Marketo Measure] ROI Dashboard (Discover), but not appear in the CRM. Commonly used to alleviate stress on your data storage limits within your CRM

**Touchpoint Suppression** is similar to Touchpoint Removal, but the data CANNOT be reported on within the ROI Dashboard. Any touchpoints that are suppressed will not be accessible in the CRM or Discover. Suppression will ensure that your CRM data and your Discover data will match. Commonly used to fine tune and further specify which touchpoint data you want to receive attribution credit.

In your [!DNL Marketo Measure] app, the [!UICONTROL Touchpoint Settings] section will be broken out into four key sections. Each section suppresses or removes a different set of data. Use the key below to ensure your rules are suppressing or removing the desired touchpoints.

* Remove Buyer Touchpoints from CRM
   * Use this section when you want to create a rule that will remove **Buyer Touchpoint data** (the touchpoints that are associated to the individual, not the opportunity) from your **CRM**
* Suppress Buyer Touchpoints from CRM
   * Use this section when you want to create a rule that will remove **Buyer Touchpoint data** (the touchpoints that are associated to the individual, not the opportunity) from your **CRM** and **Discover**
* Remove Buyer Attribution Touchpoints from CRM
   * Use this section when you want to create a rule that will remove **Buyer Attribution Touchpoint** data (the touchpoints that are associated to the opportunity and revenue) from your **CRM**
* Suppress Buyer Attribution Touchpoints from CRM
   * Use this section when you want to create a rule that will remove **Buyer Attribution Touchpoint** data (the touchpoints that are associated to the opportunity and revenue) from your **CRM** and **Discover**

## Best Practice {#best-practice}

Whether you are establishing Touchpoint Setting rules for the first time or just reviewing them to check for accuracy, keep the following best practices in mind.

* Establish the list of data you want to suppress or remove prior to creating the rules
* Identify exactly what fields will clearly denote the rule or rules you are setting up
* Make sure you have specified the correct operator for the rule
* Utilizing the key above, make sure your rule is specified in the correct section of the Touchpoint Settings
* Test your rules before implementing them by replicating the rule logic in a Buyer touchpoint report in CRM to ensure it is suppressing or removing the desired data

## Best Practice for Maintenance {#best-practice-for-maintenance}

Reviewing your [!UICONTROL Touchpoint Settings] is important as they can drastically change your data when not defined appropriately. As a best practice, we recommend you review your Touchpoint Settings at least twice a year. This is a simple visual review of the rules set up in the Touchpoint Settings section of your [!DNL Marketo Measure] app. This review will allow you to feel confident that your Touchpoint Settings are up to date and that any changes can be made accordingly.

Reasons to review your [!UICONTROL Touchpoint] Settings include...

* Turnover in your marketing team
* Major updates to your website structure
* Identification of touchpoint data that is no longer useful
   * Any time you come across touchpoint data that you feel shouldn't receive attribution credit, [!DNL touchpoint suppression] rules are the functionality to ensure your data as clean and accurate as possible.
* Changes to the fields that are used to define your suppression or removal rules

>[!MORELIKETHIS]
>
>* [Touchpoint Removal and Suppression Overview](/help/advanced-marketo-measure-features/touchpoint-settings/touchpoint-removal-and-touchpoint-suppression.md)
>* [Why Touchpoints Should Never be Deleted](/help/advanced-marketo-measure-features/touchpoint-settings/why-you-should-never-delete-touchpoints.md)
>* [Buyer Touchpoints (BT) vs Buyer Attribution Touchpoints (BAT)](/help/configuration-and-setup/getting-started-with-marketo-measure/difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints.md)

