---
unique-page-id: 18874732
description: Best Practices for Setting Up UTM Parameters - [!DNL Marketo Measure]
title: Best Practices for Setting Up UTM Parameters
exl-id: 56019f41-b6ba-48c1-9bef-2a5f56d2d5f4
feature: UTM Parameters
---
# Best Practices for Setting Up UTM Parameters {#best-practices-for-setting-up-utm-parameters}

UTM parameters are great way to slice and dice your marketing data. [!DNL Marketo Measure] uses and captures all UTM parameters to populate fields in Salesforce and in the [!DNL Marketo Measure] app. With this information, you are able to get a granular understanding of where your leads, opportunities, and closed/won deals are coming from.
  
You can use the [Google URL Builder](https://support.google.com/analytics/answer/1033867?hl=en){target="_blank"} to set up your UTM parameters and add them to your links within your marketing efforts. Use this [Google Spreadsheet](https://docs.google.com/spreadsheets/d/1QCIr1WUJQHE68cA4VTks2XE7nxuryaUymCEy_23-Oew/edit#gid=0){target="_blank"} if you want an easier way to track all your UTM links.

## High-level values for each parameter {#high-level-values-for-each-parameter}

**utm_medium**: This field maps to the Medium field. Use utm_medium to denote the high-level channel.

For example, [!UICONTROL Social], CPC, email, web, organic

Do not use this field to call out the subchannel.
  
**utm_source**: This field maps to the Touchpoint Source field. Use utm_source to define the subchannel from which the lead originates.
  
For example, Facebook, Twitter, Linkedin, Drip_email, Email_blast, newsletter.  
  
Keep it simple. Do not use this parameter to denote ad types, like retargeting or sponsored. Do not add a utm_source = homepage, webdirect, website. [!DNL Marketo Measure] automatically fills out this information for you.  
  
**utm_campaign**: This field maps to Ad Campaign Name. Use utm_campaign to denote the title of the campaign as it exists in the ad platform, or as it's referred to internally.  
  
This is also a good parameter to denote Geolocation, Ad network type (display v. search), and so on.  
  
It is recommended to use underscores instead of spaces, and avoid using punctuation. This reduces the chances of encoding errors by browsers when reading your parameters.  
  
For example, AU_Idea_for_an_App_50k  

**utm_content**: This maps to Ad Content. Use the Ad Title in the utm_content parameter. If it is an image ad, use ad title and include the ad dimensions.

For example, [ad title] 200x400px

**utm_term**: This maps to Keyword Text. Use this parameter to denote the keyword related to the firing of the ad.

If there is no keyword related to the ad, leave this parameter blank.

For example, iPhone App Ideas

**Keep it simple and succinct. Do not duplicate efforts, terms, and channels.**

We imagine the UTM hierarchy as follows:

Medium > [!UICONTROL Source] > [!UICONTROL Campaign] > [!UICONTROL Content/Term]

For example, If a [!UICONTROL display] ad is placed on Facebook, we recommend the following:

fakewebsite.com/

?utm_medium=social

&utm_source=facebook

&utm_campaign=Display_campaign_ID

&utm_content=content_of_campaign

Notice that terms/channel are not duplicated and utm_term is not used in this case.

If there are any questions, reach out to the Adobe Account Team (your Account Manager) or [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
