---
title: Spanish bill of exchange options
description: Learn about specific options and changes in basic bill of exchange process implemented in Microsoft Dynamics 365 Finance for legal entities in Spain.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 06/26/2024
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Spain
ms.search.validFrom: 2016-11-30
ms.search.form: CustParameters, BankBillOfExchangeTable
ms.dyn365.ops.version: Version 1611
---

# Spanish bill of exchange options

[!include [banner](../../includes/banner.md)]

This article describes specific options and changes in the basic bill of exchange process implemented in Dynamics 365 Finance for legal entities in Spain.

For legal entities in Spain, the bill of exchange functionality has additional options:

-   Validation for bill of exchange journals
-   Dates in bill of exchange journals

## Accounts receivable parameters for Spanish bills of exchange
To set up the parameters for bills of exchange for legal entities in Spain, go to **Accounts receivable parameters** &gt; **Bill of exchange ES**.

## Validation for bill of exchange journals
If the **Validation on bill of exchange journal** parameter is set to **Yes**, a bill of exchange isn't posted when transactions have the same voucher number and different transaction dates. This parameter applies to ledger journal transactions. This parameter is used only when the journal allows one voucher number, and when the **Validation on bill of exchange journals** option is selected on the **Accounts receivable parameters** page. The **Validation on bill of exchange journal** parameter affects the following documents:

-   Draw bill of exchange journal
-   Remittance journal
-   Protest bill of exchange journal
-   Redraw bill of exchange journal
-   Settle bill of exchange journal
-   Payment journal

## Dates in bill of exchange journals
If the **Date treatment on bill of exchange journal** parameter is set to **Yes**, the transaction date on bill of exchange journals is updated to the due date when a payment proposal is used. The **Date treatment on bill of exchange journal** parameter affects the following documents:

-   Remittance journal
-   Protest bill of exchange journal
-   Redraw bill of exchange journal






[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
