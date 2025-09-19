---
title: Turn on the Landed cost module and related features for your system
description: Learn how to turn the Landed cost module and its optional extra features on or off with a table defining feature names and requirements.
author: prasungoel 
ms.author: prasungoel 
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 01/31/2025
ms.custom: 
  - bap-template
---

# Turn on the Landed cost module and related features for your system

[!include [banner](../includes/banner.md)]

The **Landed cost** module itself is always turned on and can't be turned off, but several of its add-on features are optional. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of each feature and turn it on as needed. In the **Feature management** workspace in Microsoft Dynamics 365 Supply Chain Management, every feature in this table is listed under the **Transportation management** module. Preview features are marked as such; other features are generally available.

| Feature name and requirements | Feature description |
|---|---|
| <p>**Feature name:**<br>*Source document and accounting distribution support for Landed Cost*</p><p>**Version required:**<br>10.0.34 or later</p> | This feature for the **Landed cost** module enables landed costs to be included in the accounting distribution of purchased product receipts. Therefore, these costs can easily be identified and tracked. The feature supports the association of freight cost from Landed cost with the corresponding source documents. Therefore, it provides a more accurate and comprehensive view of the total cost of goods that are received. By helping you gain more visibility into the expenses that are associated with your purchases and transportation, this functionality allows for better cost analysis and management. Learn more in [Show landed costs in the accounting distribution of product receipts](estimate-manage-landed-costs.md#source-doc-post).<br><br>As of Supply Chain Management version 10.0.41, this feature is turned on by default. |
| <p>**Feature name:**<br>*Specify Goods In Transit Order when receiving via mobile device*</p><p>**Version required:**<br>10.0.35 or later</p> | This feature for the **Landed cost** module enables workers to select a specific goods-in-transit order for receiving when multiple goods-in-transit orders exist for the same voyage, container, item number, and purchase order number. Learn more in [Specify goods-in-transit orders when receiving with a mobile device](in-transit-processing.md#specify-GIT-order).<br><br>As of Supply Chain Management version 10.0.41, this feature is turned on by default. As of version 10.0.43, it's mandatory and can't be turned off. |
| <p>**Feature name:**<br>*Split Goods In Transit Order quantity and assign batch/serial number when receiving via mobile device.*</p><p>**Version required:**<br>10.0.35 or later</p> | This feature for the **Landed cost** module lets workers who use a mobile device assign multiple batch/serial numbers for different quantities of goods that are received from goods-in-transit orders. During the receiving process, all assigned batch/serial numbers are consolidated into one work record and processed together. Learn more in [Assign batch/serial numbers when receiving with a mobile device](in-transit-processing.md#batch-serial).<br><br>As of Supply Chain Management version 10.0.41, this feature is turned on by default. |
| <p>**Feature name:**<br>*Match vendor invoice journal with voyage cost in different currency.*</p><p>**Version required:**<br>10.0.36 or later</p> | This feature for the **Landed cost** module lets users specify a currency code on the vendor invoice journal and match it with voyage cost in another currency.<br><br>As of Supply Chain Management version 10.0.41, this feature is turned on by default. As of version 10.0.43, it's mandatory and can't be turned off. |
| <p>**Feature name:**<br>*Enable Quality Control for Goods In-Transit Order.*</p><p>**Version required:**<br>10.0.41 or later</p> | This feature enables organization to initiate and run quality checks against goods-in-transit orders. This proactive approach enables discrepancies or defects that might occur during transportation to be detected early, thereby ensuring that only products that meet predefined quality standards can proceed to their final destination. Learn more in [Quality orders](../inventory/quality-orders.md). |
