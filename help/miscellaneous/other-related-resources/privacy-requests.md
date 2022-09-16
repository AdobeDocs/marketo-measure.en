---
description: Privacy Requests - [!DNL Marketo Measure] - Product Documentation
title: Privacy Requests
exl-id: 883e475f-9868-412a-b505-230556f38484
---
# Privacy Requests {#privacy-requests}

This document provides an overview of managing individual data privacy requests that you can send to [!DNL Marketo Measure] through the [!DNL Privacy Service] UI and the **[!DNL Privacy Service] API**.

You can submit individual requests to access and delete consumer data from [!DNL Marketo Measure] in two ways:

* Through the [[!DNL Privacy Service] UI](https://experienceleague.adobe.com/docs/experience-platform/privacy/ui/overview.html){target="_blank"}.
* Through the **[!DNL Privacy Service] API**. See the documentation [here](https://experienceleague.adobe.com/docs/experience-platform/privacy/api/overview.html){target="_blank"} and the API reference [here](https://developer.adobe.com/experience-platform-apis/references/privacy-service/){target="_blank"}.

The [Privacy Service](https://experienceleague.adobe.com/docs/experience-platform/privacy/home.html){target="_blank"} supports two types of requests: data access and data deletion.

Let's see how you can create Access and Delete requests.

## Required setup to send requests for Marketo Measure {#required-setup-to-send-requests-for-marketo-measure}

To make requests to Access and Delete data for [!DNL Marketo Measure], you must:

1. Identify the following:

   a. IMS Org ID

   b. Email Address of the person you want to act on

   An IMS Org ID is a 24-character alphanumeric string appended with @AdobeOrg. If your marketing team or internal Adobe system administrator doesn't know your organization's IMS Org ID, contact Adobe Customer Care at gdprsupport@adobe.com. You need the IMS Org ID to submit requests to the Privacy API.

1. In [!DNL Privacy Service], you can submit Access and Delete requests to [!DNL Marketo Measure], and check the status of existing requests.

## Required field values in [!DNL Marketo Measure] JSON requests {#required-field-values-in-marketo-measure-json-requests}

"companyContexts":

* "namespace": **imsOrgID**
* "value": `<Your IMS Org ID Value>`

"users":

* "action": either [!UICONTROL access] or delete
* "userIDs":
   * "namespace": email
   * "type": standard
   * "value": `<Data Subject's Email Address>`

"include":

* **marketoMeasure** (which is the Adobe product that applies to the request)

"regulation":

* **gdpr**, **ccpa**, **pdpa**, **lgpd_bra**, or **nzpa_nzl** (which is the privacy regulation that applies to the request)

## Example One: GDPR Delete Request {#gdpr-delete-request}

JSON Request

```text
{
  "companyContexts": [
    {
      "namespace": "imsOrgID",
      "value": "1231659F56A68A8B7F000101@AdobeOrg"
    }
  ],
  "users": [
    {
      "action": [
        "delete"
      ],
      "userIDs": [
        {
          "namespace": "email",
          "type": "standard",
          "value": "john.doe@adobe.com"
        }
      ]
    }
  ],
  "include": [
    "marketoMeasure"
  ],
  "regulation": "gdpr",
}
```

JSON Response

```text
{
  "requestId": "16331241037112570RX-245",
  "totalRecords": 1,
  "jobs": [
    {
      "jobId": "997b01e3-9568-402c-904b-b4e60a437875",
      "customer": {
        "user": {
          "action": [
            "delete"
          ],
          "userIDs": [
            {
              "namespace": "email",
              "value": "john.doe@adobe.com",
              "type": "standard",
              "namespaceId": 6,
              "isDeletedClientSide": false
            }
          ]
        }
      }
    }
  ]
}
```

## Example Two: CCPA Access Request {#ccpa-access-request}

JSON Request

```text
{
  "companyContexts": [
    {
      "namespace": "imsOrgID",
      "value": "1231659F56A68A8B7F000101@AdobeOrg"
    }
  ],
  "users": [
    {
      "action": [
        "access"
      ],
      "userIDs": [
        {
          "namespace": "email",
          "type": "standard",
          "value": "john.doe@adobe.com"
        }
      ]
    }
  ],
  "include": [
    "marketoMeasure"
  ],
  "regulation": "ccpa",
}
```

JSON Response

```text
{
  "requestId": "16329573462631890RX-207",
  "totalRecords": 1,
  "jobs": [
    {
      "jobId": "3115e42d-011b-47ab-a2b0-ed4356af4d3e",
      "customer": {
        "user": {
          "action": [
            "access"
          ],
          "userIDs": [
            {
              "namespace": "email",
              "value": "john.doe@adobe.com",
              "type": "standard",
              "namespaceId": 6,
              "isDeletedClientSide": false
            }
          ]
        }
      }
    }
  ]
}
```
