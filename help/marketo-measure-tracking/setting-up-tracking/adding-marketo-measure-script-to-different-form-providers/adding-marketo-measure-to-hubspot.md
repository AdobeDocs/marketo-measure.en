---
unique-page-id: 18874759
description: Adding Marketo Measure to Hubspot - Marketo Measure - Product Documentation
title: Adding Marketo Measure to Hubspot
exl-id: 633e7ef7-7959-461e-881f-dcc543595b66
---
# Adding Marketo Measure to Hubspot {#adding-marketo-measure-to-hubspot}

Learn how to add the Marketo Measure JavaScript to track your Hubspot landing pages and form submissions.

Hubspot is a bit different from other marketing automation systems in that it can host your landing pages / forms AND your website. It's important to note that the below instructions are for having Marketo Measure track activity on Hubspot-hosted pages. If you power your website with a CMS other than Hubspot (e.g. Wordpress), you will need to add the Marketo Measure JavaScript to that CMS as well.

>[!NOTE]
>
>If you are deploying the JavaScript through a tag management provider such as Google Tag Manager, you do not need to manually hard code the Marketo Measure JavaScript into your website.

## Getting Started {#getting-started}

Once you have logged into your Hubspot account, follow these steps.

1. Navigate to Content.

1. Click **Content Settings**.

1. Within Content Settings, click on the Site Header HTML (see image below).

1. Add the following script within your `<header>`:

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

   It should look like this:

```text
<!-- Marketo Measure Javascript -->
<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="">

```

>[!TIP]
>
>There may already be other tracking code snippets in this area, such as a Google Analytics code. Be sure to separate them by a semicolon `;` and a single space, like so:  
>
>`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="someothercode" src="someotherfile.js" ></script>`
