---
unique-page-id: 18874747
description: Adding Marketo Measure Script to Sitecore Pages - Marketo Measure - Product Documentation
title: Adding Marketo Measure Script to Sitecore Pages
exl-id: 87ce1857-7532-45a7-8c39-255c6118b50a
---
# Adding Marketo Measure Script to Sitecore Pages {#adding-marketo-measure-script-to-sitecore-pages}

Content management systems can require additional steps beyond standard script implementation for Marketo Measure to recognize form submissions. The process below outlines how to add the Marketo Measure javascript to your Sitecore pages.

For sites with Sitecore pages:

1. Log-in Sitecore and navigate to your website. Locate the Configuration folder that resides on the same level as your Home item and Metadata folder.
1. Click the **+** next to the Configuration folder.
1. Click the **+** next to the Tools folder.
1. Select the Javascript item.
1. In the Content tab, click the **Lock and Edit** link to unlock the item for editing.
1. Find the ‘JavaScript’ section. If it is not already expanded, click the **+**.
1. Enter our script: `<script type=“text/javascript” src=“https://cdn.bizible.com/scripts/bizible.js”async=“”></script>`
1. Click **Save** in the upper left corner.
