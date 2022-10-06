---
description: Marketo Measure Integrations with Adobe Launch - Marketo Measure - Product Documentation
title: Marketo Measure Integrations with Adobe Launch
hide: yes
hidefromtoc: yes
---
# Marketo Measure Integrations with Adobe Launch {#marketo-measure-integrations-with-adobe-launch}

The Adobe Launch extension is designed for existing Marketo Measure tenants that already leverages Adobe Launch on their website. The extension is basically a tag management solution that marketers can use to configure and dynamically load scripts on their pages based on certain events and condition.

When installed and configured in Adobe Launch, Marketo Measure extension will load bizible.js script on the pages where Adobe Launch script is present. This allows marketers to add bizible.js through Adobe Launch configuration, as opposed to explicitly modifying the web page to add bizible.js script tag.

## Configure the Adobe Launch Extension {#configure-the-adobe-launch-extension}

>[!PREREQUISITES]
>
>Check out the following links to learn more about Adobe Launch and its extensions.
>
>* [Marketo Measure Extension](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email/bizible.html?lang=en#catalog){target="_blank"}
>* link
>* link

Adobe Launch Overview: https://experienceleague.adobe.com/docs/launch-learn/implementing-in-websites-with-launch/index.html?lang=en#prerequisites

Adobe Launch Extension overview: https://experienceleague.adobe.com/docs/launch/using/extension-dev/overview.html?lang=en#extension-configuration

1. Navigate to the Adobe Launch interface and create a property [following these steps](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html?lang=en#go-to-the-data-collection-interface){target="_blank"}. 

1. Install the Marketo Measure Extension.

PICC
 
1. When installing the extension, there's an "account id" field that needs to be configured.

PICC
 
The value of this field is not the "account id" in the Business_Prod.Business table. It's actually the website that's registered to the Business (i.e., honeywell.com).

The extension will append the value from this field as an optional parameter when loading bizible.js:

PICC
 
Think of this parameter as a "Current Page Override." Normally Marketo Measure Tracking app service will look at the "Current Page" field to determine which Marketo Measure tenants the web activities map to. However, if the "Current Page Override" value is present, we'll use that override value to dor the tenant lookup instead.

Example use case: a Marketo Measure tenant "Tenant1" registered domain "Website1.com" - this tells Marketo Measure that to map all web activities from "Website1.com" to "Tenant1"

"Tenant1" configured bizible.js to be loaded via the extension, where "Website1.com" is specified in the configuration

"Tenant1" also has a different domain "Website2.com", which hasn't been registered in Marketo Measure yet. "Website2.com" also uses the same Adobe Launch to load bizible.js

Since the same Adobe Launch tag is loaded from "Website2.com", the extension will load bizible.js with "Website1.com" as the "Current Page Override"

Because the override is present, Marketo Measure is able to map the traffics from "Website2.com" to "Tenant1", even though "Website2.com" hasn't been explicitly registered as "Tenant1"s domain in the Marketo Measure configuration

1. Once we install the extension, we'll also need to configure Adobe Launch rule to load the extension

PICC

Select the event where the rule is supposed to be triggered: "Core Library Loaded (Page Top)" will ensure that this rule is triggered when once the Launch library is loaded

Since we want the extension to load bizible.js every time Launch is loaded, there's no need to specify the "condition" constraint

Installing the extension will add "Marketo Measure Analytics - Initialize" in the selectable actions fields. Add this to the rule's action

To summarize, this rule will execute "Marketo Measure Analytics - Initialize" action when the event "Core Library Loaded (Page Top)" is triggered all the time

In other words, the rule will "load bizible.js with the specified Current page override configuration every time Launch is loaded"

1. Publish the rule in Launch to the selected environment.

PICC
 
Ensure that both of the Adobe Extension installation and its rule are selected to be published - we can click "add all changed resources" to populate all changes, which should include these 2

Once this is published, the site that has Launch tag installed should load the Adobe Extension as configured
