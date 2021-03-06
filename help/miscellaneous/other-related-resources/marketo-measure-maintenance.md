---
unique-page-id: 18874556
description: Marketo Measure Maintenance - Marketo Measure - Product Documentation
title: Marketo Measure Maintenance
exl-id: 4e1d53bb-0af8-4774-9f69-6a95516b3d11
---
# Marketo Measure Maintenance {#marketo-measure-maintenance}

Marketo Measure pulls almost everything it needs from your CRM on a daily basis, but there are a few maintenance tasks you’ll want to schedule regularly to keep Marketo Measure humming along and outputting the most accurate information possible.

**Sync Buyer Touchpoints for new offline campaigns (2x/month)**

As you learned during onboarding, Marketo Measure gets information about your offline marketing efforts by syncing with your CRM’s campaigns. As your organization kicks off new campaigns, be sure to enable Buyer Touchpoints for each campaign as appropriate. Check out [this article](/help/channel-tracking-and-setup/offline-channels/syncing-offline-campaigns.md)for more information.

**Upload spend for all channels (1x/month)**

To take advantage of Marketo Measure’s full revenue and ROI reporting capabilities, you need to tell Marketo Measure how much you’re spending on each of your marketing channels and subchannels. We recommend designating the owner of each channel/subchannel and having those people report spend to a single party responsible for uploading new cost information on a monthly basis.

Refresh your memory on how to upload cost information by reading [this article](/help/marketing-spend/spend-management/marketing-channel-costs.md).

**Update list of domains to track (1x/month)**

Marketo Measure tracks all pages and subdomains where our Javascript is active, but only for domains that we know about. If you’ve recently debuted a new domain, expanded internationally, or changed your primary domain, contact [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} to make sure we update your account accordingly.

**Review custom channel mapping for accuracy (1x/month)**

During onboarding, you set up custom channel mapping for your online and offline marketing efforts. As your marketing strategy and use of Marketo Measure evolve, you’ll want to keep an eye on that mapping logic to ensure that all your Touchpoints are being categorized appropriately.

Remember, Marketo Measure reprocesses your data when you edit mapping logic, so you won’t be able to change these rules more than once every 7 days.

Reference [this article](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md) for Online setup, [this article](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md) for Offline setup, and this list of best practices curated from our customers:

* Review Touchpoints that are currently falling into any “Other” or “NULL” channels you may have set up. If appropriate, update your mapping logic to re-categorize those Touchpoints into more accurate channels.
* Review Touchpoints that are currently falling into your Direct channels. If some of your email marketing campaigns or other efforts are missing UTM parameters, there’s a good chance that traffic is being inappropriately bucketed into a Direct channel. Consider updating your UTM parameters to capture the referring source.

**Evaluate touchpoint suppression settings (1x/quarter)**

If you’re seeing a lot of touchpoints that you’d prefer not be considered in your attribution story (from a Login or Unsubscribe forms, a Careers page, or an internal app, for example), you may want to evaluate your existing touchpoint suppression settings. Once a quarter, pinpoint any groups of touchpoints that are creating unnecessary noise and update your suppression logic appropriately. [Here’s a helpful article](/help/advanced-marketo-measure-features/touchpoint-settings/touchpoint-removal-and-touchpoint-suppression.md)  with the how-to.

**Review custom stage mapping for accuracy (1x/quarter) (if applicable)**

If you’re using any custom Lead, Contact, or Opportunities stages, you may have also customized what part of the pipeline those stages map to and whether or not those stages are included in a custom attribution model. Once a quarter, visit [this article](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md) to refresh your memory on custom stage mapping and ensure that you’re accurately tracking your custom stages.

**Compare Machine Learning Model to Custom Model weighting (1x/quarter) (if applicable)**

If you’re licensed for Marketo Measure’s Custom Model, you also have data available from our Machine Learning Model (MLM) in Settings > Attribution Settings. The MLM calculates the importance of each stage using touchpoint data from your account, and may help you decide how to allocate attribution weight in your Custom Model. We recommend comparing the MLM to your Custom Model once a quarter, and discussing the implications of potential changes to your Custom Model with your SM.

For more information about Marketo Measure’s Machine Learning Model, check out [this article](/help/advanced-marketo-measure-features/custom-attribution-models/machine-learning-model-faq.md).
