---
description: Data Collected by JavaScript - [!DNL Marketo Measure] - Product Documentation
title: Data Collected by JavaScript
feature: Tracking
---
# Data Collected by JavaScript {#data-collected-by-javascript}

Learn about the data collected by Marketo Measure JavaScript upon deployment.

**Sample request:**

```
https://cdn.bizible.com/m/ipv?_biz_r=https%3A%2F%2Fwww.google.com%2F&_biz_h=-1801745101&_biz_u=7059e81415f34f7bbaf40fe32fdcba21&_biz_s=8cbeed&_biz_l=https%3A%2F%2Fwww.zendesk.com%2Fservice%2F&_biz_t=1676483822155&_biz_i=Customer%20service%20software%20for%20the%20best%20customer%20experiences%20%7C%20Zendesk&_biz_n=0&rnd=235938&cdn_o=a&_biz_z=1676483822155
```

<br>

Marketo Measure collects the following common data for all types of requests:

<table>
<thead>
  <tr>
    <th>Origin</th>
    <th>Name</th>
    <th>Data Type</th>
    <th>Purpose</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Request header</td>
    <td>IP address</td>
    <td>string</td>
    <td>The location of the user is inferred through GeoIP lookup. This data is temporary and not stored permanently.</td>
  </tr>
  <tr>
    <td>Request header</td>
    <td>User-agent string</td>
    <td>string</td>
    <td>Determines what device the user is using.</td>
  </tr>
  <tr>
    <td>Query parameter</td>
    <td>_biz_u</td>
    <td>string</td>
    <td>Bizible cookie ID.</td>
  </tr>
  <tr>
    <td>Query parameter</td>
    <td>_biz_l</td>
    <td>string</td>
    <td>Current page URL.</td>
  </tr>
  <tr>
    <td>Query parameter</td>
    <td>_biz_t</td>
    <td>long</td>
    <td>Activity timestamp.</td>
  </tr>
  <tr>
    <td>Query parameter</td>
    <td>_biz_i</td>
    <td>string</td>
    <td>Current page title.</td>
  </tr>
</tbody>
</table>

In addition to the common data above, bizible.js also appends additional data depending on the request types as specified below:

<table>
<thead>
  <tr>
    <th>Request Type</th>
    <th>Request Path</th>
    <th>Additional Query Parameter</th>
    <th>Data Type</th>
    <th>Purpose</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Pageview</td>
    <td>/ipv</td>
    <td>_biz_r</td>
    <td>string</td>
    <td>Referrer page URL.</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>_biz_h</td>
    <td>string</td>
    <td>Hashed client's screen resolution.</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>_biz_c</td>
    <td>string</td>
    <td>Optional parameter. If this parameter is present, it indicates that tenant configures bizible.js to wait for user's consent before tracking, and that bizible.js has received the user's consent to be tracked.</td>
  </tr>
  <tr>
    <td>Form submits</td>
    <td>/frm</td>
    <td>eMail</td>
    <td>string</td>
    <td>Plain text email address.</td>
  </tr>
  <tr>
    <td>User id mapping</td>
    <td>/u</td>
    <td>mapType</td>
    <td>enum</td>
    <td>What kind of user id mapping bizible.js detected (Marketo Munchkin id and Adobe ECID)</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>mapValue</td>
    <td>string</td>
    <td>The actual third party cookie id value of the above integration.</td>
  </tr>
</tbody>
</table>

>[!NOTE]
>
>Bizible is the former name of Marketo Measure.
