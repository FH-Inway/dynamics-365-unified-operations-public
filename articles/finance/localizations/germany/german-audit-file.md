--- 
title: Generate German audit file
description: Learn about how to generate a German audit file with a step-by-step process using the DEMF demo company with Germany as the region of legal entity primary address.
author: mrolecki
ms.author: mrolecki
ms.topic: how-to
ms.date: 08/29/2018
ms.custom:
ms.reviewer: johnmichalak   
audience: Application User 
ms.search.region: Germany
ms.search.validFrom: 2016-06-30
ms.search.form:
ms.dyn365.ops.version: Version 7.0.0
---

# Generate German audit file

[!include [banner](../../includes/banner.md)]

This procedure shows how to generate the German audit file. This procedure was created using the demo data company DEMF with Germany as the country/region of legal entity primary address.

1. Go to General ledger > Periodic tasks > Data export.
2. In the Format mapping field, enter or select a value.
    - If the list is empty, it means that there is no German audit file export format configuration imported and active. You must import a German audit file export format configuration before you can continue.  
3. Click OK.
4. In the Comment field, type a value.
5. In the Media field, type a value.
6. In the Version field, type a value.
7. In the Table Group field, enter or select a value.
    - For example, select 'Kunden' to export customer master data and transactions.  
8. In the Period - date from field, enter a date.
9. In the Period - date to field, enter a date.
10. Click OK.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]