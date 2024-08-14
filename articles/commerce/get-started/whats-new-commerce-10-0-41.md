---
title: Preview features in Dynamics 365 Commerce 10.0.41 (September 2024)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.41. 
author: johnmichalak
ms.date: 07/30/2024
ms.topic: article
audience: Application User
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: johnmichalak
ms.search.validFrom: 2023-11-01
ms.dyn365.ops.version: 10.0.40

---

# What's new or changed in Dynamics 365 Commerce 10.0.41 (September 2024)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.41. This version has a build number of 10.0.2015.16 and is available on the following schedule:

- **Preview of release:** July 2024
- **General availability of release (self-update):** September 2024
- **General availability of release (auto-update):** October 2024

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
|Point of sale |Improve OPOS device connection reliability |To reduce the likelihood of OPOS device connection errors on POS, you can now enable the **Keep connection open** setting for hardware profile devices in Commerce headquarters. This minimizes unnecessary OPEN and CLOSE OPOS operations that often lead to connection errors. |Admin|
|Point of sale | Support for android hardware station extensibility | With android hardware station extensibility, you can build extensions to support HW station requirements to support fiscal integration with fiscal printers with android devices.| Admin |




## Resources

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Commerce version 10.0.41 includes platform updates. To learn more, see [Platform updates for version 10.0.41 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-41.md). 
  
### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.41, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=948711).

### Dynamics 365 and industry clouds: 2024 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2024 release wave 1 plan](/dynamics365/release-plan/2024wave1/). We captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that are removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice is announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months before removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
