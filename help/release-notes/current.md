---
description: Current Release Notes - [!DNL Marketo Measure]
title: Current Release Notes
exl-id: e93ff03e-ea21-41f4-abb8-32313ee74c0c
feature: Release Notes
---
# Release Notes: 2024 {#release-notes-2024}

See below for all the new and updated features for our 2024 releases.

## Q4 Release {#q4-release}

### Enhanced Segment Rules

You can now create segments using Campaign and Campaign Member fields, in addition to Touchpoint and Contact fields. This enhancement empowers you to analyze and dissect your data more effectively in Discover.

![Segment Rules for Members](assets/campaign-member.png)

### Update: Error Handling Setting for CRM Exports

We've listened to your feedback regarding the job-halting approach and are introducing a new feature in the User Interface. Starting today, you can choose whether export jobs should pause when errors occur. Use the new toggle in **My Account** > **Settings** → **CRM** → **General**. This switch is on by default to enhance data integrity and visibility. However, if you prefer not to use this feature, you can turn it off in the UI, and the export jobs will resume. This update is designed to enhance the reliability of your data management processes while giving you greater control. 

#### Key Dates and Phased Rollout

Immediate Toggle Availability: The toggle is now live in the UI and is enabled by default to prevent data from being skipped during export jobs. If you prefer export jobs to continue running despite encountering errors, disable the toggle.

Job Pausing Activation on October 1st: Beginning October 1st,2024, if the toggle is active and a record-level error is encountered during an export job, the job pauses to ensure no data is lost. These errors are usually due to missing permissions, improperly applied custom validation rules, or issues in workflows/triggers. You will receive notifications regarding the issue, and once it has been corrected, the export job will resume from the point of interruption. If you opt out of job pausing, you will still receive notifications of issues, and when they have been corrected, the skipped records are automatically re-exported.

#### Why This Matters

**Enhanced Data Integrity and Future-proofing Your Integration:** By pausing the job at the first sign of an issue, we prevent data loss and ensure accuracy. This enables swift error resolution, leading to improved data export quality and overall system reliability.

**Immediate Visibility:** Through pulse notifications, you will receive timely alerts for permission errors, allowing for prompt responses and minimizing potential impacts on your operations.

#### Supporting Your Transition

To help you adapt to this change, we have created documentation on the new feature and clear error descriptions with comprehensive troubleshooting steps.

* New documentation: [Error Handling Setting for CRM Exports](/help/configuration-and-setup/marketo-measure-and-salesforce/crm-error-handling.md)
* [Error Notifications](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md)

## Q3 Release {#q3-release}

<p>

**Reminder: Salesforce Field Deprecations - June 14**

As announced last year, we will be [phasing out our export jobs to Lead/Contact objects](https://nation.marketo.com/t5/employee-blogs/marketo-measure-salesforce-lead-and-contact-field-deprecation-06/ba-p/350179){target="_blank"} to simplify our integration and eliminate the need to export to Salesforce standard objects. You can obtain the same data from your Touchpoint objects by following the steps [documented here](/help/release-notes/previous-releases/2023.md#deprecations){target="_blank"}. We will also be sharing documentation on creating workflows to add this data to the Lead/Contact object. The deprecation will take effect on June 14, 2024.

This change will bring two key benefits:

* **Reduced Salesforce API Costs**: Customers can expect to reduce their Salesforce API costs by around 10%.
* **Streamlined Integration**: The highest number of errors in our export jobs are related to these processes. Removing them will significantly streamline our integration.

**Attributed Opportunity Dashboard**

We're excited to introduce the new [Attributed Opportunity Dashboard](/help/marketo-measure-discover-ui/dashboards/attributed-opportunity-dashboard.md){target="_blank"}, designed to give you a comprehensive view of how your marketing efforts contribute to both nascent and mature pipeline opportunities. This dashboard allows you to delve into the details of every open and closed opportunity attributable to your strategies, with the flexibility to filter by opportunity stage. It provides insights into which channels, subchannels, or campaigns rank highest in terms of attributed opportunity amount, and displays the total attributed opportunity amount along with the count of attributed open and closed opportunities.

**Marketo Engage Cookie Sync for Marketo Measure Ultimate**

Marketo Engage Cookie Sync is now available for Marketo Measure Ultimate. To use this feature:

1. On the AEP Schemas page, edit the B2B Person schema and add the field group "Marketo Engage Person Details."
1. When ingesting the data to MMU, map the Cookie ID field from the field group to the Cookies field from Marketo Engage.

**Boomerang Stages enabled for Tier 2 Customers**

Previously only available to Tier 3 customers, the Boomerang Stage feature is also be available to all Tier 2 customers beginning June 13, 2024. For more detailed information on this feature, please refer to the documentation below.

* [Boomerang Stages and Touchpoints](/help/advanced-marketo-measure-features/boomerang/boomerang-stages-and-touchpoints.md){target="_blank"}
* [Setting up Boomerang Stages](/help/advanced-marketo-measure-features/boomerang/setting-up-boomerang-stages.md){target="_blank"}
* [Boomerang Stage Scenarios](/help/advanced-marketo-measure-features/boomerang/boomerang-stage-scenarios.md){target="_blank"}

<p>

## Q2 Release {#q2-release}

<p>

**Deprecation of Marketo Measure Features in Response to Third-Party Cookie Phase-Out**

In response to growing privacy concerns, third-party cookies are being phased out, with Google Chrome's Q3 2024 deadline signaling their end. Marketo Measure will deprecate certain features dependent on third-party cookies, specifically Cross-Domain Tracking and View-through Attribution, which rely on the Google/DoubleClick impression cookie. This change will not affect other Marketo Measure functionalities or the use of first-party cookies. Following Google's timeline, these functionalities are expected to be deprecated by June 1, though data collected prior to this date will still be accessible to customers.

* [Adapting to Third-Party Cookie Deprecation in Marketo Measure](https://nation.marketo.com/t5/employee-blogs/adapting-to-third-party-cookie-deprecation-in-marketo-measure/ba-p/345110){target="_blank"}
* [Marketo Measure Cookies](/help/marketo-measure-tracking/setting-up-tracking/marketo-measure-cookies.md){target="_blank"}

**Phased Rollout of Our Enhanced Error Handling**

We are introducing a phased rollout of enhanced error handling for export jobs, starting with immediate in-app pulse notifications for permission errors, and transitioning to a new approach where export jobs will pause at the point of error. This change aims to improve data integrity and visibility, ensuring smoother and more reliable data management processes for our users. To ensure a smooth transition and minimal disruption to your operations, we are implementing these changes in two phases:

* Immediate Availability of Pulse Notifications: You'll receive in-app pulse notifications for permission errors during export jobs. This will not interrupt your exports, but will help you learn about the errors without affecting your current jobs.
* Implementation of Job Pausing on April 25: **POSTPONED** - After considering feedback from Marketo Measure users, we have decided to postpone the implementation of pausing export jobs at the point of error, originally scheduled for April 25. We recognize that halting jobs may not be the most effective approach. We are committed to finding a better solution that maintains data integrity and minimizes disruption. We will hold off on making any changes to our current system until we can ensure a solution that aligns more closely with the needs of our users.

_Why This Matters_

Enhanced Data Integrity and Future-proofing Your Integration: We stop the job at the first sign of trouble to prevent data loss and ensure accuracy. This allows for quick issue resolution, improving data export quality and system reliability.

Immediate Visibility: The introduction of pulse notifications allows for prompt response to permission errors, preventing potential impacts on operations.

_Supporting Your Transition_

To help you adapt to this change, [we have created documentation](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"} with clear error descriptions and comprehensive troubleshooting steps.

<br>

**Action Required for LinkedIn Integration**

LinkedIn recently released an updated version of their Lead Sync API. Please re-authenticate the LinkedIn connection in your Marketo Measure instance by May 20 to avoid any interruptions. 
 