---
unique-page-id: 18874535
description: Transitioning to Marketo Measure from Full Circle - Marketo Measure - Product Documentation
title: Transitioning to Marketo Measure from Full Circle
exl-id: fd471771-33e2-413a-b155-02ba6e32e10c
---
# Transitioning to Marketo Measure from Full Circle {#transitioning-to-marketo-measure-from-full-circle}

Making the move from Full Circle to Marketo Measure? You’re not alone. Here are the biggest considerations to keep in mind and the lessons we’ve learned from other customers who’ve made the switch.

## Campaign-Based Tracking vs. Multi-Source Tracking {#campaign-based-tracking-vs-multi-source-tracking}

All interactions in Full Circle are tracked through CRM campaign membership. With Marketo Measure, the purchasing journey is compiled through a combination of our JavaScript, CRM campaign membership, and CRM activity records. Making the mental shift away from “all interaction must be tracked in a CRM campaign in order for our attribution reporting to function” to “only this subset of interactions needs to be tracked in a CRM campaign for our attribution reporting to function” can be tricky.

Generally speaking, here’s how Marketo Measure creates touchpoint records for the major types of interactions:

* Form fills on your site(s): Marketo Measure Javascript
* Page views on your site(s): Created by Marketo Measure Javascript only if this page view drove a designated CRM milestone (such as Lead or Opportunity Creation)
* Offline interactions such as conferences or tradeshows: CRM campaign membership
* Digital interactions that happen anywhere on the internet that isn’t your site (such as a webinar hosted on a third-party site that generates a list upload): CRM campaign membership
* Interactions with your Sales team: CRM Activity records

If you’re comfortable with your CRM campaign management and prefer to keep existing processes in place, that’s fine. It doesn’t hurt Marketo Measure to continue tracking all interactions in CRM campaigns. You can design logic that only creates touchpoints from a desired subset of campaigns to avoid touchpoint duplication.

## Visibility vs. Attribution {#visibility-vs-attribution}

With most Full Circle setups, you see every single interaction a person has with your marketing or sales efforts. Page views, repeated page visits, membership in duplicate and triplicate campaigns—Full Circle surfaces all of those. If you view a page 300 times, Full Circle creates 300 duplicate campaigns and gives you a membership in each of them. Marketo Measure does not, and that was a conscious design decision on our part.

Marketo Measure’s goal is to provide you with an attribution story that surfaces meaningful interactions and distributes weight among the most impactful touchpoints appropriately. For example, the Marketo Measure framework won’t surface page views (without form fills) as routine touchpoints. A standalone page view isn’t likely to have an impact on driving a purchasing journey forward, but we will create a touchpoint if it’s the most recent interaction before a designated CRM milestone (such as Lead or Opportunity Creation). We don’t want to show you everything. We want to show you the stuff that matters, from an attribution standpoint.

Work with your Marketo Measure rep to set appropriate expectations around what data will no longer be available to your team.

## Pre-Marketo Measure Data {#pre-marketo-measure-data}

Marketo Measure’s standard recommendation is to start reporting and data gathering from the day you deployed the Marketo Measure JavaScript forward, and that goes double for former Full Circle customers. Think about the two sections above: You’re used to seeing a higher quantity of data, and you’re used to all of that data coming from CRM campaign membership. If you choose to include some or all of that data from prior to your Marketo Measure implementation, you won’t be comparing apples to apples across the JavaScript implementation date.

That said, we certainly understand that many customers need this historic data; especially if you have a longer sales cycle (greater than 90 days), you may want to give Marketo Measure visibility into pre-Marketo Measure data. Discuss this carefully with your Marketo Measure rep, and always keep in mind that skew across the implementation date can lead to the appearance of improvements or declines in channel performance or engagement, as well as other potentially incorrect inferences.

## In Summary {#in-summary}

You’re in good company, and we’ve helped numerous other customers handle these changes. Work with your Marketo Measure rep to understand the impacts above, as well as any other concerns you may have.
