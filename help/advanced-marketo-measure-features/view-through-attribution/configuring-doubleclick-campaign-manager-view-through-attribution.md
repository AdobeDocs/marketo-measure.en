---
unique-page-id: 18874781
description: Configuring Doubleclick Campaign Manager View Through Attribution - [!DNL Marketo Measure]
title: Configuring Doubleclick Campaign Manager View Through Attribution
exl-id: 2cc6c2cd-afb7-4052-b18b-9ad0bf16a9fa
feature: Attribution
---
# Configuring Doubleclick Campaign Manager View Through Attribution {#configuring-doubleclick-campaign-manager-view-through-attribution}

## Measuring View Through Attribution {#measuring-view-through-attribution}

>[!NOTE]
>
>If you're using the [!DNL Marketo Measure] and DoubleClick Campaign Manager integration, we require an [API connection](/help/api-connections/utilizing-marketo-measures-api-connections/integrated-ad-platforms.md#how-to-connect-ad-platforms) so we can download details of the campaigns and creatives to resolve the ads.

To begin gaining more granular insight from view through tracking with Doubleclick Campaign Manager, our tracking pixel needs to be configured.

For more information about the [!DNL Marketo Measure] View Through Attribution functionality, refer to [Marketo Measure View Through Attribution FAQ](/help/advanced-marketo-measure-features/view-through-attribution/marketo-measure-view-through-attribution-faq.md).

[!DNL Marketo Measure] is considered a piggyback tag because it's a third party call through the DCM ad tag. Piggyback tags do not work with image tags, only iframe or javascript tags. According to DCM Support, this did not change recently and has always been the case. Standard tags were deprecated on Oct 2, 2017 but do not affect the ability of [!DNL Marketo Measure] to track the impressions.

In the event you use a Parent and Child hierarchy in DCM, we will need our tag applied to all levels for impression tracking.

## How to add the Image Tag {#how-to-add-the-image-tag}

Add the tag into Doubleclick under the Advertiser setting and create an Impression Event Tag.

1. Add the following code as a 1x1 image pixel.

`https://cdn.bizibly.com/i?v=%eadv!&a=%eaid!&c=%ecid!&s=%esid!&p=%epid!&m=%m&n=%n`

1. Once it's added, confirm the delimiters are mapped as follows. This should be automatic once the tag is applied:

   v = %eadv! Expand Advertiser Id  
   a = %eaid! Expand Ad Id  
   c = %ecid! Expand Creative Id  
   s = %esid! Expand Site Id  
   p = %epid! Expand Placement Id  
   m = %m Match Code Macro  
   n = %n Random Number Macro

   ![](assets/1.png)

## FAQ {#faq}

**Q: Is the image tag secure?**

A: Yes. It is not a JavaScript tag, it is an image tag.

**Q: What permissions does the connected user need?**

A: dfatrafficking, dfareporting, userinfo.email

**Q: How long can it take to import spend data?**

A: Up to 6 hours

**Q: How long can it take to import ad data?**

A: Up to 6 hours
