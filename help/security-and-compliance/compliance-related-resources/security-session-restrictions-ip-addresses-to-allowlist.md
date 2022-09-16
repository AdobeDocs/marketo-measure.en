---
unique-page-id: 18874706
description: Security Session Restrictions - IP Addresses to Allowlist - Marketo Measure - Product Documentation
title: Security Session Restrictions - IP Addresses to Allowlist
exl-id: aaf5190f-893c-4872-8d03-93f516e70a59
---
# Security Session Restrictions: IP Addresses to Allowlist {#security-session-restrictions-ip-addresses-to-allowlist}

If there are [Session Security Settings](https://help.salesforce.com/articleView?id=admin_sessions.htm&type=0) in place preventing specific IP Addresses from pushing/pulling data to your [!DNL Salesforce] instance, we will need the following IPs allowlisted to allow [!DNL Marketo Measure] to push data to [!DNL Salesforce]:

23.100.229.112 - 23.100.229.127
23.100.234.220
23.101.160.122
23.101.165.12
23.101.171.23
52.162.84.192 - 52.162.84.207
65.52.17.21
157.55.161.105

To add [!DNL Marketo Measure] IPs to the Trusted IP Ranges in Salesforce, click **[!UICONTROL Setup]** > **[!UICONTROL Administration Setup]** > **[!UICONTROL Security Controls]** > **[!UICONTROL Network Access]** > **[!UICONTROL New]**.

![](assets/1.png)
