---
description: Domain Management - Bizible - Product Documentation
title: Domain Management
exl-id: 4db287a0-0267-463c-a359-266b41f15c59
---
# Domain Management {#domain-management}

For IMS-enabled tenants running Bizible in the Unified Shell, Bizible provides an interface that allows users to manage their own list of domains. Bizible users must first verify any domains they wish to track in the [Adobe Admin Console](https://adminconsole.adobe.com/). Once domains are verified in the Admin Console, users can manage if Bizible uses these domains for tracking website traffic.

## Adding Domains in Admin Console {#adding-domains-in-admin-console}

IMS users with access to the Adobe Admin Console can add and validate domains that they own. Domain validation involves adding a DNS record for each domain and subsequently allowing the Admin Console to verify that record.

   ![](assets/domain-management-1.png)

Instructions for adding domains can be found in the [Admin Console documentation](https://helpx.adobe.com/enterprise/using/set-up-identity.html#setup-domains). Once a domain is added, it must be [linked to a directory](https://helpx.adobe.com/enterprise/using/set-up-identity.html#link-domains-to-directories).

## Managing Domains in Bizible {#managing-domains-in-bizible}

Once a domain is added in the Admin Console, Bizible will sync this record into our database on a regular basis. This synchronization happens nightly, and also every time a user visits the **Domains** page in the Bizible UI. By default, any records that Bizible imports will be disabled, and the tenant must manually enable each domain.

   ![](assets/domain-management-2.png)

On the **Integration** > **Domains** page, the user will see all domains that they have registered in the Admin Console, along with their status. Each domain can be enabled or disabled. If a domain is enabled, Bizible tracking will collect any traffic that is seen on that domain. If a domain is disabled, Bizible will ignore any traffic seen coming from that domain and will not create touchpoints or other data. Bizible will also confirm the disablement of a domain and warn of the ramifications:

   ![](assets/domain-management-3.png)

The impact of toggling a domain is immediate, and changes are not retroactive. In the future, Bizible will purge data from disabled domains after a set period of time.

## Statuses {#statuses}

Admin Console Statuses are categorized as follows:

* **VALIDATED**: This domain is verified in Admin Console
* **UNVERIFIED**: This domain is not fully verified in Admin Console and is not eligible for tracking in Bizible
* **INVALID**: This domain may have expired or been removed from Admin Console. Tracking data in Bizible is flagged for deletion
* **LEGACY**: This domain was created in Bizible and does not exist in the Admin Console

Tracking statuses can be as follows:

* **ACTIVE**: Bizible is currently receiving data from this domain
* **DISABLED**: This domain is available for tracking, but is currently disabled
* **UNAVAILABLE**: This domain is unavailable for tracking because it is not verified

Hovering over any individual status item will trigger a tooltip that further explains that status.

## FAQ {#faq}

**What happens when a domain is removed in the Admin Console?**

When a domain is removed in the Admin Console, Bizible will mark the domain as deleted. Bizible will immediately stop tracking traffic on this domain, but will not remove any previously collected data.

**Why am I unable to enable a domain?**

There are several reasons why a domain might be disallowed for selection on this page. If the domain is not validated in the Admin Console, it will be unavailable in Bizible. Similarly, if the domain is owned by a different Adobe Org from the current Bizible tenant, it may be unavailable for selection.

**How do I remove a domain from this list?**

If a domain has the "enabled" switch turned off, Bizible will ignore it and it is effectively removed from Bizible. To permanently remove a domain from Bizible, you must disable it in Bizible, and subsequently remove it from the Admin Console.
