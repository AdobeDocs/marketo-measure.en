---
unique-page-id: 18874590
description: Marketo Measure Cookies - Marketo Measure - Product Documentation
title: Marketo Measure Cookies
exl-id: de6e35ae-af92-43ba-8416-3e07d3dd470c
---
# Marketo Measure Cookies {#marketo-measure-cookies}

Learn about the various [!DNL Marketo Measure] Cookies that are loaded onto your site when you apply the [!DNL Marketo] Measure JavaScript to your landing pages. This information may serve as useful for the web development team during implementation.

| **Cookie Name** | **Cookie Type** | **Purpose** |
|---|---|---|
| _BUID | Third party, saved on .bizible.com domain | Universal user id to identity the same user across multiple clients' domains. |
| _biz_uid | First party | User id on the current domain. |
| _biz_sid | First party | Session id of the user. |
| _biz_flagsA | First party | A single cookie that stores multiple information, such as whether or not the user has submitted a form, performed a crossdomain migration, sent a viewthrough pixel, opted out from tracking, etc. |
| _biz_nA | First party | Sequence number that [!DNL Marketo Measure] includes for all requests, for internal diagnostics purpose |
| _biz_dfsA | First party | Temporarily stores form submission data that happens before [!DNL bizible].js receives a configuration JS to determine whether or not tracking form on HTTPS is enabled. |
| _biz_pendingA | First party | Temporarily stores analytics data that has not been successfully sent to Marketo Measure server yet. |

If a Web Application Firewall (WAF) warning is triggered during the JavaScript setup, users can either disable that WAF rule or allow-list the cookies, as the below example:

![](assets/marketo-measure-cookies-1.png)
