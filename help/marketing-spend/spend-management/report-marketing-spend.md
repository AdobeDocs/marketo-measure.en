---
unique-page-id: 27656737
description: Report Marketing Spend - [!DNL Marketo Measure]
title: Report Marketing Spend
exl-id: 46b0f81c-acd1-47a5-bf75-6a943edb9009
feature: Reporting, Spend Management
---
# Report Marketing Spend {#report-marketing-spend}

## Marketing Spend Table {#marketing-spend-table}

The Marketing Spend table contains a new column to display the currency for each Channel, Subchannel, and Campaign row. This new column displays for all customers, even if they don't have Multiple Currencies enabled.

The table contains a mix of different currencies. Refer to the Marketing Spend dashboard to get a sum of any Channels, Subchannels, or Campaigns in a single currency.

## Upload Costs {#upload-costs}

When a user downloads the cost file, the file will also contain a new column with the currency for each row. The only acceptable currencies are those that have been set and stored in the CRM. You need to know the 3-letter abbreviated code for your currency (USD, CAD, JPY, EUR) and if a file is uploaded with an unrecognized currency, the file upload fails.

## Costs from Ad Integrations {#costs-from-ad-integrations}

When [!DNL Marketo Measure] imports the cost from connected platforms such as AdWords, Bing, Facebook, or Doubleclick, we also use the reported currency. The currency displays alongside the Channel, Subchannel, and Campaign when displayed in the Marketing Spend table.

If the currency from the Ad Provider doesn't match a currency that is pulled from the CRM, you may see a "Mixed Currencies" error in [!DNL Marketo Measure Discover]. To fix this, the CRM Admin must add a conversion for the unknown currency.

## Migrate to Converted Marketing Spend {#migrate-to-converted-marketing-spend}

Because the marketing spend has historically only been in a single (USD) currency, there is a small amount of work needed to change all reported spends to the new currency. Even if your account doesn't have Multiple Currencies enabled, if you have a single corporate currency other than USD, you should make this migration.

1. Download the current Spend file to a CSV
1. The currency column displays "[!UICONTROL USD]" as the assumed currency. You can either manually replace all the occurrences of "[!UICONTROL USD]" or use Find+Replace to change all the "[!UICONTROL USD]" instances to your own corporate currency, such as "[!UICONTROL EUR]" or "[!UICONTROL GBP]".
1. Save the file then upload it back into [!DNL Marketo Measure].
1. All of your reported costs will now display as the new currency.
