---
unique-page-id: 18874648
description: Difference between a Google Analytics Conversion and a Buyer Touchpoint - [!DNL Marketo Measure]
title: Difference between a Google Analytics Conversion and a Buyer Touchpoint
exl-id: d09d963c-3207-467c-852a-d1edd49511fa
feature: Touchpoints
---
# Difference between a Google Analytics Conversion and a Buyer Touchpoint {#difference-between-a-google-analytics-conversion-and-a-buyer-touchpoint}

Learn what a [!DNL Google Analytics (GA)] goal is and how it differentiates from a Buyer Touchpoint.

**What are Google Analytics' Conversions?**

[!UICONTROL Google Analytics] conversions are determined by how a marketer or a web developer codes 'goal' completions on a particular website. Goals, according to Google, could be thought of as "making a purchase (for an ecommerce site), completing a game level (for a mobile gaming app), or submitting a contact information form (for a marketing or lead generation site)." Most of the time, marketers see goals/conversions as someone filling out an informational form.

However, goals can't be coded to manage specific behavior. Rather, there are Goal Types that a web developer can configure. Below are some of those examples:

<table> 
 <colgroup> 
  <col> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <td><strong>Goal Type</strong></td> 
   <td><p><strong>Description</strong></p></td> 
   <td><strong>Example</strong></td> 
  </tr> 
  <tr> 
   <td><p>Destination</p></td> 
   <td>A specific location loads</td> 
   <td><em>Thank you for registering!</em> web page or app screen</td> 
  </tr> 
  <tr> 
   <td>Duration</td> 
   <td>Sessions that last a specific amount of time or longer</td> 
   <td>10 minutes or longer spent on a support site</td> 
  </tr> 
  <tr> 
   <td>Pages/Screens per session</td> 
   <td>A user views a specific number of pages or screens</td> 
   <td>5 pages or screens have been loaded</td> 
  </tr> 
  <tr> 
   <td>Event</td> 
   <td>An action defined as an Event is triggered</td> 
   <td>Social recommendation, video play, ad click</td> 
  </tr> 
 </tbody> 
</table>

Most marketers configure their conversions as "Destination Goals," meaning that they usually create a thank you page after a form to consider that a formal conversion.

What this means, is that Google considers Thank You page views as a conversion. From a Google Analytics standpoint, this is a realization most marketers are OK with.

However, Buyer Touchpoints act differently.

**How do Buyer Touchpoints differ?**

[!DNL Marketo Measure] JavaScript tracks session data and form submissions on all forms of a particular site. There's no need to code goals from a [!DNL Marketo Measure] standpoint. This process is automatic. For form submissions, [!DNL Marketo Measure] reports a form completion every time an anonymous user fills out information fields on a particular form and also clicks the form submission button. [!DNL Marketo Measure] doesn't need a thank you page to record the form submission.

[!DNL Marketo Measure] creates a form touchpoint when:

* A lead/contact that is associated to those conversions appear in your CRM.
* The [!DNL Marketo Measure] JS is present on the web pages containing the form.
* A form is submitted within a 30-min session.

[!DNL Marketo Measure] ignores Destination Google Analytic conversions when:

* A bot submits forms on a website (these bots usually don't make it into a client's CRM).
* A user submits more forms after their first form submission. [!DNL Marketo Measure] will only push the first conversion from that session.
* The user clicks the form submission multiple times. [!DNL Marketo Measure] will only consider the first form submission.
* The user reloads the thank you page multiple times.
* The user is using any Ad Blocking tools.

As you can see that there are fundamental differences between what GA and [!DNL Marketo Measure] consider a conversion to be. Therefore, it is likely that the number of conversions and the number of form Touchpoints differ.
