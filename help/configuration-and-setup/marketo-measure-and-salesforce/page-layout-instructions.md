---
unique-page-id: 18874799
description: Page Layout Instructions - [!DNL Marketo Measure] - Product Documentation
title: Page Layout Instructions
exl-id: 627377f0-d0cf-448c-a7b5-7eb5634b9627
---
# Page Layout Instructions {#page-layout-instructions}

>[!NOTE]
>
>You may see instructions specifying "[!DNL Marketo Measure]" in our documentation, but still see "Bizible" in your CRM. We are working to have that updated and the rebranding will be reflected in your CRM soon.

To easily see [!DNL Marketo Measure] data, it's recommended to update Page Layouts for the [!UICONTROL Account], [!UICONTROL Contact], [!UICONTROL Lead], [!UICONTROL Opportunity], and [!UICONTROL Campaign] Objects. The instructions are broken out for each Object Page Layout below.

To begin, first navigate to your [!DNL Salesforce] Setup settings and locate the [!UICONTROL Customize] tab.

## Campaign Object {#campaign-object}

We recommend adding the [!DNL Marketo Measure] fields to your SFDC Campaign for only your sandbox. The fields can be used to test touchpoint generation. In production we recommend only adding the [!DNL Marketo Measure] Bulk Update Touchpoint Date button. We don't recommend adding the [!DNL Marketo Measure] fields to production since you can create Campaign Sync rule rules.

1. Within your Build option, select **[!UICONTROL Campaigns]**.

1. Click **[!UICONTROL Page Layouts]**.

   ![](assets/1-1.jpg)

1. Click **[!UICONTROL Edit]** next to the page layout you want to update.

   ![](assets/2-1.jpg)

1. Within the [!UICONTROL fields] option, select the **[!UICONTROL Enable Buyer Touchpoints]** field and drag it wherever you would like on the page. Next, add the **[!UICONTROL Touchpoint Start Date]** and **[!UICONTROL Touchpoint End Date]** fields.

   ![](assets/3-2.png)

1. Next, at the top of the page click the "[!UICONTROL Buttons]" option within the quick find menu.

1. Drag the **[!UICONTROL Bulk Update Touchpoint Date]** button to your custom buttons section.

   ![](assets/4-1.jpg)

1. Click **[!UICONTROL Save]**.

   >[!NOTE]
   >
   >If you are using multiple Campaign record types, the picklist values for the **[!UICONTROL Enable Buyer Touchpoints]** field will need to be updated. Please reference [this article](/help/channel-tracking-and-setup/offline-channels/configurations-for-multiple-campaign-record-types.md) for instructions.

## Leads {#leads}

1. Within your Build option, select **[!UICONTROL Leads]**.

1. Click **[!UICONTROL Page Layouts]**.

1. Click **[!UICONTROL Edit]** next to the page layout you want to update. Keep in mind that multiple page layouts can contain the Buyer Touchpoints sections.

1. Click on the VisualForce page option on the left within your quick find menu.

1. Create a new section and name it "Buyer Touchpoints."

   >[!NOTE]
   >
   >Select the "one column" format for each of these sections.

1. Drag the **[!UICONTROL Marketo Measure Lead Related List]** VisualForce page into your page layout section.

   ![](assets/5-1.png)

1. Click on the wrench within the [!DNL VisualForce] page and change the height to 100 and enable scrollbars.

1. Back in the menu, select the [!UICONTROL Canvas Apps] section and create a new section called "Marketo Measure Insights" beneath the Touchpoints [!DNL VisualForce] section you just created.

   >[!NOTE]
   >
   >Select the "one column" format for each of these sections.

1. Drag the [!DNL Marketo Measure Insights] Canvas App into that newly created section. Click **Save**. Sometimes it's necessary to save the page layout first before dropping in the Canvas App because Salesforce doesn't instantly recognize it. So after creating the new section, save the page layout and then re-edit to drag the canvas app within that section. This applies to every object.

   >[!NOTE]
   >
   >For the [!DNL Marketo Measure Insights] Canvas App to function properly, [permissions need to be configured properly](/help/configuration-and-setup/marketo-measure-insights-canvas-app/marketo-measure-insights-configuration.md).

   >[!TIP]
   >
   >Most customers don't use the fields that end with (FT) or (LC) because they're legacy fields from before the [!DNL Marketo Measure] Touchpoint existed as an object.

If you're leveraging the [!DNL Marketo Measure] ABM feature, [please click here for additional page layout instructions](/help/advanced-marketo-measure-features/account-based-marketing/account-based-marketing-overview.md).

## Contacts {#contacts}

1. Within your Build option, select **[!UICONTROL Contacts]**.

1. Click **[!UICONTROL Page Layouts]**.

1. Select the Page Layout you'd like to edit.

   Go to the Related Lists option within the quick find menu and add the **[!UICONTROL Buyer Touchpoints]** related list.

1. Click the wrench icon and add the following columns in this order:

   * Buyer Touchpoint
   * Marketing Channel
   * Touchpoint Source
   * Ad Campaign Name
   * Touchpoint Position
   * Touchpoint Date

1. Sort By: Touchpoint Date, Ascending.

   ![](assets/6.jpg)

1. Expand the Buttons option and deselect **[!UICONTROL New]**.

   ![](assets/7.png)

1. Go back to the [!UICONTROL Related List] option in the menu and now add the **[!UICONTROL Buyer Attribution Touchpoint]** related list.

1. Click the wrench icon and add the following columns in this order:

   * Attribution Touchpoint
   * Marketing Channel
   * Opportunity
   * Ad Campaign Name
   * Touchpoint Type
   * Touchpoint Position
   * Attribution % W-Shaped (_or most robust attribution model such as Full Path or Custom_)
   * Revenue W-Shaped (_or most robust attribution model such as Full Path or Custom_)
   * Touchpoint Date

1. Sort by Touchpoint [!UICONTROL Date] > [!UICONTROL Ascending].

1. Expand the Buttons section and deselect **[!UICONTROL New]**.

1. Click **[!UICONTROL Save]**.

## Opportunities {#opportunities}

1. Within your Build option, select **[!UICONTROL Opportunities]**.

1. Click **[!UICONTROL Page Layouts]**.

1. Select the Page Layout you'd like to edit.

1. Add the **[!UICONTROL Buyer Attribution Touchpoint]** Related List and click the wrench to add the following columns for Opportunities:

   * Attribution Touchpoint
   * Marketing Channel
   * Contact
   * Ad Campaign Name
   * Touchpoint Type
   * Touchpoint Position
   * Attribution % W-Shaped (_or most robust attribution model such as Full Path or Custom_)
   * Revenue W-Shaped (_or most robust attribution model such as Full Path or Custom_)
   * Touchpoint Date

1. Sort by [!UICONTROL Touchpoint Date] > [!UICONTROL Ascending].

1. Deselect **[!UICONTROL New]** within the [!UICONTROL Buttons] section.

1. Click **[!UICONTROL Save]**.

## Accounts {#accounts}

1. Within your Build option, select **[!UICONTROL Accounts]**.

1. Click **[!UICONTROL Page Layouts]**.

1. Select the Page Layout you'd like to edit.

1. Add the **[!UICONTROL Buyer Attribution Touchpoint]** Related List and click the wrench to add the following columns:

   * Attribution Touchpoint
   * Marketing Channel
   * Opportunity
   * Ad Campaign Name
   * Touchpoint Type
   * Touchpoint Position
   * Attribution % W-Shaped (_or most robust attribution model such as Full Path or Custom_)
   * Revenue W-Shaped (_or most robust attribution model such as Full Path or Custom_)
   * Touchpoint Date

1. Sort by Touchpoint Date > Ascending.

1. Deselect **[!UICONTROL New]** within the [!UICONTROL Buttons] section.

1. Click **[!UICONTROL Save]**.

If you are leveraging the [!DNL Marketo Measure] ABM feature,  [please click here for additional page layout instructions](/help/advanced-marketo-measure-features/account-based-marketing/account-based-marketing-overview.md).
