---
unique-page-id: 18874652
description: "[!DNL Marketo Measure] View Through Attribution FAQ - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] View Through Attribution FAQ"
exl-id: d20e88f3-3ff8-4381-a4b8-6862798caa74
feature: Attribution
---
# [!DNL Marketo Measure] View Through Attribution FAQ {#marketo-measure-view-through-attribution-faq}

## What is View Through Attribution? {#what-is-view-through-attribution}

The [!DNL Marketo Measure] [!UICONTROL View Through Attribution] feature includes the ability to include ad impressions in the attribution model.

>[!IMPORTANT]
>
>Due to privacy concerns, third-party cookies are on the way out. Google Chrome's announced Q3 2024 deprecation of third-party cookies effectively marks the end of this form of tracking. As a result, Adobe is deprecating Marketo Measure functions which rely on third-party cookies; specifically, Cross-Domain Tracking and View-through Attribution, which use the Google/DoubleClick impression cookie. No other functions of Marketo Measure will be impacted. First-party cookie usage is also not impacted. In light of Google's schedule, the expected deprecation date for the two functions above is 6/1/2024. Related data collected before this date remains available to Adobe customers.

## Why is [!UICONTROL View Through Attribution] Important? {#why-is-view-through-attribution-important}

Historically, re-targeting or impression advertising has been difficult for marketers to account for in attribution analysis. Potential clients may, time after time, be exposed to re-targeting ads but it's unlikely that they actually click one of these ads and fill out a form within the same session. Our View Through Attribution solution now has the ability to trace whether or not someone was exposed to an impression ad. This touchpoint will be appended to the individual record and will carry through until the prospect becomes a client. With this information, the marketer will now get better insight on the performance of their re-targeting advertising.

## What is involved in setting this up? {#what-is-involved-in-setting-this-up}

In order for [!DNL Marketo Measure] to start measuring the ad impressions, there is an impression tag that needs to be placed in Doubleclick Campaign Manager. Once the tag is implemented, the impressions are stored in our logs and we take care of the rest. Reach out to your Success Manager if you are interested in measuring view through attribution.

## Which ad platforms are supported? {#which-ad-platforms-are-supported}

We currently support [!DNL Doubleclick] Campaign Manager.

## How is the attribution calculated? {#how-is-the-attribution-calculated}

We ran some careful analysis of impression data and its influence on conversions across all stages and marketing channels. The distribution varies depending on the model as you can see from the table below:

<table> 
 <colgroup> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <th><br></th> 
   <th>First Touch</th> 
   <th>Lead Creation</th> 
   <th>U-Shaped</th> 
   <th>W-Shaped</th> 
   <th>Full Path</th> 
   <th>Custom Model</th> 
  </tr> 
  <tr> 
   <td><strong>Impressions</strong></td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>10%</td> 
   <td>10%</td> 
   <td>10%</td> 
   <td>Custom</td> 
  </tr> 
  <tr> 
   <td><strong>FT</strong></td> 
   <td>100%</td> 
   <td>0%</td> 
   <td>35%</td> 
   <td>26.6%</td> 
   <td>20%</td> 
   <td>Custom</td> 
  </tr> 
  <tr> 
   <td><strong>LC</strong></td> 
   <td>0%</td> 
   <td>100%</td> 
   <td>35%</td> 
   <td>26.6%</td> 
   <td>20%</td> 
   <td>Custom</td> 
  </tr> 
  <tr> 
   <td><strong>OC</strong></td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>26.6%</td> 
   <td>20%</td> 
   <td>Custom</td> 
  </tr> 
  <tr> 
   <td><strong>Closed</strong></td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>20%</td> 
   <td>Custom</td> 
  </tr> 
  <tr> 
   <td><strong>Middle</strong></td> 
   <td>0%</td> 
   <td>0%</td> 
   <td>20%</td> 
   <td>10%</td> 
   <td>10%</td> 
   <td>Custom</td> 
  </tr> 
 </tbody> 
</table>

## What will this look like in [!DNL Salesforce?] {#what-will-this-look-like-in-salesforce}

[!DNL Marketo Measure] will create a single impression Touchpoint on any Lead that was exposed to the display ad. We are able to map the user even after they first come to your website (FT) and fill out a form (LC). The Touchpoint will contain ad information such as Ad Campaign Name/ID, Ad ID, Ad Content, Site Name/ID, Placement Name/ID, Marketing Channel, Geo, Referrer Page, and more.

The view-through attribution model will depend on the client and their data.
