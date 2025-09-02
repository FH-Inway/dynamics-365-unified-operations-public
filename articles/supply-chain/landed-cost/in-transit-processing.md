---
title: Goods-in-transit processing and receiving
description: When an order or voyage is set up to use goods-in-transit processing, goods can be invoiced before they have been received in the warehouse for consumption.
author: prasungoel 
ms.author: prasungoel 
ms.reviewer: kamaybac
ms.search.form: DeliveryTerms, InventLocation, InventPosting, ITMGoodsInTransitOrder, ITMTableListPage, ITMTable, ITMContainersListPage, ITMContainers, ITMFolioTableListPage, ITMFolioTable, ITMGoodsInTransitOrderEditLines, SysOperationTemplateForm, WHSRFMenuItem, WHSLocDirTable, WHSWorkTemplateTable
ms.topic: how-to
ms.date: 03/24/2025
ms.custom: 
  - bap-template
---

# Goods-in-transit processing and receiving

[!include [banner](../../includes/banner.md)]

This article describes how to work with goods-in-transit orders. This type of order is used only by the **Landed cost** module. When an order or voyage is set up to use goods-in-transit processing, you don't have to wait until goods are received in the warehouse before you can invoice them. Instead, the goods are invoiced when they leave the vendor's warehouse or port of origin, and the financial costs are recognized when the voyage begins. This functionality lets you correctly take ownership of inventory, because goods often become the property of your organization when they leave the shipping port.

When goods-in-transit orders are used, the financially updated items are received in an interim warehouse that is known as a *goods-in-transit warehouse*. The goods stay in this warehouse until they can be received at the final destination warehouse (that is, the warehouse that is defined on the purchase order line). They can't be manually removed. When a goods-in-transit order is invoiced, goods are immediately moved to the goods-in-transit warehouse to signify the change in ownership.

As long as the items are in transit, they aren't available in inventory and can't be picked from inventory for a delivery. However, you can view the goods-in-transit inventory. You can also use the goods for master planning. In this case, use the confirmed delivery date on the purchase order line as the expected date when the inventory will be available for consumption. The following sections describe the setup that is required to process inventory and voyages by using the goods-in-transit concept and functionality.

## Required setup for goods-in-transit orders

### Terms of delivery

When you enable the **Landed cost** module, the standard *terms of delivery* entity is enhanced to support the goods-in-transit feature.

When the **Goods in transit management** option is set to *Yes* for the applicable terms of delivery record, the goods are put into the goods-in-transit warehouse. This action is triggered only if the inventory receipt isn't processed before an invoice is processed. When the delivery terms for an order are set to use goods in transit, users can no longer post a product receipt for the purchase order. If they try, an error occurs. The error message states that they must use the goods-in-transit functionality to proceed.

To work with delivery terms information for goods in transit, go to **Procurement and Sourcing** \> **Setup** \> **Distribution** \> **Terms of delivery**. The following table describes the fields that the **Landed cost** module adds to the **Terms of delivery** page to support the goods-in-transit functionality. Both fields are on the **General** FastTab. For more information about the other fields on this page, see [Terms of delivery (form)](/dynamicsax-2012/terms-of-delivery-form).

| Field | Description |
|---|---|
| Shipping port mandatory | Set this option to *Yes* if a shipping port is mandatory when the delivery terms apply. |
| Goods in transit management | Set this option to *Yes* to use goods-in-transit management when the delivery terms apply. |

### Warehouses for goods in transit and under-delivery

When you enable the **Landed cost** module, the standard *warehouses* entity is enhanced to enable purchase orders to be invoiced while the goods are in a goods-in-transit warehouse.

Landed cost adds two new types of warehouse: *goods in transit* and *under-delivery*. Warehouses of both types can be selected as default warehouses. Successful processing of goods-in-transit orders requires that both the goods-in-transit warehouse and the under-delivery warehouse be configured on the **Warehouses** page. Then, for each default warehouse that will be used with Landed cost and goods in transit, the goods-in-transit warehouse and under-delivery warehouse must be selected for the available warehouses of each type.

The *goods in transit* warehouse type will be associated with your goods-in-transit warehouse. That warehouse will be used to process the goods on goods-in-transit orders before they're received at the final destination warehouse.

When the purchase order invoice is posted for a voyage that is enabled for goods-in-transit functionality, inventory is purchased in the receiving warehouse. It's then immediately transferred to the configured goods-in-transit warehouse. This transfer signifies the change in ownership of the goods that haven't yet physically arrived at the destination warehouse.

In general, one goods-in-transit warehouse is enough for each site if Site and Warehouse are the only inventory dimensions that are used for inventory management. If the Location inventory dimension is also used, a goods-in-transit warehouse must be set up for each combination of a site and warehouse, so that the default location can also be specified.

A default receipt location must be specified for the under-delivery and goods-in-transit warehouses. Go to **Inventory management** \> **Setup** \> **Inventory breakdown** \> **Warehouses**, and set the **Default receipt location** field.

The following table describes the fields that the **Landed cost** module adds to the **Warehouses** page to support the goods-in-transit functionality. Both fields appear on the **General** FastTab. For information about the other fields on the page, see [Warehouses (form)](/dynamicsax-2012/warehouses-form).

| Field | Description |
|---|---|
| Goods in transit warehouse | Identify the goods-in-transit warehouse that is related to the main warehouse. |
| Under delivery warehouse | Identify the under-delivery warehouse that is related to the main warehouse. |

> [!NOTE]
> Warehouses that have a **Type** value of *Goods in transit* or *Under* can't be enabled for warehouse management processes (WMS). If you try to set the **Use warehouse management processes** option to *Yes* for warehouses of one of these types, you receive the following error message: "Landed cost goods in transit warehouse and under warehouse shouldn't use warehouse management processes. Please replace it with new warehouse if warehouse management processes parameter can't be disabled."

## Goods-in-transit orders

You can review and manage goods-in-transit orders directly in the **Landed cost** module. You can process goods-in-transit orders directly from the **Goods in transit orders** page. Alternatively, you can go to the voyage that is associated with the goods-in-transit orders, and process the whole voyage, shipping container, or folio. When you invoice a voyage and create goods-in-transit orders, a new goods-in-transit order is created for each combination of inventory and inventory dimensions that is associated with the purchase order line.

To manage goods in transit, Landed cost uses a two-step procedure:

1. When a purchase order is invoiced, a goods-in-transit order is created. A status of *In transit* is assigned to it.

    > [!NOTE]
    > After the goods-in-transit order is created, the invoice date can't be changed.

1. The goods-in-transit order is processed on the **Goods in transit orders** page. It's then received in the warehouse that is specified on the purchase order. At that point, the status is changed to *Received*.

To work with goods-in-transit orders, go to **Landed cost** \> **Periodic tasks** \> **Goods in transit orders**.

## Receiving stock from the goods-in-transit warehouse

You can receive goods from a goods-in-transit order in several ways:

- If warehouse management processes (WMS) isn't enabled for items, you can use in-transit receiving or post an arrival journal.
- If both WMS and batch/serial number tracking are enabled for items, you can use a mobile device to receive goods from a goods-in-transit order.
- If WMS is enabled for items, but batch/serial number tracking isn't, you can use a mobile device or post an arrival journal to register the receipt of goods from a goods-in-transit order.

The following illustration presents the preceding information in the form of a flow diagram to show when you should use each type of receipt method to receive goods-in-transit orders.

:::image type="content" source="media/receiving-stock-from-git-warehouse.png" alt-text="Diagram that shows when to use each type of receipt method to receive goods-in-transit orders." lightbox="media/receiving-stock-from-git-warehouse.png":::

### In-transit receiving

You can do in-transit receiving from any of the following pages:

- On the **Goods in transit orders** page, select the line, and then, on the Action Pane, select **Receive**.
- On the **All voyages** page, select or open a voyage. Then, on the Action Pane, on the **Manage** tab, in the **Goods in transit** group, select **Receive goods in transit**.
- On the **All shipping containers** page, select or open a shipping container. Then, on the Action Pane, on the **Manage** tab, in the **Goods in transit** group, select **Receive goods in transit**.
- On the **All folios** page, select or open a folio. Then, on the Action Pane, on the **Manage** tab, in the **Goods in transit** group, select **Receive goods in transit**.

> [!NOTE]
> In-transit receiving is normally used in situations where locations and batch/serial number tracking aren't used.

### Arrival journal

You can also receive goods by creating an arrival journal. You can create an arrival journal directly from the voyage page.

1. Open the voyage, container, or folio.
1. On the Action Pane, on the **Manage** tab, in the **Functions** group, select **Create arrival journal**.
1. In the **Create arrival journal** dialog box, set the following values:
    - **Initialize quantity** – Set this option to *Yes* to set the quantity from the in-transit quantity. If this option is set to *No*, no default quantity is set from the goods-in-transit lines.
    - **Create from goods in transit** – Set this option to *Yes* to take quantities from the selected in-transit lines for the selected voyage, container, or folio.
    - **Create from order lines** – Set this option to *Yes* to set the default quantity in the arrival journal from the purchase order lines. The default quantity in the arrival journal can be set in this way only if the quantity on the purchase order line matches the quantity on the goods-in-transit order.

1. Process the arrival journal as described in [Register item receipts with an item arrival journal](/dynamicsax-2012/appuser-itpro/register-item-receipts-with-an-item-arrival-journal).

### Warehouse mobile device receiving

Goods can be received by using a mobile device, provided that the mobile device menu and **Warehouse management** module have been set up to receive goods on a goods-in-transit order. This section describes the setup that is associated with goods-in-transit receiving.

To set up mobile devices for goods-in-transit processing, go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**.

Landed cost adds the following work creation processes to the mobile device menu items to support goods-in-transit processing:

- Goods in transit item receiving
- Goods in transit item receiving and putaway

The configuration settings for these processes resemble the settings for the [purchase order receive and putaway work creation processes](/dynamicsax-2012/appuser-itpro/configure-mobile-devices-for-warehouse-work). However, the *Goods in transit item receiving and putaway* process also adds the following field.

- **Enable shipping container complete** – If this option is set to *Yes*, when the putaway work is completed, the Warehouse Management mobile app provides a button that is named **Shipping container complete**. When that button is selected, the worker is asked to confirm that the container is complete. At that point, all short receipts are processed as an under transaction. The **Shipping container complete** button works just like the **Close** checkbox on the goods-in-transit order receiving page, which is used to depreciate the remaining quantity. The **Shipping container complete** button is available only for under-delivery scenarios and for the **GIT Receive and Putaway** action on the mobile device. When a goods-in-transit order is received in full or as an over-delivery, this button isn't visible.

#### <a name="specify-GIT-order"></a>Specify goods-in-transit orders when receiving with a mobile device

Workers using the Warehouse Management mobile app can register the receipt of goods in transit even when multiple orders are associated with the same voyage, container, item number, and purchase order number. To do so, the worker starts by entering the voyage, container, item, and order numbers, and can then select the relevant goods-in-transit order from a drop-down list.

#### Differences in mobile device receiving for a goods-in-transit order flow versus a standard purchase order flow

The receipt process for goods-in-transit orders via the **Landed cost** module on a mobile device isn't always consistent with the receipt process for purchase orders when Landed cost and goods-in-transit orders aren't enabled.

Here are some examples of the differences:

- The **Voyage** and **Shipping Container** fields must be set for goods-in-transit receiving. By contrast, these fields aren't needed for standard purchase order receiving.
- *Assign putaway cluster* functionality for the putaway process isn't available for goods-in-transit receiving.
- In the normal receipt process that doesn't involve goods-in-transit orders, the worker can cancel in-process work. The license plate is then automatically deregistered. By contrast, putaway work can't be canceled at mid-stage for goods-in-transit receiving. In this situation, a movement journal must be used to move items back to the receiving location. The registration must then be manually undone.

#### <a name="batch-serial"></a>Receive goods-in-transit orders by using a mobile device when serial/batch numbers are enabled

Workers using the Warehouse Management mobile app can register batch/serial numbers when receiving goods-in-transit orders that include items enabled for batch/serial number tracking. The system consolidates the received quantity for each batch/serial number into one work process and automatically assigns the numbers to the received items.

If batch and serial numbers are known when goods are received, they can be manually specified on the device during the receipt process. When more than one serialized item is received on the Warehouse mobile device, the voyage number, shipping container, item, quantity, and license plate number must be manually entered together with each new serial number.

Alternatively, you can let the system automatically assign batch/serial numbers when you receive items that batch/serial number tracking is enabled for.

#### Under-receive when batch/serial number control is activated

To under-receive a serial-enabled item, let the system automatically assign batch/serial numbers. If a serial number is manually set for the quantity that is received, the remaining amount on the under-delivery warehouse can't be posted without a serial number.

### Location directives

Landed cost adds a new work order type that is named *Goods in transit* to the **Location directives** page. This work order type should be configured in the same manner as the [purchase order work order types](/dynamicsax-2012/appuser-itpro/create-a-work-template).

### Work templates

This section describes features that the **Landed cost** module adds to work templates.

#### Goods in transit work order type

Landed cost adds a new work order type that is named *Goods in transit* to the **Work templates** page. This work order type should be configured in the same manner as the [purchase order work templates](/dynamicsax-2012/appuser-itpro/create-a-work-template).

#### Work header breaks

Work templates that have a work order type of *Goods in transit* can be configured to split work headers. On the **Work templates** page, follow one of these steps:

- On the **General** tab for the template, set work header maximums. These maximums work in the same way that they work for purchase order work templates. (Learn more in [purchase order work templates](/dynamicsax-2012/appuser-itpro/create-a-work-template).)
- Use the **Work header breaks** button to define when the system should create new work headers, based on fields that are used for sorting. For example, to create a work header for each container ID, select **Edit query** on the Action Pane, and then add the **Container ID** field to the **Sorting** tab of the query editor. Fields that are added to the **Sorting** tab are available for selection as *grouping fields*. To set up grouping fields, select **Work header breaks** on the Action Pane, and then, for each field that you want to use as a grouping field, select the checkbox in the **Group by this field** column.

Landed cost [creates an over transaction](over-under-transactions.md) if the registered quantity exceeds the original order quantity. When a work header is completed, the system updates the status of the inventory transactions for the principal order quantity. However, it first updates the quantity that is linked to the over transaction after the principal is completely purchased.

If you cancel a work header for an over transaction that has already been registered, the over transaction is first reduced by the canceled quantity. After the over transaction is reduced to a quantity of 0 (zero), the record is removed, and any additional quantities are unregistered against the principal order quantity.

### Marking for goods-in-transit stock

Goods-in-transit transactions are marked to the purchase order transactions. They're then considered in inventory closing and are reflected in the inventory aging report as zero-on-hand items that have inventory value.

> [!NOTE]
> If sales orders are marked to purchase orders to reserve incoming stock, goods-in-transit orders will be split if a purchase order line is marked to multiple sales order lines. Any goods-in-transit order that is split must be manually received one by one.

## Posting rules for landed cost

Landed cost adds two new posting rules that you can configure. These posting rules are used to financially post the direct purchase order invoice amounts to identify ownership of the goods when they leave the point of origin. This process replaces the concept of *goods received not invoiced*, because the goods are invoiced before they're received.

To work with posting profiles, go to **Inventory management** \> **Setup** \> **Posting** \> **Posting**. On the **Purchase Order** tab, the following new posting rules are available:

- *Landed cost, goods-in-transit* – Specify the posting rules for goods-in-transit management.
- *Landed cost, cost charge accrual* – Specify the posting rules for charge account accrual.
