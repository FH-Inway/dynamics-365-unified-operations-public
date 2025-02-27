---
title: Workers responsible for approving nonconformances
description: Learn how to configure workers that are responsible for approving nonconformances with an outline on enabling a user for nonconformance processing.
author: johanhoffmann
ms.author: johanho
ms.topic: article
ms.date: 03/23/2021
ms.reviewer: kamaybac
ms.search.form: InventTestTable
ms.assetid: a1d9417b-268f-4334-8ab6-8499d6c3acf0
---

# Workers responsible for approving nonconformances

[!include [banner](../includes/banner.md)]

This article describes how to configure workers that are responsible for approving nonconformances.

Nonconformances must be approved before users can start to enter details such as corrections or operations. Before users can approve or reject nonconformances, their user ID (user record) must be linked to a worker record. You can optionally configure workers that are responsible for quality and then allow one worker to approve work on behalf of another worker.

## Enable a user for nonconformance processing

Before a user can approve or reject nonconformances, you must link their user record to a worker record. The approval fields can then be automatically set, and the current user can be automatically filled in for the timesheet. Before the user can use the document notes, you must activate document handling in their user options.

1. Go to **System administration \> Users \> Users**.
1. Find and open the user who should be able to approve or reject nonconformances.
1. Set the **Person** field to the name of the worker that is related to the current user record.
1. On the Action Pane, select **User options**.
1. On the **Options** page for the current user record, on the **Preferences** tab, set the **Enable document handling** option to *Yes*.
1. Close the pages.

## Define workers that are responsible for quality

1. Go to **Inventory management \> Setup \> Quality control \> Workers responsible for quality**.
2. On the Action Pane, select **New**.
3. In the **Worker** field, select the worker that enters quality data.
4. In the **Worker responsible** field, select the worker that the selected worker enters work on behalf of. When nonconformances are created and updated, this worker will be entered by default in **Worker** fields.

## Related information

- [Quality management overview](quality-management-processes.md)
- [Enable quality and nonconformance management](enable-quality-management.md)
- [Quality charges](quality-charges.md)
- [Quarantine zones for nonconformances](quality-quarantine-zones.md)
- [Diagnostic types for nonconformances](quality-diagnostic-types.md)
- [Quality charges for nonconformances](quality-charges.md)
- [Operations for nonconformances](quality-operations.md)
- [Quality management for warehouse processes](quality-management-for-warehouses-processes.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
