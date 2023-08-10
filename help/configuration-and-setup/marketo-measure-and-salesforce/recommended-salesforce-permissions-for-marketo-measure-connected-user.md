---
unique-page-id: 18874696
description: Recommended [!DNL Salesforce] Permissions for [!DNL Marketo Measure] Connected User - [!DNL Marketo Measure] - Product Documentation
title: Recommended [!DNL Salesforce] Permissions for [!DNL Marketo Measure] Connected User
exl-id: b74aa28b-4a7b-42d1-8df0-d1ae0ff1f338
feature: Salesforce
---
# Recommended [!DNL Salesforce] Permissions for [!DNL Marketo Measure] Connected User {#recommended-salesforce-permissions-for-marketo-measure-connected-user}

[!DNL Marketo Measure] sends and receives data through a connected [!DNL Salesforce] user within the [!DNL Marketo Measure] app.

In order to push touchpoint data to your [!DNL Salesforce] instance, the connected user must have access to [!DNL Marketo Measure] custom objects (i.e. Buyer Touchpoint and Buyer Attribution Touchpoint) as well as standard [!DNL Salesforce] objects such as Leads and Contacts (see [[!DNL Marketo Measure] in Salesforce](/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md).

[!DNL Salesforce] Administrator user licenses can serve as the connected user as they often have the necessary data privileges by default. However, your team may prefer to use an integrations user or a dedicated [!DNL Salesforce] user license to track the impact of [!DNL Marketo Measure] on your instance.

We recommend the following permissions to ensure that [!DNL Marketo Measure] data is accurately flowing:

* [!DNL Marketo Measure] Administrator Permission Set For Dedicated User

The managed permission set gives an SFDC admin the ability to create, read, write, delete records from [!DNL Marketo Measure] objects.

* View and Edit Converted Leads Permission Set

This allows [!DNL Marketo Measure] to decorate leads after they have been converted to contacts. If this permission set is not enabled there can be significant data tracking gaps. You can find more information in [[!DNL Salesforce Trailblazer] community](https://help.salesforce.com/articleView?id=leads_view_edit_converted.htm&type=5).

* [!DNL Salesforce] Marketing User Checkbox

The [!UICONTROL Marketing User] checkbox allows the user to create campaigns and use the Campaign Import Wizards. If this option isn't selected, the user can only view campaigns and advanced campaign setup, edit the Campaign History for a single lead or contact, and run campaign reports. [!DNL Marketo Measure] needs to ability to read and write to the campaign object.

**Additional Troubleshooting**

If [!DNL Marketo Measure] is still experiencing issues reading or writing data it may be helpful to investigate the following:

* Access to [!DNL Salesforce] Queues

If the dedicated user does not have access to leads in queues then it is unable to modify the leads with [!DNL Marketo Measure] data. You can accomplish this by having a role in the hierarchy that allows access to queues or individually granting users access.

* Field Level Security and Accessibility

Field level security and field accessibility are related but have some key differences. Field Level Security defines field visibility for a given profile while Field Accessibility determines whether a field is editable based on the field level security and page layout configuration. Using the [!DNL Marketo Measure] package's permission sets you will receive the necessary field object security settings. In some cases, in order to have the correct field accessibility, the connected user will need to have the [!DNL Marketo Measure] fields on the page layouts. [!DNL Marketo Measure] fields on the layout allow for the [!DNL Marketo Measure] data to map into [!DNL Salesforce]. This will depend on your particular [!DNL Salesforce] environment.

Every organization's [!DNL Salesforce] has individual needs but we provide you with our requirements to balance the [!DNL Marketo Measure] access needs with your security protocols. Don't hesitate to reach out to [[!DNL Marketo Support]](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
