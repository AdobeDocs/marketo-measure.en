---
description: "Data Collected by JavaScript guidance for Marketo Measure users"
title: Data Collected by JavaScript
feature: Tracking
exl-id: 83814168-9d3e-45ac-b514-df58f0b2e90b
hidefromtoc: yes
---
# Data Collected by JavaScript {#data-collected-by-javascript}

Learn about the data collected by Marketo Measure JavaScript upon deployment.

**Sample request:**

```text
https://cdn.bizible.com/m/ipv?_biz_r=https%3A%2F%2Fwww.google.com%2F&_biz_h=-1801745101&_biz_u=7059e81415f34f7bbaf40fe32fdcba21&_biz_s=8cbeed&_biz_l=https%3A%2F%2Fwww.zendesk.com%2Fservice%2F&_biz_t=1676483822155&_biz_i=Customer%20service%20software%20for%20the%20best%20customer%20experiences%20%7C%20Zendesk&_biz_n=0&rnd=235938&cdn_o=a&_biz_z=1676483822155
```

<br>

Marketo Measure collects the following common data for all types of requests:

| Origin | Name | Data Type | Purpose |
| --- | --- | --- | --- |
| Request header | IP address | string | The location of the user is inferred through GeoIP lookup. This data is temporary and not stored permanently. |
| Request header | User-agent string | string | Determines what device the user is using. |
| Query parameter | `_biz_u` | string | Bizible cookie ID. |
| Query parameter | `_biz_l` | string | Current page URL. |
| Query parameter | `_biz_t` | long | Activity timestamp. |
| Query parameter | `_biz_i` | string | Current page title. |

In addition to the common data above, bizible.js also appends additional data depending on the request types as specified below:

| Request Type | Request Path | Additional Query Parameter | Data Type | Purpose |
| --- | --- | --- | --- | --- |
| Pageview | `/ipv` | `_biz_r` | string | Referrer page URL. |
|  |  | `_biz_h` | string | Hashed client's screen resolution. |
|  |  | `_biz_c` | string | Optional parameter. If this parameter is present, it indicates that tenant configures `bizible.js` to wait for user's consent before tracking, and that `bizible.js` has received the user's consent to be tracked. |
| Form submits | `/frm` | `eMail` | string | Plain text email address. |
| User id mapping | `/u` | `mapType` | enum | What kind of user id mapping `bizible.js` detected (Marketo Munchkin id and Adobe ECID) |
|  |  | `mapValue` | string | The actual third party cookie id value of the above integration. |

>[!NOTE]
>
>Bizible is the former name of Marketo Measure.
