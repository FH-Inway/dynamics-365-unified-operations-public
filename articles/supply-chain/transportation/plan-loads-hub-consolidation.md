---
title: Plan loads using hub consolidation overview
description: Learn about the feature for consolidating shipments in a hub when you deliver goods from different warehouses to the same customer.
author: Weijiesa
ms.author: weijiesa
ms.topic: overview
ms.date: 07/25/2019
ms.reviewer: kamaybac
ms.collection: get-started
ms.search.region: Global
ms.search.industry: Distribution
ms.search.validFrom: 2016-02-28
ms.search.form: WHSLoadPlanningWorkbench, WHSHistory, WHSLoadTable, WHSLoadPlanningListPage, TMSParameters, WHSOutboundLoadPlanningWorkbench, WHSInboundLoadPlanningWorkbench
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: d27b0926-a534-4caf-a2a3-acbc7c440bca
---

# Plan loads using hub consolidation overview

[!include [banner](../includes/banner.md)]

This article describes the feature for consolidating shipments in a hub when you deliver goods from different warehouses to the same customer, or when you receive goods from multiple vendors in the same warehouse.

It can be useful to consolidate shipments in a hub when you deliver goods from different warehouses to the same customer, or when goods are delivered from multiple vendors to the same warehouse.

## Building loads

Before you can use hub consolidation, you must enable the **In transit planning** option on the **Transportation management parameters** page. You must also create the hubs where consolidation will occur.

The following diagram shows an example of hub consolidation. In this case, sales orders from different warehouses are going to the same customer. The basic loads are created based on sales orders in the usual way, by using the **Outbound load planning workbench** page.

[![Hub consolidation.](./media/hubconsol.jpg)](./media/hubconsol.jpg)

To consolidate the two loads in a hub before they are delivered to the customer, on the **Outbound load planning workbench** page, in the **Transportation** field, select **Hub consolidation**. When you select the correct hub for each load, the loads will have the hub as the *drop off* destination. You will also have two *transportation request lines* in the **Supply and Demand** section on the **Outbound load planning workbench** page. You can then add these two lines to a new load. This new load will have both sales order lines, and will also have the hub as the *pick up* address and customer A as the *drop off* destination. The three loads are then ready to be rated and routed like any other load. You can select whatever shipping carrier the system suggests for each load.

You can use a similar method to consolidate loads for multiple transfer orders. In this case, customer A in the preceding diagram is a warehouse.

Alternatively, you can consolidate loads for multiple purchase orders, where the loads are delivered from different vendors to the same warehouse. In this case, you would work on the **Inbound load planning workbench** page instead of the **Outbound load planning workbench** page.

You can have more than one consolidation hub, and can consolidate in multiple hubs for more loads that come from different warehouses. After you build your basic loads and use the hub consolidation option, you build the new loads by using the consolidated transportation request lines. You then rate and route your loads.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]