---
unique-page-id: 18874590
description: "[!DNL Marketo Measure] Cookies - [!DNL Marketo Measure] - Product Documentation"
title: "[!DNL Marketo Measure] Cookies"
exl-id: de6e35ae-af92-43ba-8416-3e07d3dd470c
feature: Tracking
---
# Marketo Measure Cookies {#marketo-measure-cookies}

Learn about the various [!DNL Marketo Measure] Cookies that are loaded onto your site when you apply the [!DNL Marketo Measure] JavaScript to your landing pages. This information may serve as useful for the web development team during implementation.

<table>
<thead>
  <tr>
    <th>Cookie Name</th>
    <th>Cookie Type</th>
    <th>Purpose</th>
    <th>Expiry</th>
    <th>Has Secure Flag Set?<br></th>
    <th>Has HTTP Only Flag Set?</th>
    <th>Cookie Setter</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>_biz_uid</td>
    <td>First party</td>
    <td>Uniquely identify a user on the current domain.</td>
    <td>1 year</td>
    <td>No</td>
    <td>No</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_nA</td>
    <td>First party</td>
    <td>A sequence number that Marketo Measure includes for all requests for internal diagnostics purposes.</td>
    <td>1 year</td>
    <td>No</td>
    <td>No</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_flagsA</td>
    <td>First party</td>
    <td>A cookie that stores various user information, such as form submission, cross-domain migration, view-through pixel, tracking opt-out status, etc.</td>
    <td>1 year</td>
    <td>No</td>
    <td>No</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_pendingA</td>
    <td>First party</td>
    <td>Temporarily stores analytics data until successfully sent to Marketo Measure server.</td>
    <td>1 year</td>
    <td>No</td>
    <td>No</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_ABTestA</td>
    <td>First party</td>
    <td>List of checksums from Optimizely and Visual Web Optimizer ABTests data that have already been reported, preventing bizible.js from resending collected data.</td>
    <td>1 year</td>
    <td>No</td>
    <td>No</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_EventA</td>
    <td>First party</td>
    <td>List of checksums reported by Bizible Events to prevent bizible.js from resending collected data.</td>
    <td>1 year</td>
    <td>No</td>
    <td>No</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_su</td>
    <td>First party</td>
    <td>Universal user ID to identify a user across multiple domains, only applicable to tenants with integration bypassing ITP limitations.</td>
    <td>1 year</td>
    <td>Yes</td>
    <td>No</td>
    <td>Edgecast</td>
  </tr>
  <tr>
    <td>_BUID</td>
    <td>Third party, domain=.<a href="http://bizible.com/">bizible.com</a></td>
    <td>Universal user ID to identify a user across multiple domains.</td>
    <td>1 year</td>
    <td>Yes</td>
    <td>No</td>
    <td>Edgecast</td>
  </tr>
  <tr>
    <td>_BUID</td>
    <td>Third party, domain=.<a href="http://bizibly.com/">bizibly.com</a></td>
    <td>Mapping between Marketo Measure cookie ID on the tenant's domain and its Doubleclick impression cookie ID.</td>
    <td>1 year</td>
    <td>Yes</td>
    <td>No</td>
    <td>Edgecast</td>
  </tr>
</tbody>
</table>

If a Web Application Firewall (WAF) warning is triggered during the JavaScript setup, users can either disable that WAF rule or allow-list the cookies, as the below example:

![](assets/marketo-measure-cookies-1.png)
