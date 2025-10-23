---
title: Preview features in Dynamics 365 Commerce 10.0.46 (October 2025)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.46. 
author: johnmichalak
ms.date: 10/24/2025
ms.update-cycle: 1095-days
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: johnmichalak
ms.search.validFrom: 2023-11-01
ms.dyn365.ops.version: 10.0.46

---

# What's new or changed in Dynamics 365 Commerce 10.0.46 (October 2025)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.46. This version has a build number of 10.0.2345 and is available on the following schedule:

- **Preview of release:** October 2025
- **General availability of release (self-update):** November 2025
- **General availability of release (auto-update):** December 2025

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Extensibility | Generated extension SQL script | The Generated extension SQL script feature simplifies and accelerates the process of adding extensions to the channel database. It also helps optimize performance and avoid common customization errors that impact data synchronization.<br><br>In Dynamics 365 headquarters, a new Generated extension SQL script section on the **Scheduler Subjobs** page (**Retail and Commerce** \> **Headquarters setup** \> **Commerce scheduler** \> **Scheduler subjobs**) displays SQL script that you can use as a starting point to add or modify tables in the channel database for the selected subjob. Learn more in [Generated extension SQL script](../dev-itpro/channel-db-extensions.md#generated-extension-sql-script).| |
|  Unified pricing management | Enable streamlined migration to unified pricing management | This feature provides a migration script for Dynamics 365 Commerce unified pricing management that doesn't require additional configuration. | Admins |
| Point of sale | Skip automatic balance check for gift cards before payment | The **Pay with gift card** payment flow automatically checks the gift card balance and displays it to the cashier before processing the payment. This feature eliminates the need for additional steps to determine the balance. However, once the gift card number is entered or swiped for a balance check, the system temporarily saves this number for redemption. This is considered a manual entry, and hence the customer must enter the PIN on the terminal, regardless of whether the number was manually entered or swiped for the balance check. If enforcing a pin number for swiped cards is unacceptable, then starting 10.0.46, you can disable the automatic gift card balance check. Learn more in [Pay with gift card](../dev-itpro/faster-checkout-pos.md#pay-with-gift-card).  | Admins |
| Point of sale | Create customer orders with payment links from Adyen | With this feature, retail stores can create payment links for customers who are interested in a product but need more time to decide. When you provide payment links, customers can easily complete their purchases remotely without needing to return to the store. This approach keeps sales attributed to the physical store and the sales associate who helped the customer, so their performance metrics and potential commissions stay intact. If the customers make the payment within a preconfigured duration then the order gets released for fulfillment else the order gets cancelled. Learn more in [Enable pay by link in POS by using the Adyen connector](../dev-itpro/pay-by-link-overview.md). | Admins |
| Call center | Create call center orders with payment links from Adyen | This feature enables the call center users to generate payment links for customers which eliminates the need for customers to share sensitive card details verbally over the phone, thus enhancing security and trust. These payment links also enable customers to use modern payment methods like digital wallets that aren't feasible in traditional phone transactions. Additionally, similar to the customer orders from point of sale, if the customers are undecided about the order, then, based on a configuration, the call center users can create the orders on a payment hold. If the customers make the payment within a preconfigured duration then the order gets released for fulfillment else the order gets cancelled. Learn more in https://aka.ms/PBLCallCenter | Admins |
| E-commerce | Leverage asynchronous payments for ecommerce orders | Many modern payment methods rely on asynchronous processing i.e., the payment provider sends a notification to indicate success or failure for authorization. With 10.0.46, merchants can leverage new checkout APIs which leverage such asynchronous payment processing. When such a payment method is used, Commerce Scale Unit (CSU) waits for the payment notification to arrive. Once the notification is available, the CSU triggers the automatic checkout of the cart and thus ensuring orders can created even though the web browser might have some problems. In case the payment notification has been received but the order cannot be created due to any reason, then the CSU logs such information in the Commerce Headquarters for monitoring. | Admins |
| Commerce Headquarters | Process critical payment notifications from Adyen | As part of this feature, Dynamics 365 Commerce enables support for processing asynchronous notifications such as dispute, capture failures, reports availability etc., from Adyen. The Commerce notification service receives these notifications and sends the relevant notifications to Commerce headquarters for further processing. Implementation partners can use notifications such as disputes and report notifications to build custom experiences for businesses to meet their business process requirements. The system also provides a way to purge unwanted notifications from the Commerce HQ and release the storage used by such notifications. Learn more in https://aka.ms/OtherPaymentNotifications | Admins |
| Point of sale | General availability of Offline for iOS and Android devices | With 10.0.46 the offline capabilities in Store Commerce iOS and Android devices will be generally available.  This release brings more hardening to the offline capabilities released in 10.0.45 along with including CSU CORS support to seamlessly enable Store Commerce with iOs offline to connect to CSU out of the box. | Admins |
| Commerce Headquarters | Purge log and error files | There is an existing feature that allows the businesses to delete the Commerce transactions from Commerce headquarters. However, sometimes the businesses only want to delete the logs and error files as they can grow very fast but keep the transactions in the system. To do so, we have added a new configuration on the **Purge commerce sales transactions** dialog which will allow the admins to only delete the logs and error files. Learn more in [Purge Commerce transactions](../purge-transactions.md) | Admins |

## Features turned on by default in this release

The following table lists the features that became turned on by default in version 10.0.43. You can still disable these features in **Feature management**, if necessary.

| Module | Feature name | More information |
|--|--|--|


## Resources

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Commerce version 10.0.46 includes platform updates. Learn more in [Platform updates for version 10.0.46 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-46.md). 
  
### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.46, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=NNNNN).

### Dynamics 365 and industry clouds: 2025 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2025 release wave 2 plan](/dynamics365/release-plan/2025wave2/). We captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that are removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice is announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months before removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
