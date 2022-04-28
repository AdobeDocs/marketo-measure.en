---
unique-page-id: 18874564
description: Definition of Marketo Measure Web Sessions - Marketo Measure - Product Documentation
title: Definition of Marketo Measure Web Sessions
exl-id: ddf4f19d-2024-413a-b0ae-4efd468c24de
---
# Definition of Marketo Measure Web Sessions {#definition-of-marketo-measure-web-sessions}

Learn how Marketo Measure defines web sessions.

A **web session** refers to an individual's interactions with your website during a certain amount of time. The session begins when a user lands on your website.

For example, Haley visits adobe.com. Her visit to the site begins a session. When Haley leaves the site, by closing the tab/web browser or navigating away from the site, the session ends.

One user cannot open multiple sessions at the same time. If Haley opens adobe.com in 10 separate tabs, only one session has been created in relation to her visit to the website.

## How does Marketo Measure define a new session? {#how-does-marketo-measure-define-a-new-session}

There are a few things that determine when a session ends, and when a new session begins. The two main ways Marketo Measure sessions can end are:

* **Time-based expiry**
* **Channel-based expiry**

## Time-based expiration {#time-based-expiration}

**How long does a session last?**

Marketo Measure sessions will end after 30 minutes of inactivity on the website. For example:

When Haley visits adobe.com, a session begins. She explores the website for a few minutes and then steps away from her computer, but leaves the website open. After 30 minutes of inactivity the session will end.

Currently, Marketo Measure only considers page navigation and form submissions as activity. Scrolling through the web page or hovering over an element on the page is not considered activity. So if Haley visits adobe.com to read a blog post, and it takes her one hour to read, her web session will still end after 30 minutes even if she is scrolling through the content on the page.

## Channel-based expiration {#channel-based-expiration}

Marketo Measure will begin a new session any time a user comes to your website from a different digital marketing channel, or an external website. This includes:

* A referral website
* Social channels (Facebook, LinkedIn, etc.)
* Paid or Organic Search Channels (Google/Bing)

**Referral Websites and Social Channels**

Any time a visitor comes to your website from a referring website or a social channel, a new session will begin.

Say Haley is on LinkedIn, clicks on a Marketo Measure post and is redirected to the Adobe website. Then, while scrolling through Facebook, Haley sees another Marketo Measure post. When she clicks on this post and is redirected to the Adobe site, this causes the first web session that is related to LinkedIn to end, and a new session related to Facebook begins.

**Paid or Organic Search Channels**

New sessions will begin any time a user comes to your site through paid or organic search channels. If Haley comes to the Adobe website through organic search, and then immediately visits your website through a paid ad on Google, two separate sessions will be created.

**Web Direct Traffic**

If a visitor comes to your website by typing your website’s URL into the address bar, it does not always cause a new session to begin.

If Haley’s first web session begins as the result of a visit from a referral site, social channel, or paid/organic search channel and then she visits the site via web direct, this would not cause a new session to begin.

_However_, if Haley’s first web session originated from Web Direct, and then she visits the website via _an external/referral site_, the first session will end and a new session is opened related to the external/referral site.

## Google Analytics Sessions {#google-analytics-sessions}

There are some similarities to how Marketo Measure and Google Analytics defines sessions. For more information on how Google Analytics defines sessions, please visit: [https://support.google.com/analytics/answer/2731565?hl=en](http://support.google.com/analytics/answer/2731565?hl=en)
