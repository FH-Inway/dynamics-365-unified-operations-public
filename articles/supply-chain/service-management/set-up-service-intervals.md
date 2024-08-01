---
title: Set up service intervals 
description: Learn how to set up service intervals, which indicate when service order lines are created for service agreement lines when you create service orders.
author: ChristianRytt
ms.author: crytt
ms.topic: article
ms.date: 02/20/2018
ms.custom:
ms.reviewer: kamaybac
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: SMAAgreementinterval
ms.dyn365.ops.version: AX 7.0.0
---

# Set up service intervals  

[!include [banner](../includes/banner.md)]

Service interval indicates the frequency with which service order lines are created for service agreement lines when you create service orders.

1. Click **Service management** \> **Setup** \> **Service agreements** \> **Service intervals**.
2. Create a new service interval.
3. Enter the ID and description of the service interval.
4. In the **Range** field, select the range.
5. In the **Frequency** field, type the frequency. The frequency is the factor by which you must multiply the range to obtain the interval for a service agreement.
6. Press **Alt+S** to save the service interval.

## Example

You want to create a service interval of 10 days.

**Create a 10-day service interval**

1. Click **Service management** \> **Setup** \> **Service agreements** \> **Service intervals**.
2. Create a new service interval.
3. Enter the ID and description of the service interval.
4. In the **Range** field, select **Daily**.
5. In the **Frequency** field, type 10.
6. Press **Alt+S** to save the service interval.

## Related articles

[Service intervals](service-intervals.md)  


[!INCLUDE[footer-include](../../includes/footer-banner.md)]