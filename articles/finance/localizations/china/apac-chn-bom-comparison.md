---
title: Bill of materials comparison for China
description: A product might be accompanied by several versions of its bill of materials in its lifecycle, because many products are redesigned to meet changing requirements. 
author: AdamTrukawka
ms.author: atrukawk
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 06/27/2024
ms.reviewer: johnmichalak
ms.search.region: China (PRC)
ms.search.validFrom: 2016-11-30
ms.search.form: InventBOMComparison_CN
ms.dyn365.ops.version: Version 1611
ms.assetid: e399ab34-4bfa-4b6d-a956-d425c1395ea3
---

# Bill of materials comparison for China

[!include [banner](../../includes/banner.md)]

This article provides information about BOM comparison for China.

A product might be accompanied by several versions of its bill of materials (BOM) over the course of its life cycle, because many products are redesigned or modified to meet changing requirements. In general, the cost of a BOM reflects the actual cost of production, and is derived from the components and materials that are used, in addition to the direct and indirect costs of creating the final product. The price of the BOM can be assigned manually, or it can be calculated by marking up the costs that are incurred during the manufacture or construction of the product. Use the **BOM comparison** page to compare the component quantities and inventory cost, or the latest purchase price of the components, among the various BOM versions. BOM comparison also lets you to perform the following tasks:

-   Create a new BOM for an existing product, and base the new BOM on earlier versions.
-   Compare and highlight differences in components among a group of similar products.
-   Answer customer inquiries about product differences and uses.
-   Maintain accurate inventory records in industrial and manufacturing environments.
-   Maintain accurate operational and personnel records, and maintain accurate data.
-   Respond quickly to changing production levels and requirements.
-   Control inventory levels.
-   Identify and reduce inventory of obsolete parts.
-   Lower overall manufacturing costs.
-   Improve design and construction processes.
-   Meet client requirements by customizing designs and processes at various budget levels.
-   Generate conceptual estimates or customer quotes that are based on actual experience.

## Example
The following table shows how a BOM comparison is done. In this example, products FG001 and FG003, each of which has one active BOM, and product FG002, which has two active BOMs, are compared. The report lists each component in a BOM version, shows the component quantity in the appropriate units, and shows the inventory cost or latest purchase price.

| Product | BOM     | Site   | Components | Quantity | Unit | Cost      |
|---------|---------|--------|------------|----------|------|-----------|
| FG001   | FG001V1 |        | MT001      | 2        | pcs  | USD 20.00 |
|         |         |        | MT002      | 3        | cm   | USD 10.00 |
|         |         |        | MT005      | 3        | kg   | USD 32.00 |
| FG002   | FG002V1 |        | MT001      | 1        | pcs  | USD 50.00 |
|         |         |        | MT003      | 1        | pcs  | USD 12.00 |
|         |         |        | MT005      | 1        | kg   | USD 10.00 |
|         | FG002V2 | Site 1 | MT002      | 3        | cm   | USD 30.00 |
|         |         |        | MT004      | 2        | box  | USD 32.00 |
|         |         |        | MT005      | 1        | kg   | USD 10.00 |
| FG003   | FG003V1 |        | MT003      | 4        | pcs  | USD 30.00 |
|         |         |        | MT004      | 2        | box  | USD 23.00 |
|         |         |        | MT005      | 3        | kg   | USD 18.00 |







[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
