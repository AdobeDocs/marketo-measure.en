---
unique-page-id: 18874757
description: Adding Marketo Measure JavaScript to Pardot - Marketo Measure - Product Documentation
title: Adding Marketo Measure JavaScript to Pardot
exl-id: e49190ad-aa86-4f8f-a9ed-48de9e937a7e
---
# Adding Marketo Measure JavaScript to Pardot {#adding-marketo-measure-javascript-to-pardot}

Pardot forms require additional handling within the form template beyond putting script on the site in order for Marketo Measure to recognize form submissions. The process is simple; it only requires placing the Marketo Measure tracking script into the Pardot form template.

## Step by Step Instructions {#step-by-step-instructions}

Once you've logged into your Pardot account, follow the steps below.

1. Navigate to **Marketing**.

1. Click on **Landing Pages**.

1. Select **Layout Template**.

   ![](assets/1-3.png)

1. Determine the appropriate Layout Template and click **Edit** to the right.

   ![](assets/2-1.png)

1. Copy and paste the Marketo Measure JavaScript code right before the close header tag on your HTML page.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Follow these steps for all applicable Landing Page Layout Templates.

1. Make sure the Marketo Measure JavaScript is on the general site page as well.

   Within the Pardot Layout Template, the code will look something like this:

```text
<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>
   </head>
   <body>
```

## Additional Notes {#additional-notes}

If the Pardot IFrame has the following HTML tag:

`<base href="http://go.pardot.com">`

**And** the IFrame itself is actually on a secure page (HTTPS) instead of a nonsecure page (HTTP), when we try to load our script on the Pardot IFrame, the browser will try to load an HTTP version of our script on an HTTPS page which will fail and prevent us from tracking. The solution is to update the script on the Pardot IFrame to load the secure version of our script:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

As well, there may already be other tracking code snippets in this area, such as a Google Analytics code. Be sure to separate them by a semicolon `;` and a single space, like shown in this example:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="othercode_example" src="otherfile_example.js" ></script>`
