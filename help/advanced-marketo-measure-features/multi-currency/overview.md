---
unique-page-id: 27656735
description: Overview - [!DNL Marketo Measure] - Product Documentation
title: Overview
exl-id: 2076521c-b579-457c-ab1c-263b1da4dd89
feature: Multi-Currency
---
# Overview {#overview}

Today, the [!DNL Marketo Measure] application only supports a single currency (assumed to be USD), whereas we know and are aware that we have customers around the world who need to report on their own corporate and user currencies. This feature enables users to switch between the same currencies used in their CRM when viewing reported spend or sales revenue in [!DNL Marketo Measure].

## Availability {#availability}

Tier 2 and higher.

## Requirements {#requirements}

[!DNL Marketo Measure] will automatically pull the currency setting from the customer's CRM. Manual configuration in [!DNL Marketo Measure] to match the CRM is no longer required. The currency setting can be found in the "General" page under "CRM".

In [!DNL Salesforce], the customer must have "Activate Multiple Currencies" enabled. Optionally, the customer can also select "Yes, I want to enable Advanced Currency Management."

In Dynamics, the customer can set static exchange rates in their Settings for multiple currencies. There is no concept of "advanced currency management" in Dynamics.

## Terms {#terms}

| **Term** |Description |
|---|---|
| **Advanced Currency** |The customer has Advanced Currency Management and Multiple Currencies enabled, which means they can have different conversion rates for different time periods. |
| **Corporate Currency** |These are the various currencies that are listed and declared by an organization in the CRM, all with conversion rates. [!DNL Marketo Measure] will import these values and make these currencies available to users within our product. |
| **Currency Locale** |The single currency that is used for an organization, set on the Company Information page. |
| **Local Currency (or User Currency)** |The currency set for a single user on the User Profile, so that they can view any amount in their own local currency. The organization will have had to declare and set up the currency before a user can select their local currency. |
| **Single Currency** |Used for customers that do not use Multiple Currencies in the CRM, but their organization runs in a different currency, so they have a "Currency Locale." This is still a single currency for the organization but without any conversion. |
| **Simple Currency** |The customer has Multiple Currencies enabled, but they have a static conversion rate per currency. |
