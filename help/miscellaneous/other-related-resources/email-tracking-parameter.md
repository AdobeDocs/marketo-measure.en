---
unique-page-id: 37356030
description: Email Tracking Parameter - [!DNL Marketo Measure]
title: Email Tracking Parameter
exl-id: e2cfd59e-ce4a-4cbb-b64a-828d1db7410f
feature: Tracking
---
# Email Tracking Parameter {#email-tracking-parameter}

The [!DNL Marketo Measure] Email Tracking Parameter allows marketers to treat email clicks as form submissions so that touchpoints get generated for those actions. Without using an email tracking parameter, click-throughs from an email are only treated as "web visits" until the user actually engages with the site through a form submission or a web chat.

## Use Cases  {#use-cases}

**Webinar Registration**: The Marketing team sends out an email invite with a single button to register for a webinar. Because the email already has the person's information, the single click auto-registers them. The landing page contains the email tracking parameter so when they click through and land on the confirmation page, [!DNL Marketo Measure] can capture the email address and treat the click-through as a form fill, which generates a touchpoint.

**Content Download**: The Content Marketing team wants to promote a recent eBook that they've published with a direct download link from an email. When the email template is built, the download confirmation page contains the email tracking parameter so that when they click through, [!DNL Marketo Measure] can capture the email address. Without having to fill out a form on the site, [!DNL Marketo Measure] can generate a touchpoint for the content download. This is because the email landed them on the confirmation page with the email tracking parameter.

## How It Works {#how-it-works}

When a visitor arrives on your site, [!DNL Marketo Measure] expects to find a landing page with either an email address or [!DNL Salesforce] Id so we can associate that visit with a "form submission" and generate a touchpoint for that activity.

As the customer, you build out an email template as you normally would. Once it's time to add in the landing page for the action that you want to track, you need to determine either the token, or variable tag, or macro that your Marketing Automation platform accepts to dynamically display the value for each individual.

Marketo Measure accepts the following values: Email Address, Salesforce Lead Id, or Salesforce Contact Id.

## Tag Examples {#tag-examples}

<table> 
 <colgroup> 
  <col> 
  <col> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <th><p>Marketing Automation</p></th> 
   <th><p>Token / Tag / Macro </p></th> 
   <th><p>Example</p></th> 
   <th><p>Supporting Material</p></th> 
  </tr> 
  <tr> 
   <td><p>Marketo</p></td> 
   <td><p>{{lead.Email Address}} </p></td> 
   <td><p>https://engage.marketo.com/rs/460-TDH-945/images/BZ-B2B-Marketing-Attribution-101-ebook.pdf?mailId={{lead.EmailAddress}}</p></td> 
   <td><p>https://experienceleague.adobe.com/docs/marketo/using/product-docs/demand-generation/landing-pages/personalizing-landing-pages/tokens-overview.html</p></td> 
  </tr> 
  <tr> 
   <td><p>Pardot</p></td> 
   <td><p>%%email%% </p><p>or</p><p>%%user_crm_id%%</p></td> 
   <td><p>https://engage.marketo.com/rs/460-TDH-945/images/BZ-B2B-Marketing-Attribution-101-ebook.pdf?mailId=%%email%%</p></td> 
   <td><p>https://help.salesforce.com/s/articleView?language=en_US&id=pardot_variable_tags_reference.htm&type=5</p></td> 
  </tr> 
  <tr> 
   <td><p>Hubspot</p></td> 
   <td><p>(inserted via Editor)</p></td> 
   <td><p>n/a</p></td> 
   <td><p>https://knowledge.hubspot.com/website-pages/personalize-your-content</p></td> 
  </tr> 
  <tr> 
   <td><p>Act-On</p></td> 
   <td><p>(inserted via Message Composer)</p></td> 
   <td><p>n/a</p></td> 
   <td><p>https://connect.act-on.com/hc/en-us/articles/360033436074-How-to-Personalize-Email-Content-with-CRM-Data</p></td> 
  </tr> 
 </tbody> 
</table>

And finally, within [!DNL Marketo Measure], you need to specify the tracking parameter so that [!DNL Marketo Measure] can locate the email or Id value. The default is "mailId" as shown in the examples above and the screenshot below. Enter the value into your Settings in [!DNL Marketo Measure], then click **[!UICONTROL Save]**.

![](assets/one.png)
