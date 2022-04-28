---
description: Domain Management - Marketo Measure - Product Documentation
title: Domain Management
exl-id: 4db287a0-0267-463c-a359-266b41f15c59
---
# Domain Management {#domain-management}

For IMS-enabled tenants running Marketo Measure in the Unified Shell, Marketo Measure provides an interface that allows users to manage their own list of domains. Marketo Measure users must first verify any domains they wish to track in the [Adobe Admin Console](https://adminconsole.adobe.com/). Once domains are verified in the Admin Console, users can manage if Marketo Measure uses these domains for tracking website traffic.

## Adding Domains in Admin Console {#adding-domains-in-admin-console}

IMS users with access to the Adobe Admin Console can add and validate domains that they own. Domain validation involves adding a DNS record for each domain and subsequently allowing the Admin Console to verify that record.

   ![](assets/domain-management-1.png)

Instructions for adding domains can be found in the [Admin Console documentation](https://helpx.adobe.com/enterprise/using/set-up-identity.html#setup-domains). Once a domain is added, it must be [linked to a directory](https://helpx.adobe.com/enterprise/using/set-up-identity.html#link-domains-to-directories).

## Managing Domains in Marketo Measure {#managing-domains-in-marketo-measure}

Once a domain is added in the Admin Console, Marketo Measure will sync this record into our database on a regular basis. This synchronization happens nightly, and also every time a user visits the **Domains** page in the Marketo Measure UI. By default, any records that Marketo Measure imports will be disabled, and the tenant must manually enable each domain.

   ![](assets/domain-management-2.png)

On the **Integration** > **Domains** page, the user will see all domains that they have registered in the Admin Console, along with their status. Each domain can be enabled or disabled. If a domain is enabled, Marketo Measure tracking will collect any traffic that is seen on that domain. If a domain is disabled, Marketo Measure will ignore any traffic seen coming from that domain and will not create touchpoints or other data. Marketo Measure will also confirm the disablement of a domain and warn of the ramifications:

   ![](assets/domain-management-3.png)

The impact of toggling a domain is immediate, and changes are not retroactive. In the future, Marketo Measure will purge data from disabled domains after a set period of time.

## Statuses {#statuses}

Admin Console Statuses are categorized as follows:

* **VALIDATED**: This domain is verified in Admin Console
* **UNVERIFIED**: This domain is not fully verified in Admin Console and is not eligible for tracking in Marketo Measure
* **INVALID**: This domain may have expired or been removed from Admin Console. Tracking data in Marketo Measure is flagged for deletion
* **LEGACY**: This domain was created in Marketo Measure and does not exist in the Admin Console

Tracking statuses can be as follows:

* **ACTIVE**: Marketo Measure is currently receiving data from this domain
* **DISABLED**: This domain is available for tracking, but is currently disabled
* **UNAVAILABLE**: This domain is unavailable for tracking because it is not verified

Hovering over any individual status item will trigger a tooltip that further explains that status.

## FAQ {#faq}

**What happens when a domain is removed in the Admin Console?**

When a domain is removed in the Admin Console, Marketo Measure will mark the domain as deleted. Marketo Measure will immediately stop tracking traffic on this domain, but will not remove any previously collected data.

**Why am I unable to enable a domain?**

There are several reasons why a domain might be disallowed for selection on this page. If the domain is not validated in the Admin Console, it will be unavailable in Marketo Measure. Similarly, if the domain is owned by a different Adobe Org from the current Marketo Measure tenant, it may be unavailable for selection.

**How do I remove a domain from this list?**

If a domain has the "enabled" switch turned off, Marketo Measure will ignore it and it is effectively removed from Marketo Measure. To permanently remove a domain from Marketo Measure, you must disable it in Marketo Measure, and subsequently remove it from the Admin Console.
