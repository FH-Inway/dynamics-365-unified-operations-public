---
title: Deprecated master planning overview
description: Learn how the new Planning Optimization planning engine is now replacing the legacy build-in planning engine and when the deprecated engine will be removed.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 04/25/2026
ms.custom:
  - bap-template
ms.collection:
  - ai-assisted
---

# Deprecated master planning overview

[!include [banner](../../includes/banner.md)]

> [!NOTE]
> Although we strongly recommend that you migrate to Planning Optimization as soon as possible for the reasons outlined in this article, you can continue to use the deprecated master planning engine while you prepare to migrate without requesting an exception from Microsoft. For more information about how to do so, see [Continue to use deprecated master planning with existing companies](continue-using-deprecated-planning.md).

As [previously announced](../get-started/removed-deprecated-features-scm-updates.md#use-of-built-in-supply-chain-management-master-planning-engine-for-distribution-scenarios), the built-in master planning engine is deprecated. This deprecation means that Microsoft no longer supports the engine (unless you face a blocking issue or a regression in functionality) and isn't investing in it (no new features are released).

Planning Optimization is the master planning engine for Supply Chain Management and completely replaces the built-in master planning engine.

If you currently use the deprecated master planning engine, start planning your migration to Planning Optimization now. It's important to get started right away. We strongly encourage you to complete the migration as soon as Planning Optimization supports the features you require so that you can start taking advantage of the many performance improvements and other new capabilities provided by the new service.

Work with a partner to evaluate and plan the migration to Planning Optimization.

Before you switch to Planning Optimization, evaluate the results of the Planning Optimization fit analysis. Learn more in [Planning Optimization fit analysis](planning-optimization/planning-optimization-fit-analysis.md).

## When will the deprecated planning engine be removed?

There's currently no timeline for the full removal of the deprecated master planning engine from Supply Chain Management. Microsoft isn't currently planning to remove it.

> [!IMPORTANT]
> If Microsoft decides to remove the deprecated master planning engine, the company will announce those plans at least 12 months before the removal date on the [Removed or deprecated features in Dynamics 365 Supply Chain Management](../get-started/removed-deprecated-features-scm-updates.md) page. Monitor that page and the [What's new or changed in Dynamics 365 Supply Chain Management](../get-started/whats-new-home-page.md) page for the latest announcements.

Although the deprecated master planning engine isn't being removed right now, it's important to understand what *deprecated* means in practice:

- **No new features** &ndash; Microsoft isn't investing in new capabilities for the deprecated engine.
- **Limited support** &ndash; Microsoft provides support only for blocking issues (where master planning doesn't create any planned orders or continuously fails) and for regressions in functionality. Other issues aren't supported.
- **Version restrictions** &ndash; Starting in Supply Chain Management version 10.0.41, the deprecated master planning engine is blocked for all new deployments. Existing deployments can continue using it on a per-company basis.

We strongly recommend that you begin planning your migration to Planning Optimization now, even though there's no removal date. For guidance, see [Migration to Planning Optimization for master planning](new-master-planning-engine.md).
