---
description: Current Release Notes - [!DNL Marketo Measure]
title: Current Release Notes
exl-id: e93ff03e-ea21-41f4-abb8-32313ee74c0c
feature: Release Notes
---
# Release Notes: 2024 {#release-notes-2024}

See below for all the new and updated features for our 2024 releases.

## Q2 Release {#q2-release}

<p>

**Deprecation of Marketo Measure Features in Response to Third-Party Cookie Phase-Out**

In response to growing privacy concerns, third-party cookies are being phased out, with Google Chrome's Q3 2024 deadline signaling their end. Marketo Measure will deprecate certain features dependent on third-party cookies, specifically Cross-Domain Tracking and View-through Attribution, which rely on the Google/DoubleClick impression cookie. This change will not affect other Marketo Measure functionalities or the use of first-party cookies. Following Google's timeline, these functionalities are expected to be deprecated by June 1, though data collected prior to this date will still be accessible to customers.

* [Adapting to Third-Party Cookie Deprecation in Marketo Measure](https://nation.marketo.com/t5/employee-blogs/adapting-to-third-party-cookie-deprecation-in-marketo-measure/ba-p/345110){target="_blank"}
* [Marketo Measure Cookies](/help/marketo-measure-tracking/setting-up-tracking/marketo-measure-cookies.md){target="_blank"}

**Phased Rollout of Our Enhanced Error Handling**

We are introducing a phased rollout of enhanced error handling for export jobs, starting with immediate in-app pulse notifications for permission errors, and transitioning on April 25 to a new approach where export jobs will pause at the point of error. This change aims to improve data integrity and visibility, ensuring smoother and more reliable data management processes for our users. To ensure a smooth transition and minimal disruption to your operations, we are implementing these changes in two phases:

* Immediate Availability of Pulse Notifications: You'll receive in-app pulse notifications for permission errors during export jobs. This will not interrupt your exports, but will help you learn about the errors without affecting your current jobs.
* Implementation of Job Pausing on April 25: Starting April 25, if our system encounters a permission error during an export job, it will pause the job to ensure no data is skipped. You'll be notified of any issues, and once the permissions are corrected, the export job will resume seamlessly from where it left off.

_Why This Matters_

Enhanced Data Integrity and Future-proofing Your Integration: We stop the job at the first sign of trouble to prevent data loss and ensure accuracy. This allows for quick issue resolution, improving data export quality and system reliability.

Immediate Visibility: The introduction of pulse notifications allows for prompt response to permission errors, preventing potential impacts on operations.

_Supporting Your Transition_

To help you adapt to this change, [we have created documentation](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"} with clear error descriptions and comprehensive troubleshooting steps.

**Action Required for LinkedIn Integration**

LinkedIn recently released an updated version of their Lead Sync API. Please re-authenticate the LinkedIn connection in your Marketo Measure instance by May 20 to avoid any interruptions. 
 