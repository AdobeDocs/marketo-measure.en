---
description: "What is Adobe Marketo Measure"
title: What is Adobe Marketo Measure?
hide: yes
hidefromtoc: yes
---
# What is Adobe Marketo Measure? {#what-is-adobe-marketo-measure}

Adobe Marketo Measure (formerly known as Bizible) is a leading multi-touch attribution platform.

It consolidates data from disparate data sources (CRM, marketing automation, website, etc.). With that data in one location, it creates a time series of events (the aforementioned touchpoints) for each person, identified by their unique email address.

These touchpoints are then related to opportunities through either Account-based or Opportunity Contact Role-based methodologies, so that we can attribution Opportunities back to the multiple different touchpoints that played a role in each Opportunity's journey.

Using various rule-based and position-based attribution models (which we'll delve into much deeper later on), each touchpoint related to an Opportunity is given a weight, which then assigns a dollar value to each touchpoint.

As each touchpoint is classified channel, subchannel, campaign and other defined segments, it allows you to then figure out which marketing activities are most heavily correlated with opportunities and wins.

Let's talk more about how it does this
How Marketo Measure Works
Marketo Measure integrates with many of the tools in your tech stack. It also integrates directly with the ad platforms listed below.

●    Google Ads
●    Bing Ads
●    Facebook/Meta
●    LinkedIn

These integrations help to resolve paid media campaign traffic to the exact ad campaign from these platforms, when autotagging is turned on.

These integrations also automatically ingest all of the ad campaign and ad spend from these platforms, directly into the Marketo Measure platform.

Note: These integrations can't bring in touchpoints within the paid media walled gardens with the exception of the LinkedIn Lead Gen form integration. This means that you are not getting touchpoints for things like comments, shares and likes… or any other interaction that takes place solely inside these platforms.
Marketo Measure also has a javascript that is placed onto your website that creates touchpoints from web interactions. These touchpoints are then categorized into channels and subchannels based on rules that utilize UTM parameters, campaign info, landing pages and/or referring URLs. More on this functionality later on.

It also integrates with your CRM to bring in Opportunities, Accounts, Contacts, Leads, Opportunity Contact Roles, Campaigns, Campaign Members and Activities (Tasks and Events). This integration allows you to set up rules that create touchpoints from Campaign membership as well as Activities logged against a person (phone calls, emails, meetings, etc.). Again, more on these settings later on.

Marketo Measure can also integrate directly with Marketo Engage. This integration allows you to create rules that create touchpoints from Program membership as well as the Marketo Activity Log. We'll dive deeper into this functionality also.

With all of that data, you're now creating touchpoints from a plethora of different sources of data. And these touchpoints are then assigned a Channel and, in some cases, a Subchannel. This categorizes the touchpoints based on where they came from.

Touchpoints are also assigned a position. This position is based on where the touchpoint is in the buying process and journey. There are four standard positions, and you have the ability to create custom positions. The standard positions are as follows…

●    First Touch (FT) - The very first touchpoint (could be anonymous)
●    Lead Creation (LC) - The first touchpoint where we capture an email address
●    Opportunity Creation (OC) - The last touch prior to the creation of an Opportunity
●    Closed - The last touch prior to the closure (closed won or closed lost) of an Opportunity

The positions then dictate the weight, based on the different attribution models.

Opportunities then have their value divvied up amongst all of the touchpoints that influenced them, like pie pieces, to give each touchpoint a value.

For example, if a touchpoint has a weight of 30% and it's related to an Opportunity with a value of $10,000, then that touchpoint is valued at $3,000.
