---
unique-page-id: 18874634
description: Duplicate Records in My Report - [!DNL Marketo Measure] - Product Documentation
title: Duplicate Records in My Report
exl-id: 4ee42371-5b67-4c69-9b49-3249f33614d0
feature: Reporting
---
# Duplicate Records in My Report {#duplicate-records-in-my-report}

>[!NOTE]
>
>You may see instructions specifying "[!DNL Marketo Measure]" in our documentation, but still see "[!DNL Bizible]" in your CRM. We are working to have that updated and the rebranding will be reflected in your CRM soon.

As you dive into the [!DNL Marketo Measure] Reports in [!DNL Salesforce], you may start to find 'duplicate' records in your reports. You will likely experience this feeling when you review [!DNL Marketo Measure] out-of-the-box reports.

When reporting with the Buyer Touchpoints object or the Buyer Attribution Touchpoint object, it's important to understand that you're no longer reporting on the count of leads, contacts, or opportunities but rather you'll be reporting on the number of Buyer Touchpoints or Buyer Attribution Touchpoints associated to those standard objects (leads, contacts, opportunities).

Let's take the following report as an example:

This is a **Contacts with Buyer Touchpoints** report. Again, this means that we're looking at the count of touchpoints associated to an individual contact.

![](assets/1.gif)

As you can see, it looks like there are three James Williams contacts in the report, and therefore you might be thinking, "duplicates!"

However, this report is showing the number of touchpoints related to James. Within the report, you can see that James has an individual FT (First Touch), an individual LC, Form (Lead Creation Touch), and a PostLC touchpoint (a form submission that takes place after the LC touchpoint).

If you want to understand the 'count of contacts' you can then use the fields 'Count - First Touch', 'Count-Lead Creation Touch' or 'Count-U-Shaped' to understand how many contacts have had marketing interactions.

>[!MORELIKETHIS]
>
>[[!DNL Marketo Measure] University: Stock SFDC Reports](https://universityonline.marketo.com/courses/bizible-fundamentals-bizible-102/#/page/5c5cb68dfb384d0c9fb96cc4)
