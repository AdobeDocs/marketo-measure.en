---
unique-page-id: 18874564
description: Definition of [!DNL Marketo Measure] Web Sessions - [!DNL Marketo Measure]
title: Definition of [!DNL Marketo Measure] Web Sessions
exl-id: ddf4f19d-2024-413a-b0ae-4efd468c24de
feature: Tracking
---
# Definition of [!DNL Marketo Measure] Web Sessions {#definition-of-marketo-measure-web-sessions}

Learn how [!DNL Marketo Measure] defines web sessions.

A **web session** refers to an individual's interactions with your website during a certain amount of time. The session begins when a user lands on your website.

For example, Haley visits adobe.com. Her visit to the site begins a session. When Haley leaves the site, by closing the tab/web browser or navigating away from the site, the session ends.

One user cannot open multiple sessions at the same time. If Haley opens [!DNL adobe.com] in ten separate tabs, only one session has been created in relation to her visit to the website.

## How does [!DNL Marketo Measure] define a new session? {#how-does-marketo-measure-define-a-new-session}

There are a few things that determine when a session ends, and when a new session begins. The two main ways [!DNL Marketo Measure] sessions can end are:

* **Time-based expiry**
* **Channel-based expiry**

## Time-based expiration {#time-based-expiration}

### Legacy behavior {#legacy-behavior}

**How long does a session last?**

[!UICONTROL Marketo Measure] sessions will end after 30 minutes of inactivity on the website. For example:

When Haley visits adobe.com, a session begins. She explores the website for a few minutes and then steps away from her computer, but leaves the website open. After 30 minutes of inactivity, the session ends.

Currently, [!UICONTROL Marketo Measure] only considers page navigation and form submissions as activity. Scrolling through the web page or hovering over an element on the page is not considered activity. So if Haley visits adobe.com to read a blog post, and it takes her one hour to read, her web session will still end after 30 minutes even if she is scrolling through the content on the page.

### New behavior {#new-behavior}

For new users, this will be the default behavior.

Existing users can adopt the new behavior by turning on the toggle under **Settings** > **Everytouch Attribution** > **Session Channel Carryover**. Once activated, this setting cannot be reversed.

When a new session is created after 30 minutes of inactivity, the previous session's channel will carry over if the new session starts within seven days. This carryover applies only to Direct visits (either no referrer or internal referrers). If the inactivity exceeds seven days, the channel for the new session will default to Direct/Other. For example, if Haley visits landingpage.com from Google, is inactive for over 30 minutes, and returns within seven days, the new session will retain the Google channel. However, if the same user revisits the page through a different channel, the non-Direct channel will not be overridden by the previous Google channel.

Only the channel will carry over, excluding campaign or referrer details. This is because channel classification is handled by Marketo Measure, while other data points are collected separately.

**Social Sign-In**

When a visitor uses social sign-in via Google, Microsoft, or Apple, the session will be merged into one continuous session. For example, if a visitor lands on a page from LinkedIn, completes a Google social sign-in, and reaches a thank-you page, it will all count as a single session. Without the session channel carryover toggle on, the social sign-in would create separate sessions due to the external referrer.

## Channel-based expiration {#channel-based-expiration}

[!DNL Marketo Measure] begins a new session anytime a user comes to your website from a different digital marketing channel, or an external website. This includes:

* A referral website
* Social channels ([!DNL Facebook], [!DNL LinkedIn], and so on)
* Paid or Organic Search Channels ([!DNL Google/Bing])

**Referral Websites and Social Channels**

Anytime a visitor comes to your website from a referring website or a social channel, a new session begins.

Say that Haley is on LinkedIn, clicks a [!DNL Marketo Measure] post and is redirected to the Adobe website. Then, while scrolling through [!DNL Facebook], Haley sees another [!DNL Marketo Measure] post. When she clicks this post and is redirected to the Adobe site, this causes the first web session that is related to [!DNL LinkedIn] to end, and a new session related to [!DNL Facebook] begins.

**Paid or Organic Search Channels**

New sessions begin anytime that a user comes to your site through paid or organic search channels. If Haley comes to the Adobe website through organic search, and then immediately visits your website through a paid ad on Google, two separate sessions are created.

**Web Direct Traffic**

If a visitor comes to your website by typing your website's URL into the address bar, it does not always cause a new session to begin.

If Haley's first web session begins as the result of a visit from a referral site, social channel, or paid/organic search channel and then she visits the site via web direct, this would not cause a new session to begin.

_However_, if Haley's first web session originated from Web Direct, and then she visits the website via _an external/referral site_, the first session ends and a new session is opened related to the external/referral site.

## Google Analytics Sessions {#google-analytics-sessions}

There are some similarities to how [!DNL Marketo Measure] and Google Analytics defines sessions. For more information on how Google Analytics defines sessions, visit: [https://support.google.com/analytics/answer/2731565?hl=en](https://support.google.com/analytics/answer/2731565?hl=en){target="_blank"}
