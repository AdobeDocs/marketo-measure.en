---
description: "[!DNL Marketo Measure] Reporting Guide - [!DNL Marketo Measure] - Product Documentation"
title: "[!DNL Marketo Measure] Reporting Guide"
exl-id: 9b991f9e-c187-4b43-b0a8-8ed3e9a6056b
---
# [!DNL Marketo Measure] Reporting Guide {#marketo-measure-reporting-guide}

>[!NOTE]
>
>You may see instructions specifying "[!DNL Marketo Measure]" in our documentation, but still see "Bizible" in your CRM. We are working to have that updated and the rebranding will be reflected in your CRM soon.

Before building a [!DNL Marketo Measure] report, it's most crucial to confirm your [!DNL Marketo Measure] Account Settings have been reviewed and configured to ensure the data within the reports is accurate and reflects the specificities of your business. In addition to this, reporting projects work best when they follow a structured process. Justin Norris, a [!DNL Marketo Measure] power-user, advocate and partner from [Perkuto](https://perkuto.com/) expertly summarized [how to approach reporting in [!DNL Marketo Measure]](https://perkuto.com/blog/turning-attribution-data-into-actionable-insights/):

**Establish Goals**: "The first question to ask is 'why do we measure?' Lori Wizdo of [Forrester Research](https://go.forrester.com/) summed it up nicely in a [Marketo webinar](https://www.marketo.com/webinars/beyond-revenue-performance-real-kpis-of-b2b-marketing/). According to her, 'we measure to prove or validate a decision or the value of marketing or to get better (process improvement).' We would add that the insights from good measurement also provide input and guidance into the marketing planning process.

So before you begin, it's essential to be crystal clear on your goals, the questions you're trying to answer, or the problems you're attempting to solve. What story do you want to tell? What decisions will be made as a result? Too often these fundamentals are poorly thought out, leading to frustration for all involved."

**Report Design**: "Next, you need to design the report and determine the specific dimensions, metrics, and dataset it will contain. A common experience is to provide a business user with exactly what they ask for, only for them to still feel that their needs are unmet. This is because the insight a business user is actually looking for is not always contained in the report they request. A good analyst (or a MOPS person with an analyst hat on) will ask clarifying questions, establish common definitions ("so, what do you really mean by lead?"), and even sketch out a visual of the final report to make sure there's alignment. Only then do you build the report, knowing you have a solid set of requirements."

**Report Build**: "Once you go to build, it's not uncommon to run into roadblocks or dead-ends. For example, you might discover that you lack an essential data point or that your objects don't link in the way that you need. To solve these problems, I also think it's critical to understand what's happening "under the hood" in your reporting "machine." This fluency will allow you to quickly size up a reporting request and evaluate whether it's achievable (and more easily devise creative solutions when it's not)."

Let's take a look "under the hood" to better understand what makes the [!DNL Marketo Measure] attribution reporting machine run.

## Buyer Touchpoint Objects (CRM) {#buyer-touchpoint-objects-crm}

At the highest level, there are two reporting categories based on the two different Buyer Touchpoint objects: These categories determine which type of [!DNL Marketo Measure] data you would like to report on: data related to an _individual_, or data related to an _opportunity_.

1. **Buyer Touchpoints** (BTs) / Individuals / Total Engagement

   * Commonly used for 'top of the funnel' (TOFU) metrics and reporting related to _individuals_ (Leads, Contacts, [!DNL Marketo Measure] Persons)
   * BTs are used for understanding all marketing interactions related to **people**, as they contain the complete touchpoint history for each person. As a reminder, these touchpoints are created in CRM for the anonymous First Touch, the Lead Creation Touch, and any subsequent form submission or touchpoint that you choose to sync from
an offline campaign or activity.

1. **Buyer Attribution Touchpoints** (BATs) / Opportunity / Account level / Revenue

   * Commonly used for 'middle and/or bottom of the funnel' (MOFU and BOFU) metrics and reporting related to _Opportunities_.
   * BATs represent the relevant touchpoints of all the people connected to the **opportunity** (either via Opportunity Contact Roles or via a shared Account ID, depending on your settings). Unlike BTs which relate only to people, BATs can also be associated with **revenue**. As such, you'll use BATs to answer questions related to opportunities, including how many opportunities were opened or closed, or the pipeline value and revenue won.

>[!NOTE]
>
>BATs are created from BTs. Essentially, tracking begins at the individual level via the BTs. Once an Opportunity is created on an Account, all BTs from Contacts under the same Account are referenced and eligible to create BATs that relate to the Opportunity, so you'll want to use one or the other depending on what questions you're trying to answer: questions related to 'People' metrics (BT reports), or questions related to 'Opportunity' metrics (BAT reports)

Support Article: [Difference Between Buyer Touchpoints and Buyer Attribution Touchpoints](/help/configuration-and-setup/getting-started-with-marketo-measure/difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints.md#configuration-and-setup)

## Buyer Touchpoint (BT) {#buyer-touchpoint-bt}

The Buyer Touchpoint (BT) is the object used to track every marketing interaction someone has with your marketing materials. Each individual's (Lead/Contact/[!DNL Marketo Measure] Person) journey would be represented by their related BTs. In [!DNL Marketo Measure], an individual's journey consists of:

1. How did this person first interact with our brand? (First Touch or _FT_)
1. How did this person convert / become known / become a Lead? (Lead Creation or _LC_)
1. How else has this person interacted with our brand and marketing materials since becoming a Lead? (_PostLC_)

Buyer Touchpoints are used to answer questions related to _people_ ("people" are represented by either Leads or Contacts within a CRM), such as Lead/Contact generation or acquisition metrics, rather than Opportunity related metrics. For example:

* Which channels are delivering the most Leads?
* Which channels are more or less costly to create a new Lead?
* What content are my Leads/Contacts engaging with?
* What is the marketing story of particular titles, roles, personas?
* Which channels drive MQLs, or other Lead/Contact statuses?

Primarily, companies need to know, "where are my Leads/Contacts coming from?". Historically, this was answered with a single, one dimensional value (Lead Source for example). However, as outlined in #1 and #2 above, we know that Leads can have multiple touchpoints during their journey of becoming a Lead. The Buyer Touchpoint allows us to get insight into the two most crucial interactions that represent how a Lead was generated: their First Touch and their Lead Creation Touch. Buyer Touchpoints are also _multi-dimensional_ meaning they carry loads of marketing data, primarily where the person came from (Marketing Channel) and what the person engaged with (Content).

The [attribution models](/help/introduction-to-marketo-measure/overview-resources/marketo-measure-attribution-models.md) providing the best insight into people-based metrics are:

* **First Touch** - 100% attribution credit to the Lead's First Touch (FT)
* **Lead Creation** - 100% attribution credit to the Lead's Lead Creation Touch (LC)
* **U-Shaped** - multi-touch approach, with 40% credit to the FT, 40% credit to the LC

<table> 
 <tbody>
  <tr>
   <td><img src="assets/bizible-reporting-guide-1.png"></td> 
   <td>The U-Shape Model is designed to give credit to any Buyer Touchpoints that summarize how a Lead became a Lead. While subsequent touchpoints from these Leads can also be reported to understand additional engagement (Post LC), they are not a part of the <strong>Lead Creation journey</strong> so they do not get any attribution credit in the FT, LC or U-shaped models.<p>

&#42;Most commonly, U-shaped attribution reflects an even 50/50 split between FT and LC. If the Lead converts in the same session as the First Touch, a single touchpoint would represent both the FT and LC Touchpoint Positions. Therefore, 100% of the attribution would be given to a single touchpoint.</td> 
  </tr>
 </tbody>
</table>

These models place heavy emphasis on early-stage interactions and top of funnel engagement. U-Shaped attribution is the recommended model as it factors in both the FT and LC touchpoints ensuring credit is given to any touch that influenced the Lead into creation. However, additional insight can be gained from the First Touch and Lead Creation Touch models if you are looking to understand those specific parts of the Lead journey in more detail.

## Recommended Reports using the Buyer Touchpoint (BT) {#recommended-reports-using-the-buyer-touchpoint-bt}

1. **LEADS with BUYER TOUCHPOINTS**

**1.1 | New Leads by Marketing Channel**

Summarizing your Lead's Buyer Touchpoint data by the field 'Marketing Channel' is the highest-level view that represents what channels/tactics are influencing new Leads into creation. Structuring this report around a 'Date Type' = "Created Date" ensures a cohort of 'net new Leads' (when the Lead was created in your CRM) is established in the report.

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>What marketing channels are influencing Leads into creation?</td> 
  </tr>
  <tr>
   <td>Report Type</td> 
   <td>Leads and Buyer Touchpoints (CRM)<br>
   Metric: Leads ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Date Field / Date Type</td> 
   <td>Lead Created Date (CRM) / Created Date (Discover)</td> 
  </tr>
  <tr>
   <td>Date Range</td> 
   <td><i>select desired date range</i></td> 
  </tr>
  <tr>
   <td>Group / Dimension</td> 
   <td>Marketing Channel</td> 
  </tr>
  <tr>
   <td>Optimal Models</td> 
   <td>First Touch, Lead Creation, <strong>U-Shaped</strong><br>
   &#42;SUM the 'Count' fields in your CRM reports (Count - First Touch, Count - Lead Creation, Count - U-Shaped)</td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>For any 'Leads with Buyer Touchpoints' report type, start by customizing the pre-built report titled '[!DNL Marketo Measure] 101 | Leads by Channel'. This report is available out-of-the box and is a great sandbox pre-built as described in the table above and can quickly be customized for more specific reporting needs.

**1.2 | New Leads by Campaign (or more granular insights)**

For more granular insight into the data summarized in the 'New Leads by Marketing Channel' report (1.1), add an additional summary at the campaign level. This will allow you to not only understand what 'Marketing Channels' are driving new Leads into creation, but more specifically, what campaigns within those channels are performing the best:

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>What <i>campaigns</i> are influencing Leads into creation?</td> 
  </tr>
  <tr>
   <td>Report Type</td> 
   <td>Leads and Buyer Touchpoints (CRM)<br>
   Metric: Leads ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Date Field / Date Type</td> 
   <td>Lead Created Date (CRM) / Created Date (Discover)</td> 
  </tr>
  <tr>
   <td>Date Range</td> 
   <td><i>select desired date range</i></td> 
  </tr>
  <tr>
   <td>Group / Dimension</td> 
   <td>Ad Campaign Name (CRM)</td> 
  </tr>
  <tr>
   <td>Optimal Models</td> 
   <td>First Touch, Lead Creation, <strong>U-Shaped</strong><br>
   &#42;SUM the 'Count' fields in your CRM reports (Count - First Touch, Count - Lead Creation, Count - U-Shaped)</td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Get even more granular insight by summarizing the report with other available fields from the Buyer Touchpoint object. Do this by setting additional groupings (CRM) or dimensions (Discover). Depending on the channel (which may be representative of your role), there may be additional details beyond the campaign level in which you're looking to gain insight. Let's drill into 'Paid Search' for example in the table below...

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>What <i>keywords</i> are influencing Leads into creation?</td> 
  </tr>
  <tr>
   <td>Report Type</td> 
   <td>Leads and Buyer Touchpoints (CRM)<br>
   Metric: Leads ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Filters</td> 
   <td>Marketing Channel = Paid Search</td> 
  </tr>
  <tr>
   <td>Date Field / Date Type</td> 
   <td>Lead Created Date (CRM) / Created Date (Discover)</td> 
  </tr>
  <tr>
   <td>Date Range</td> 
   <td><i>select desired date range</i></td> 
  </tr>
  <tr>
   <td>Group / Dimension</td> 
   <td>Keyword Text (CRM) / Keyword (Discover)</td> 
  </tr>
  <tr>
   <td>Optimal Models</td> 
   <td>First Touch, Lead Creation, <strong>U-Shaped</strong><br>
   &#42;SUM the 'Count' fields in your CRM reports (Count - First Touch, Count - Lead Creation, Count - U-Shaped)</td> 
  </tr>
 </tbody>
</table>

The level of granularity may vary by channel. The recommended approach would be to ask yourself, "what about 'channel X' am I looking to understand in more detail?". Paid Search Managers may also be interested in additional dimensions such as:

* Ad Campaign Name
* Ad Content
* Ad Group

Events Managers however may be more interested in which specific Events or which types of Events influenced the most Leads into creation:

* Ad Campaign Name / Salesforce Campaign = specific Event
* Medium = Campaign 'Type'

**REMINDER**: Additional filters may need to be added to any of the report variations outlined above or below. These filters would be specific to your organization and would be something that your Marketing Ops or Sales Ops teams could help advise. It's not uncommon for an organization to run the same filters across all reports to ensure the report is as clean and accurate as possible. Common examples could be:

* Filtering out any internal records from tests, usually by email address
* Filtering based on certain 'Record Types' that may be specific to your business unit

**1.3 | New Leads by Content (CRM reports only)**

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>What <i>content</i> are influencing Leads into creation?</td> 
  </tr>
  <tr>
   <td>Report Type</td> 
   <td>Leads and Buyer Touchpoints (CRM)</td> 
  </tr>
  <tr>
   <td>Date Field</td> 
   <td>Lead Created Date</td> 
  </tr>
  <tr>
   <td>Date Range</td> 
   <td><i>select desired date range</i></td> 
  </tr>
  <tr>
   <td>Group / Dimension</td> 
   <td>Landing Page<br> 
   Form URL</td> 
  </tr>
  <tr>
   <td>Optimal Models</td> 
   <td>First Touch, Lead Creation, <strong>U-Shaped</strong><br></td> 
  </tr>
 </tbody>
</table>

**REMINDER**: The two primary fields for reporting on digital content/assets are 'Landing Page' and 'Form URL'. These two values may be the same if the Lead converts (submits a form) on the same page in which they "landed" (Landing Page), _however_, sometimes these values are different. For example, the Lead may click a link on Facebook that takes them to a page of your website (this would be the 'Landing Page' value). The Lead may then navigate away from that page, continue their session on the site, and end up submitting a form on another page (Form URL). This would be summarized in a single touchpoint that represents where the Lead came from (Marketing Channel), what content brought them to the site (Landing Page), and what content they ended up downloading (Form URL). 'Form URL' is also the go-to field for reporting on other forms not associated with downloadable content such as 'Contact Us' or 'Demo Request' forms.

>[!TIP]
>
>Get insight into specific 'content' with additional filters
>
>* Filter by: 'Landing Page' CONTAINS (for example):
>   * /blog
>   * /ebook
>   * /webinar
>
>* OR: 'Form URL' CONTAINS (for example)
>   * /contact
>   * /demo

'Content' based reports provide great value when reporting on any part of the funnel, however they are most commonly used at the top of the funnel to provide additional insight into a Leads initial engagement. Considering "Organic Search" tends to be the strongest channel at driving initial engagement (FT), there isn't as much 'Campaign' level data.

'Content' based reports are great for gaining insight into what's driving Leads more specifically within the higher-level Marketing Channel, in this case "Organic Search".

**1.4 | Total Lead Engagement in a given Date Range**

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>What marketing channels have had the most <i>total Lead engagement</i> in the past (week/month/quarter)?</td> 
  </tr>
  <tr>
   <td>Report Type</td> 
   <td>Leads and Buyer Touchpoints (CRM)<br> 
   Metric: Leads ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Date Field / Date Type</td> 
   <td>Touchpoint Date</td> 
  </tr>
  <tr>
   <td>Date Range</td> 
   <td><i>select desired date range</i></td> 
  </tr>
  <tr>
   <td>Group / Dimension</td> 
   <td>Marketing Channel (or more granular)</td> 
  </tr>
  <tr>
   <td>Optimal Models&#42;</td> 
   <td>&#42;This report is less about measuring where Leads are coming from with an attribution model but more about the <i>total number of touchpoints (amount of engagement)</i>, inclusive of those after the Lead Creation Touch. The total record count of touchpoints would reflect which channels have seen the most Lead engagement.</td> 
  </tr>
 </tbody>
</table>

**REMINDER**: Basing your reports around 'Touchpoint Date' is the most reflective way of understanding marketing performance during a certain date range. 'Touchpoint Date' structures the report in a way where the attribution isn't only related to the channel, campaign, or content, but also shows when the touchpoint occured. This is the most effective way at understanding what marketing engagement was happening at a certain point in time and also the recommended way of measuring marketing's impact as it compares to marketing spend invested during the same time. It is recommended when doing any marketing spend or ROI analysis (see 5.1).

**2. MARKETING QUALIFIED LEADS with BUYER TOUCHPOINTS**

One of the most common reports is focused not just on new Leads or Lead level engagement, but more specifically 'marketing qualified leads' (MQLs). There are a couple of different approaches when it comes to reporting on MQLs depending on what [!DNL Marketo Measure] features and functionality you have access to.

**2.1 | Marketing Qualified Leads by Channel (multi-touch)**

This approach towards measuring marketing's impact on influencing MQLs is essentially a continuation of the 'New Leads by Marketing Channel' (1.1) report but with the additional criteria that the Leads being measured are more specifically MQLs. The U-Shaped attribution model is still recommended here to identify what marketing channels and content are generating Leads that are then _likely_ to become an MQL:

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>Which marketing channels are best at generating new Leads that become <i>MQLs</i>?</td> 
  </tr>
  <tr>
   <td>Report Type</td> 
   <td>Leads and Buyer Touchpoints (CRM)<br> 
   Metric: Leads ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Filters</td> 
   <td>MQL = true&#42;<br>
   &#42;<i>MQLs may be defined differently per organization. Ensure the [!DNL Marketo Measure] report is filtered for MQLs using the same field(s) as other MQL based reports. A Segment filter would need to be created in the same way for reporting on MQLs in [!DNL Marketo Measure] Discover.</i></td> 
  </tr>
  <tr>
   <td>Date Field / Date Type</td> 
   <td>MQL Date (or equivalent) / Created Date ([!DNL Marketo Measure] Discover)<br> <i>Lead Created Date could also be used in CRM reporting if 'MQL Date' isn't an option in your CRM. It's important to keep in mind what Date Field you're using at it defines the cohorted data set.</i></td> 
  </tr>
  <tr>
   <td>Date Range</td> 
   <td><i>select desired date range</i></td> 
  </tr>
  <tr>
   <td>Group / Dimension</td> 
   <td>Marketing Channel</td> 
  </tr>
  <tr>
   <td>Optimal Models</td> 
   <td>First Touch, Lead Creation, <strong>U-Shaped</strong><br> 
   SUM the 'Count' fields in your CRM reports (Count - First Touch, Count - Lead Creation, Count - U-Shaped)</td> 
  </tr>
 </tbody>
</table>

**2.2 | Marketing Qualified Leads by Channel (single touch, CRM only)**

This approach towards measuring marketing's impact on influencing MQLs is focused more on identifying which _single touchpoint_ was the last touch before the Lead reached MQL.

>[!NOTE]
>
>In order to run this report, a 'Lead Status' value of 'MQL' is required to define the MQL stage for tracking purposes (Funnel Stage). If MQLs aren't tracked via the 'Lead Status' field, the Custom Attribution Model with Custom Stages feature is necessary to build a custom 'MQL' Stage in the [!DNL Marketo Measure] Account Settings.

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>Which marketing channels are strongest at pushing Leads to reach the MQL status?</td> 
  </tr>
  <tr>
   <td>Report Type</td> 
   <td>Leads and Buyer Touchpoints (CRM)<br>
   <i>this report is only possible within CRM reporting. It is not possible to filter on certain 'Touchpoint Position' values in [!DNL Marketo Measure] Discover</i></td> 
  </tr>
  <tr>
   <td>Filters</td> 
   <td><strong>Touchpoint Position CONTAINS "MQL"</strong></td> 
  </tr>
  <tr>
   <td>Date Field / Date Type</td> 
   <td>MQL Date (or equivalent)</td> 
  </tr>
  <tr>
   <td>Date Range</td> 
   <td><i>select desired date range</i></td> 
  </tr>
  <tr>
   <td>Group / Dimension</td> 
   <td>Marketing Channel</td> 
  </tr>
  <tr>
   <td>Optimal Models</td> 
   <td><i>Because this report is filtered on a single touchpoint, the Lead level attribution models aren't as relevant. Like the 'Lead Engagement Report' (1.4), the number of touchpoint records would be leveraged here to understand which channels are the strongest (each Lead would only have one MQL touchpoint).</i></td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Explore other groupings or dimensions to gain additional insight into MQLs. As mentioned in the other 'Leads with Buyer Touchpoints' reports, the Buyer Touchpoint offers much more granularity than just Marketing Channel. A 'Content' based report could also be combined with either of the MQL reports above to better understand what content is best influencing MQLs.

**3. [!DNL MARKETO MEASURE] PERSONS with BUYER TOUCHPOINTS**

There's a third custom [!DNL Marketo Measure] object in Salesforce that can be very useful when reporting on people related metrics: **the [!DNL Marketo Measure] Person (BP)**. The BP solves the age-old problem of how to represent both Leads and Contacts information in the same report. It unites all BTs related to a "person" (a [!DNL Marketo Measure] Person's ID is their email address). Whether they exist as a Lead or a Contact, the BP acts as a bridge object, to help reports span across Lead and Contact, and is very useful in producing more sophisticated reports on people.

The [!DNL Marketo Measure] Person relates to only one of the touchpoint objects, the Buyer Touchpoint (BT). This means that it can't be leveraged for an Opportunity or revenue related metrics. A '[!DNL Marketo Measure] Person and Buyer Touchpoints' report type is great for understanding _total engagement_ as it surfaces all BTs whether the BT relates to a Lead or Contact more specifically. For example - if you have a Salesforce Campaign being used to track an Event, you may have campaign members within the CRM Campaign that exist either as Leads OR Contacts. [!DNL Marketo Measure] will create touchpoints for the campaign members regardless, but without the [!DNL Marketo Measure] Person, standard Salesforce reporting would require two separate reports to understand how many _total_ touchpoints you have from the Event: one that's 'Leads with Buyer Touchpoints' and one that's 'Contacts with Buyer Touchpoints'. A few other [!DNL Marketo Measure] Person based reporting use cases are listed below:

**3.1 [!DNL Marketo Measure] Persons who have Downloaded 'ebooks' or 'whitepapers' (total downloads)**

This report would be the same as a 'Content' based report at the Lead level. However, rather than looking to measure the number of attributable Leads to each piece of content, using a [!DNL Marketo Measure] Persons report will be helpful in understanding the total _number of downloads_ if the asset is gated (the total number of touchpoints would represent the total number of downloads/form submissions).

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>How many people have downloaded a particular asset?</td> 
  </tr>
  <tr>
   <td>Report Type</td> 
   <td>[!DNL Marketo Measure] Persons and Buyer Touchpoints (CRM)</td> 
  </tr>
  <tr>
   <td>Filters</td> 
   <td>'Form URL' CONTAINS (for example)<br>
   <li>/ebook</li>
   <li>/whitepaper</li>
   <i>The filter values above are examples only. The actual value will be based on each organizations' URL structure.</i></td> 
  </tr>
  <tr>
   <td>Date Field / Date Type</td> 
   <td>Touchpoint Date <i>(when was the asset downloaded)</i></td> 
  </tr>
  <tr>
   <td>Date Range</td> 
   <td><i>select desired date range</i></td> 
  </tr>
  <tr>
   <td>Group / Dimension</td> 
   <td>Form URL</td> 
  </tr>
  <tr>
   <td>Optimal Models</td> 
   <td>This report is less about measuring where the Leads or Contacts are coming from with an attribution model, but more about the <i>total number of touchpoints (amount of engagement)</i>, inclusive of those after the Lead Creation Touch. With this report we're looking to understand the <i>amount of total engagement</i>. The total record count of touchpoints would reflect which assets have been downloaded the most.</td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>For any 'Leads with [!DNL Marketo Measure] Persons' report type, start by customizing the pre-built report titled '**[!DNL Marketo Measure] 101 | Leads/Contacts by Channel**'. This report is available out-of-the box and is a great [!DNL Marketo Measure] Persons based sandbox. It is pre-built and can be quickly customized for more specific reporting needs.

>[!TIP]
>
>You can use this report to gain insight into the total engagement of any marketing dimension from the Buyer Touchpoint object, not only content downloads as presented in the example. The report could instead be grouped or filtered on dimensions like 'Marketing Channel' or 'Ad Campaign Name' to best understand the total engagement from both Leads and Contacts in your database. Simply change the filters or groupings within the report to zero in on other dimensions represented by other fields from the touchpoint object.

**3.2 [!DNL Marketo Measure] Persons who have Registered for an Event (CRM only)**

_This report is only applicable if registration forms are hosted on your website(s) that [!DNL Marketo Measure] is able to track digitally._

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>What Marketing Channels are driving my event registrations?</td> 
  </tr>
  <tr>
   <td>Report Type</td> 
   <td>[!DNL Marketo Measure] Persons and Buyer Touchpoints (CRM)</td> 
  </tr>
  <tr>
   <td>Filters</td> 
   <td>'Form URL' CONTAINS (for example)<br>
   <li>/event</li>
   <i>The filter value above are examples only. The actual value will be based on each organizations' URL structure.</i></td> 
  </tr>
  <tr>
   <td>Date Field / Date Type</td> 
   <td>Touchpoint Date <i>(when the registration form was submitted)</i></td> 
  </tr>
  <tr>
   <td>Date Range</td> 
   <td><i>select desired date range</i></td> 
  </tr>
  <tr>
   <td>Group / Dimension</td> 
   <td>Form URL<br>
   Marketing Channel</td> 
  </tr>
  <tr>
   <td>Optimal Models</td> 
   <td>This report is less about measuring where the Leads or Contacts are coming from with an attribution model, but more about the <i>total number of touchpoints (number of registrations)</i>, inclusive of those after the Lead Creation Touch. With this report we're looking to gain insight into what's driving event registrations. The total record count of touchpoints per 'Marketing Channel' would reflect which channels drove the most registrations.</td> 
  </tr>
 </tbody>
</table>

The key takeaway from this report is that the Buyer Touchpoint data will also provide Marketing Channel data. While you may already have insight around the number of people who have registered for your events, this report will also provide insight into what digital Marketing Channels, Sources, and/or Campaigns are bringing people to your website to then register for the event.

>[!TIP]
>
>This same approach can be taken when looking to gain insight into webinar registrations or perhaps on-demand webinar downloads (if they are a gated asset). The only difference would be the filter value in the 'Form URL' if those forms are hosted on unique pages of your website. The goal is the same however. It answers the questions, "which of my Marketing Channels are driving the most registrations/on-demand webinar downloads.

**3.3 [!DNL Marketo Measure] Persons with Buyer Touchpoints (Touchpoint Validation)**

Considering the [!DNL Marketo Measure] Person allows us to report on all touchpoints in a single report, it is the ideal report type to use when looking to validate your data. We want to ensure we're not overlooking any touchpoints that may reveal where, for example, there is an issue in the configuration of your 'Marketing Channels' (see the support articles linked below for more information about configuring your 'Marketing Channels').

* [Online Custom Channel Setup](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md)
* [Offline Custom Channel Setup](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md)

Essentially, the touchpoint data will reflect what's been tracked by [!DNL Marketo Measure] and can be audited to ensure your configuration matches inputs based on things like: UTM parameter values, Referring Pages, or Campaign Types. If the touchpoint data doesn't match your configuration, something most likely needs to be adjusted. Beyond the 'Marketing Channel' setup, you can look at touchpoint data to determine what touchpoints may need to be [suppressed](/help/advanced-marketo-measure-features/touchpoint-settings/touchpoint-removal-and-touchpoint-suppression.md) or [segmented](/help/advanced-marketo-measure-features/segmentation/custom-segmentation.md). It is recommended to audit your touchpoint data within a '[!DNL Marketo Measure] Persons and Buyer Touchpoints' report at the end of each month or quarter if possible. This will ensure your attribution is as accurate as possible. The '[!DNL Marketo Measure] 101 | Leads/Contacts by Channel' report available out-of-the-box is a great place to start. Include the following fields if they're not already included to review some of the most crucial pieces of configuration:

* **Marketing Channel** - Path = Marketing Channel.Subchannel (values set in [!DNL Marketo Measure])
* **Touchpoint Source** = utm_source
* **Medium** = utm_medium (online touchpoints) OR CRM Campaign Type (offline touchpoints)
* **Referrer Page** (used the 'Online Channels' configuration) 
* **Landing Page - Raw** (used the 'Online Channels' configuration) also a common input for touchpoint suppression in the 'Touchpoint Settings' tab of your Settings)
* **Form URL** (a common input for touchpoint suppression in the 'Touchpoint Settings' tab of your Settings)

**BUYER ATTRIBUTION TOUCHPOINT (BAT)**

Buyer Attribution Touchpoints (BATs) represent the relevant touchpoints of all the Contacts connected to the Opportunity (either via Opportunity Contact Roles or via a shared Account ID, depending on your settings). Unlike BTs (which are mainly connected to people) BATs can be associated with revenue. As such, you'll use BATs to answer questions related to opportunities, primarily open _Opportunities/Pipeline Revenue_ and closed won _Opportunities/Deals/Revenue_. A BAT is created via a Contact's BT records as soon as an Opportunity is created under the same Account as the Contact (the BT is not converted into a BAT. The BT data is simply referenced to create an additional record - the BAT that then relates to the Opportunity).

The Buyer Attribution Touchpoint allows us to measure marketing's impact deeper in the funnel. _The depth of the funnel at which you want to measure can be represented by the various multi-touch attribution models_.

Considering BATs primary relationship is with the Opportunity, they are used to answer questions such as:

* Which of my marketing efforts have influenced the most Opportunities?
* How much new pipeline revenue can I attribute to each of my marketing channels?
* Which of my campaigns saw the greatest ROI last quarter?

The [attribution models](/help/introduction-to-marketo-measure/overview-resources/marketo-measure-attribution-models.md) providing best insight into Opportunity-based metrics are:

**W-Shaped** - The '_Pipeline Model_'. Three milestone touchpoints are included in the W-Shaped model. In this model, the FT, LC, and OC touchpoints are each attributed 30% of the attribution credit. The remaining 10% is attributed equally to any intermediary touchpoints that occur between the three milestone touchpoints.

<table> 
 <tbody>
  <tr>
   <td><img src="assets/bizible-reporting-guide-2.png"></td> 
   <td>This model essentially summarizes the journey of a new Opportunity which is typically synonymous with the generation of new Pipeline Revenue.<p>
   <p>
   When looking to measure marketing's impact on new Opportunities or new pipeline generated, the W-Shaped model is recommended.</td> 
  </tr>
 </tbody>
</table>

**Full Path** - The '_Closed Won Model_'. This model includes the four milestone touchpoints: FT, LC, OC and Closed. Each is given 22.5% of the Opportunity credit, and the remaining 10% is distributed equally among the intermediary touches.

<table> 
 <tbody>
  <tr>
   <td><img src="assets/bizible-reporting-guide-3.png"></td> 
   <td>This model essentially summarizes the journey of a closed won Deal which is typically synonymous with closed won Revenue/bookings.<p>
   <p>
   When looking to measure marketing's impact on closed won Deals or closed won Revenue, the Full Path Model is recommended.</td> 
  </tr>
 </tbody>
</table>

This model essentially summarizes the journey of a closed won Deal which is typically synonymous with closed won Revenue/bookings.

When looking to measure marketing's impact on closed won Deals or closed won Revenue, the Full Path Model is recommended.

**Custom** - [!DNL Marketo Measure] also offers a Custom Attribution model that allows users to choose which touchpoints or custom stages to include in their model. Additionally, users can control the percentage of attribution credit attributed to these touchpoints and stages. Depending on the setup of your custom model, it may be used most appropriately to measure either Opportunities and Pipeline OR, Deals and Closed Won Revenue. Keep this in mind when using it in your reporting.

>[!NOTE]
>
>The Custom Attribution Model is an additional feature not available to all customers. Contact the Adobe Account Team (your Account Manager) to learn more about how to add this feature to your account.

Commonly, marketers need to know, "where are my Opportunities coming from?". Similar to Lead level reporting, this question was historically answered with a single, one-dimensional value (Primary Campaign Source for example). However, we know that much more goes into the development of an Opportunity than a single touchpoint from a single Contact. There are typically several touchpoints from various channels and by multiple stakeholders that influence an Opportunity into creation. With [!DNL Marketo Measure], we can surface all the touchpoints from an Account to best understand where an Opportunity came from. Beyond that however, we can continue to surface any touchpoint that occurred after the Opportunity was created and up to the point the Opportunity is closed. This allows us to not only take a multi-touch approach into understanding where an Opportunity came from, but also what influenced it to close and ultimately to represent closed won revenue. This gives insight into different questions such as, "what is marketing's impact on influencing Deals to close?", "what marketing is driving closed won Revenue?" and ultimately, "which of my marketing efforts are seeing the greatest ROI?"

## RECOMMENDED REPORTS USING THE BUYER ATTRIBUTION TOUCHPOINT (BAT) {#recommended-reports-using-the-buyer-attribution-touchpoint}

**4.1 | New Opportunities by Marketing Channel**

Summarizing your Opportunities' Buyer Attribution Touchpoint data by the field 'Marketing Channel' is the highest-level view that represents what channels/tactics are influencing new Opportunities into creation. Structuring this report around a 'Date Type' = "Opportunity Created Date" ensures that we're also summarizing the report based on when the Opportunity was actually created in your CRM. The touchpoints may have been from sometime prior, but they will still relate to the Opportunities that have been created within the defined Date Range and thus receive attribution credit as they are recognized as influencing the Opportunity.

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>What <i>marketing channels</i> are influencing Opportunities into creation?</td> 
  </tr>
  <tr>
   <td>Report Type</td> 
   <td>Buyer Attribution Touchpoints with Opportunities (CRM)<br> 
   Metric: Opportunities ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Filters</td> 
   <td>
   <li>Opportunity Stage&#42; <i>(optional depending on which specific Opportunities you may want to limit to the report. You may only want to report on BATs that are still associated to only 'Open' Opportunities for example)</i></li>
   <li>Opportunity Type (it's common to filter in on certain Opportunities i.e. 'New Business' as opposed to <i>all</i> Opportunities)</li><br>
   &#42;A Segment filter for 'Opportunity Type' should be leveraged in [!DNL Marketo Measure] Discover</td> 
  </tr>
  <tr>
   <td>Date Field / Date Type</td> 
   <td>Opportunity Created Date (CRM) / Created Date (Discover)</td> 
  </tr>
  <tr>
   <td>Date Range</td> 
   <td><i>select desired date range</i></td> 
  </tr>
  <tr>
   <td>Group / Dimension</td> 
   <td>Marketing Channel</td> 
  </tr>
  <tr>
   <td>Optimal Models</td> 
   <td><strong>W-Shaped</strong><br>
   SUM the 'W-Shaped' fields in your CRM reports (Count - W-Shaped, Revenue - W-Shaped)</td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>For any 'Buyer Attribution Touchpoints with Opportunities' report type, start by customizing the pre-built report titled '[!DNL Marketo Measure] 101 | Opportunities by Channel'. This report is available out-of-the box and is a great sandbox pre-built as described in the table above and can be quickly customized for more specific reporting needs (report uses a Full Path model out-of-the-box so be sure to customize the report to include any other attribution model, in this case, the W-Shaped model).

>[!TIP]
>
>The report outlined above would also be used when looking to understand how much currency should also be attributed. When reporting at the Opportunity level using BATs, there are two key metrics that be summarized: currency (the amount of the Opportunity) and the Opportunity record itself. In the example above, we're more specifically measuring open Opportunities and new pipeline revenue.

>[!TIP]
>
>Get even more granular insight by summarizing the report with other available fields from the Buyer Attribution Touchpoint object. This is done in the same way it was at the Lead level with Buyer Touchpoints (1.2). Do this by adding additional groupings (CRM) or dimensions (Discover). Depending on the channel (which may be representative of your role), there may be additional details beyond the campaign level in which you're looking to gain more insight. Let's drill into 'Paid Search' below:

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>Which <i>keywords</i> from my Paid Search ads are generating the most pipeline revenue?
</td> 
  </tr>
  <tr>
   <td>Report Type</td> 
   <td>Buyer Attribution Touchpoints with Opportunities (CRM)<br> 
   Metric: Opportunities ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Filters</td> 
   <td>
   <li>Marketing Channel = Paid Search</li>
   <li>Opportunity Stage&#42; <i>(optional depending on which specific Opportunities you may want to limit to the report. This example is based on Pipeline Revenue which is defined in [!DNL Marketo Measure] by 'Open' Opportunities representing potential revenue/open pipeline)</i></li>
   <li>Opportunity Type (it's common to filter in on certain Opportunities i.e. 'New Business' as opposed to <i>all</i> Opportunities)</li><br>
   &#42;A Segment filter for 'Opportunity Type' should be leveraged in [!DNL Marketo Measure] Discover</td> 
  </tr>
  <tr>
   <td>Date Field / Date Type</td> 
   <td>Opportunity Created Date</td> 
  </tr>
  <tr>
   <td>Date Range</td> 
   <td><i>select desired date range</i></td> 
  </tr>
  <tr>
   <td>Group / Dimension</td> 
   <td>Keyword Text (CRM)<br> 
   Keyword (Discover)</td> 
  </tr>
  <tr>
   <td>Optimal Models</td> 
   <td><strong>W-Shaped</strong><br>
   SUM the 'W-Shaped' fields in your CRM reports (Count - W-Shaped, Revenue - W-Shaped)</td> 
  </tr>
 </tbody>
</table>

**4.2 | Deals by Marketing Channel**

This report would essentially be the same as the first Buyer Attribution Touchpoint example (4.1) except the metric has now changed from open Opportunities to closed won Deals. The metric should always be what informs which attribution model to use. Considering we're now looking at closed won Deals and their related BATs, we should use a model that represents the entire buyer's journey (Deal). This ensures any marketing touch track during the buyer's journey receives attribution credit:

<table> 
 <tbody>
  <tr>
   <td>Question</td> 
   <td>What <i>marketing channels</i> are influencing Deals to close?</td> 
  </tr>
  <tr>
   <td>Report Type</td> 
   <td>Buyer Attribution Touchpoints with Opportunities (CRM)<br> 
   Metric: Deals ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Filters</td> 
   <td>
   <li>Opportunity Stage (<i>only Closed Won Opportunities should be in report</i>) OR,</li>
   <li>Opportunity Won = True</li>
   <li>Opportunity Type (it's common to filter in on certain Opportunities i.e. 'New Business' as opposed to all Opportunities)<br>
   </td> 
  </tr>
  <tr>
   <td>Date Field / Date Type</td> 
   <td>Opportunity Closed Date</td> 
  </tr>
  <tr>
   <td>Date Range</td> 
   <td><i>select desired date range</i></td> 
  </tr>
  <tr>
   <td>Group / Dimension</td> 
   <td>Marketing Channel</td> 
  </tr>
  <tr>
   <td>Optimal Models</td> 
   <td><strong>Full Path</strong><br>
   SUM the 'Full Path' fields in your CRM reports (Count - Full Path, Revenue - Full Path)</td> 
  </tr>
 </tbody>
</table>

**REMINDER**: It's crucial to remember to filter for the specific Opportunities you want to include in BAT based reporting, especially when it comes 'Open Opportunities and Pipeline Revenue' vs. 'Deals and Closed Won Revenue'. This is typically done via an 'Opportunity Stage' filter (the 'Opportunity Won' = true/false filter can also be very helpful here).

**5. ROI ([!DNL Marketo Measure] Discover only)**

The [!DNL Marketo Measure] Discover dashboards provide a high-level view of your Marketing Performance using [!DNL Marketo Measure] attribution data. These aggregated dashboards provide key marketing spend and ROI data which is not available in your CRM reporting. This pre-built environment allows you to view your marketing performance in alignment with your ROI data allowing you to make actionable decisions in regards to your marketing.

>[!TIP]
>
>Whenever you have a question related to ROI, Spend or Cost, [!DNL Marketo Measure] Discover will be the best place for reporting!

The [!DNL Marketo Measure] Discover dashboards are comprised of Buyer Touchpoint and Buyer Attribution Touchpoints data as well as key CRM data. The main difference between CRM reporting and reporting in [!DNL Marketo Measure] Discover is that the touchpoint data in Discover is presented more in an 'aggregated' fashion, and summarized by dimension (Marketing Channel, Campaign, etc.) as opposed to individual touchpoint records which can then be summarized. [!DNL Marketo Measure] Discover is used to understand at a high level which of your efforts are making the greatest impact on Leads, Opps, Deals and how much revenue should be attributed to them. Once we have the attributed revenue calculated via the various attribution models (Full Path is recommended for attributing closed won revenue/bookings), we can then measure it against how much was spent in the same dimension (Marketing Channel, Subchannel, or Campaign). This then gives us the **ROI**.

>[!TIP]
>
>One of the most important things to remember when reporting in Discover is which Data Type you're using to filter. Date Type will dictate which data set [!DNL Marketo Measure] is using in the various tiles.

* **Touchpoint Date**: Displays the related data that had a 'Touchpoint Date' in the timeframe specified
* **Created Date**: Displays the related data that had a 'Created Date' in the timeframe specified
* **Closed Date**: Displays the related data that had a 'Close Date' in the timeframe specified

When reporting on ROI in [!DNL Marketo Measure] Discover, it is recommended to use a 'Date Type' = "Touchpoint Date". In order to determine the return of each dollar invested, we need to ensure the revenue is attributed back to the date in which the investment was made. 'Date Type' = "Touchpoint Date" ensures the reports are structured in this way as opposed to when the Opportunity was created (Create Date) or closed (Closed Date). Let's take a closer look:

The filters highlighted below are crucial to an ROI focused report in [!DNL Marketo Measure] (most likely, you'll be setting these filters in the 'Overview', 'CMO', or 'ROI' boards):

**5.1 | ROI in the 'Overview' Board**

![](assets/bizible-reporting-guide-4.png)

The 'Date' range not only sets the cohort of touchpoints (by Touchpoint Date) that are receiving attribution, but also it defines the range the 'Spend' tile or columns represent.
[!DNL Marketo Measure] simply looks at the 'Date' range to determine how much was spent either in total, or at the Marketing Channel, Subchannel, or Campaign levels See below:

![](assets/bizible-reporting-guide-5.png)

The screenshot above shows the Marketing Spend data over the past 3 complete months. In this example, $12,970 was spent across all channels. This number is comprised of the Marketing Spend data [!DNL Marketo Measure] has from integrations with any of your connected ads accounts (Google AdWords, Bing Ads, Facebook Ads, LinkedIn, DoubleClick) and any additional Marketing Spend that has been uploaded within your account, or pulled automatically from a Campaign records in your CRM. The example also shows how much closed won 'Revenue' can also be attributed to touchpoints that happened during the same date range (green boxes). This is how ROI is calculated: revenue attributed to touchpoints that were sourced from investment in the same date range:

![](assets/bizible-reporting-guide-6.png)

**REMINDER**: [!DNL Marketo Measure] defines 'Revenue' as closed won Revenue or Bookings and defines 'Pipeline Revenue' as _open/potential revenue from open Opportunities_.

Another important takeaway from the ROI report above is the 'Pipeline Revenue' represented within the red box. This means that from the $12,970 USD invested over the past 3 complete months, we're currently attributing $705,199 of closed won 'Revenue' but we're also attributing $6,905,532 of open, potential revenue ('Pipeline Revenue) to touchpoints created from the same investment! What we would expect to see is a portion of the 'Pipeline Revenue' close over time, feeding the 'Revenue' number, and thus, the ROI number would increase over time. The 'Spend' number is fixed because we can't go back in time to spend more in the last 3 complete months. This is the importance of using a 'Date Type' of "Touchpoint Date" within any ROI reporting: It defines the amount (**I**)nvested, and ensures the amount of (**R**)evenue attributed is attributed back to the same touchpoints that were sourced from the investment (for every dollar spent, how much was made?).

>[!TIP]
>
>Filter in on Marketing Channels, Subchannels, and/or Campaigns in which you know the Marketing Spend data is complete and accurate. The example above is for all Marketing Channels, but if some Channels don't have the related Marketing Spend data uploaded, the ROI reporting could be inaccurate. See the example below, this time in the 'ROI' board that is focused on the Campaigns within the Marketing Channel of "Paid Search", a Channel with very granular Marketing Spend data via the integrations.

![](assets/bizible-reporting-guide-7.png)
