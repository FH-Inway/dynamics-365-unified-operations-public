---
title: Automatically create service orders  
description: Learn how you can generate service orders that are based on a service agreement for the valid period of the service agreement.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: SMAServiceOrderTable
ms.topic: how-to
ms.date: 03/17/2025
ms.custom: 
  - bap-template
---

# Automatically create service orders

[!include [banner](../includes/banner.md)]

You can generate service orders that are based on a service agreement for the valid period of the service agreement.

The service orders that you generate from a service agreement are all attached to the service agreement.

Service orders are generated automatically from the following settings:

- The service agreement interval that is set up in the service agreement lines. The service agreement interval indicates the frequency that service-order lines are created. Learn more in [Service intervals](service-intervals.md).

- The period that you specify to define the service period in the **From date** and **To date** fields on the **Create service orders** page. Learn more in [Create service orders automatically](create-service-orders-automatically.md).

- The **Combine service orders** option on the service agreement header. This option defines whether service order lines generated from a service agreement, combines service orders according to employee, service task, service object, or service agreement. Learn more in [Combine service orders](combine-service-orders.md).

- The **Time window** option on the service agreement line. The time window defines how far a service order line can move relative to its calculated date. Learn more in [Time windows](time-windows.md).

> [!NOTE]
> If the day that is specified for a service order isn't open in the calendar selected on the **Service management parameters** page, a message indicates that there's a calendar conflict. You can safely ignore the message; the service order will still be created even though the day is closed on the calendar.

## Example 1

The service agreement lasts from January 1, 2012 until December 31, 2012. If the service period that you specify on the **Create service orders** page is from November 1, 2012 until February 1, 2013, service orders are created from November 1, 2012 until December 31, 2012.

## Example 2

The service agreement lasts from January 1, 2012 until December 31, 2012. Two service agreement lines are attached to the service agreement. The first service agreement line has a starting date on January 2, 2012 and an ending date on March 1, 2012. The second service agreement line has a starting date on April 1, 2012 and an ending date on December 31, 2012. You specify a period on the **Create service orders** page that is from October 1, 2012 until December 31, 2012. Therefore, service orders are generated only for the second agreement line, because the starting date and ending date of the first agreement line are before the period that you specified for the service order.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
