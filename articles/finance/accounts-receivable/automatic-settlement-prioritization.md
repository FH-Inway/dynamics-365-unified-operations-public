---
title: Automatic settlement and prioritization
description: Learn about how transactions are settled if you select Automatic settlement on the Accounts receivable or Accounts payable parameters pages.
author: mukumarm
ms.author: mukumarm
ms.topic: article
ms.date: 07/06/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: CustOpenTrans, CustParameters, LedgerJournalTransCustPaym, VendParameters
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: e7837cf6-ec69-44b4-8d47-eba38d5c7b1f
---

# Automatic settlement and prioritization

[!include [banner](../includes/banner.md)]

This article describes how transactions are settled if you select Automatic settlement on the **Accounts receivable parameters** or **Accounts payable parameters** pages. It also explains how you can use automatic settlement with payment priority.

When you settle payments with invoices and other transactions, you have two options. You can manually select the transactions to settle, or the system can select the transactions automatically by using the automatic settlement functionality. You can also customize how automatic settlements are processed by using the **Prioritize settlement** option. All these options are part of the settlement parameters that you define on the **Accounts receivable parameters** or **Accounts payable parameters** pages. The way that transactions are automatically settled can differ, depending on the method that you use for automatic settlement. The following methods are available:

- User-defined settlement priority
- Default automatic settlement

The following sections describe how transactions are settled for each method.

## Example transactions

The examples of settlements later in this article are based on the following transactions. All transactions are for customer 2050.

| Transaction| Date | Amount | Cash discount terms | Cash discount date | Comments                                         |
|-----------|-------|--------|--------------|--------------------|--------------------------------------------------------|
| Invoice 1     | August 15   | 100.00 | 2%14, Net 30        | August 29    |                                                |
| Invoice 2     | September 1 | 250.00 | 2%14, Net 30        | September 15       |                                       |
| Invoice 3     | October 15  | 500.00 | 2% 14/Net 30        | October 29        |                                        |
| Interest note | October 15  | 7.00   |    |    | This interest note is for invoice 1 and invoice 2. The amount is calculated as 2-percent interest on amounts that are 30 or more days past due. For example, 0.02 × (100.00 + 250.00) = 7.00. |

## User-defined settlement priority

If you set **Use priority for automatic settlements** to **Yes** on the **Accounts receivable parameters** or **Accounts payable parameters** pages, the system uses the settlement priority you define on the **Settlement priority** page when it selects transactions for automatic settlement. For this example, the settlement priority is defined as follows:

1. Transaction type
    - Payment fees
    - Collection letters
    - Interest notes
    - Invoices

1. Transaction date, Ascending
1. Voucher

If you post a payment for 700.00 on October 25, the payment settles to the transactions in the following order.

| Voucher       | Date       | Invoice | Amount in transaction currency | Amount to settle | Balance | Currency |
|---------------|------------|---------|--------------------------------|------------------|---------|----------|
| Interest note | 10/15/2025 |         | 7.00                           | 7.00             | 0.00    | USD      |
| Invoice 1     | 8/15/2025  | 10001   | 100.00                         | 100.00           | 0.00    | USD      |
| Invoice 2     | 9/1/2025   | 10002   | 250.00                         | 250.00           | 0.00    | USD      |
| Invoice 3     | 10/15/2025 |         | 500.00                         | 343.00           | 157.00  | USD      |

## Default automatic settlement

If you don't specify a settlement priority, the system automatically selects transactions for settlement based on the due date. The transactions you settle must have the same currency as the transaction that they're settled with. If you post a payment for 700.00 on October 25, the system selects the following transactions for settlement.

| Voucher       | Date       | Invoice | Amount in transaction currency | Amount to settle | Balance | Currency |
|---------------|------------|---------|--------------------------------|------------------|---------|----------|
| Invoice 1     | 8/15/2025  | 10001   | 100.00                         | 100.00           | 0.00    | USD      |
| Invoice 2     | 9/1/2025   | 10002   | 250.00                         | 250.00           | 0.00    | USD      |
| Invoice 3     | 10/15/2025 |         | 500.00                         | 350.00           | 150.00  | USD      |
| Interest note | 10/15/2025 |         | 7.00                           | 0.00             | 7.00    | USD      |

## Closed date for payment transaction

The settlement event that fully closes the payment determines the closed date of a payment transaction. When you settle multiple invoices against a payment, and settlement priority rather than transaction date determines settlement order, the payment closed date might not be the latest transaction date of the settled invoices.

## Example

| Transaction | Transaction date | Amount | Settlement order | Result |
|---|---|---|---|---|
| Invoice A | Jan-31-2026 | 900.00 | 1 | Settled first and payment remains open |
| Invoice B | Jan-15-2026 | 100.00 | 2 | Settled second and payment becomes fully settled |
| Payment | Jan-15-2026 or later | 1,000.00 | - | Closed when Invoice B completes settlement |

In this example:

1. The payment amount is 1,000.00.
1. Invoice A, dated Jan-31-2026, is settled first for 900.00.
1. The payment has a remaining unsettled amount of 100.00 and isn't closed yet.
1. Invoice B, dated Jan-15-2026, is settled next for 100.00.
1. The payment is fully settled and closed.
1. The payment transaction closed date can be Jan-15-2026 because the invoice that completed the settlement has the earlier transaction date.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
