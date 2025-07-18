---
title: Payment terms in commercial transactions report (PL-00053)
description: Learn how to configure and generate the payment terms report for Polish legal entities in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/19/2025
ms.reviewer: johnmichalak
ms.search.region: Poland 
---

# Payment terms in commercial transactions report

[!include [banner](../../includes/banner.md)]

This article explains how to configure and generate the payment terms report for Polish legal entities in Microsoft Dynamics 365 Finance.

By January 31 of each year, some companies must submit a report about the payment terms of commercial transactions for the previous year. Companies submit the report through the tax authority application by entering the data that a wizard requests. The system generates a report.

You can use the report to generate a summarized report and a detailed report to facilitate the manual entry of information in the tax authority application. Currently, there is no option for automatic integration with the tax authority site.

The Payment terms report is generated by using the Electronic reporting (ER) tool. The generated report is in Microsoft Excel format and includes the following files:

- **AP detailed report** – The list of payments that have been received within 30 days, within 31 to 60 days, within 61 to 120 days, and after 120 days.
- **AR detailed report** – The list of payments that have been made within 30 days, within 31 to 60 days, within 61 to 120 days, and after 120 days.
- **Summary report** – A consolidation of the AP and AR detailed reports, and payments that aren't received and made during the reported period.

## Prerequisites

In Dynamics 365 Finance, import the following Electronic reporting (ER) configurations from the Global repository.

| ER configuration name              | Configuration type |
|------------------------------------|--------------------|
| Statistics on invoices             | Model              |
| Payment terms model mapping        | Model mapping      |
| Payment terms report (PL)          | Format (exporting) |

For more information about how to download ER configurations, see [Download ER configurations from the Global repository](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

Import the most recent versions of the configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version. Use **Issue search** feature of the [LCS](https://lcs.dynamics.com/v2) portal to find information about the changes by the KB number.

> [!NOTE]
> After you import all the ER configurations from the preceding table, set **Default for model mapping** to **Yes** for the **Payment terms model mapping** configuration.

### Enable features in Feature management

Microsoft recommends that you enable features to improve performance of the **Payment terms in commercial transactions** report.

To enable features in Feature management, follow these steps.

1. In Dynamics 365 Finance, go to **Feature management** \> **All**.
1. In the feature list, find and select the following features:

    - **Optimization of query data source creation time during execution of ER reports**
    - **Optimize datasets memory consumption at ER reports runtime**

1. Select **Enable now**.

## Scenarios covered

Report generation covers the following scenarios:

- Customer and vendor transactions that are filtered by posting group and vendor or customer group:

	- Payments
	- Open transactions

- Payment days that are calculated in the following ways:

	- By payment or settlement date
	- By document or invoice date
	- Per installment, according to the payment schedule

- Amounts in the accounting currency
- Exchange adjustments, or revaluations that are included as part of the payment amount
- Project invoices
- Correction notes
- Compensation between vendor and customer accounts
- Advance invoices or prepayments

> [!NOTE]
> The report doesn't include credit notes that are fully settled.

### Payment terms in commercial transactions report and One voucher

Using the One voucher functionality introduces a limitation of further Payment terms in commercial transactions reporting for data if one voucher was applied. If you post transactions that are part of the Payment terms in commercial transactions report, we recommend that you set the **Allow multiple transactions within one voucher** parameter on the **General ledger parameters** page to **No** in your legal entity. For information about One voucher functionality, see [One voucher](../../general-ledger/one-voucher.md).

## Run the statistics on invoices process

Before you generate the Payment terms report, run the **Statistics on invoices** process from the **Accounts payable** and **Account receivable** modules to generate a specific view of the payment history. The Payment terms report uses this process to get all invoices that have been fully and partially paid. You can run the process in real time, or you can schedule it to run in the background through batch processing.

To run the statistics on invoices process, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable** \> **Periodic tasks** \> **Statistics on invoices** or **Accounts receivable** \> **Periodic tasks** \> **Statistics on invoices**.
1. Select **Calculate statistics**.
1. Select the **From** and **To** dates.
1. Select one or more vendor or customer posting profiles. Posting profiles let you easily include vendor or customer transactions for all vendors or customers, a group of vendors or customers, or a single vendor or customer on the report that is generated. To select all available vendors and customers, leave the field blank.
1. Optional: Select the vendor or customer group to apply an additional transaction filter. To select all available vendors and customers, leave the field blank.
1. Select **OK** to run the process.

## Generate a payment terms report

To generate a payment terms report, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable** \> **Periodic tasks** \> **Statistics on invoices** or **Accounts receivable** \> **Periodic tasks** \> **Statistics on invoices**.
1. Select **Payment terms report**, and then select the related ER format.
1. In the **Details** field, select the detail type for the report. You can select multiple options.

	- AP details
	- AR details
	- Resume

1. Select the report language. The current report is translated into US English (**en-us**) and Polish (**pl**).
1. Select the **From** and **To** dates.
1. Select the vendor or customer group to filter for specific transactions.
1. Select the customer or vendor profile to filter for specific transactions.
1. Select **OK** to generate the reports.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
