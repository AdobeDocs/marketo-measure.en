---
unique-page-id: 18874722
description: Best Practices for Testing - [!DNL Marketo Measure]
title: Best Practices for Testing
exl-id: ff95a1a9-d324-47f5-b47d-39014dff77e4
feature: Tracking
---
# Best Practices for Testing {#best-practices-for-testing}

You should test all the different types of forms you have to ensure the [!DNL Marketo Measure] JavaScript is working properly.

## Recommended Test Process {#recommended-test-process}

1. Use an incognito browser or clear your cookies between each form submission test _and_ use a different email address each time.

   >[!TIP]
   >
   >A best practice is to use a fake email that contains something indicating it's a test, as well as the time of day. For example: `testing830am@test.com`.

1. Start your search at a search engine (e.g., `google.com`), or navigate to a form directly.

1. Submit the form on your website using a unique email address.

1. Record the URL of the page you're submitting the form on and the email address used.

1. Locate the record created in your CRM (Lead or Contact) for that form submission and verify that a touchpoint was appropriately created.

>[!NOTE]
>
>You can use a [!DNL Marketo Measure] stock report such as Leads with [!DNL Marketo Measure] Touchpoints or look at the Lead/Contact page layout if you chose to update your page layouts with [!DNL Marketo Measure] details. This could take some time for the data to process.
