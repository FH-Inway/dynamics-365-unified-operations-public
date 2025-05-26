---
title: Payment times reporting schema
description: Learn how to set up, create, and generate the Payment times reporting schema for Australia, including outlines on configuration and statistics on invoices.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/11/2024
ms.reviewer: johnmichalak
ms.search.region: Australia

---

# Payment times reporting schema

[!include [banner](../../includes/banner.md)]

This article explains how to set up, create, and generate the Payment times reporting schema (PTRS) that is required for Australian legal entities.

The Australian government established the PTRS to help improve payment times for Australian small businesses. Under the schema, large businesses and government enterprises must report their small business payment terms and times every six months during an income year.

> [!NOTE]
> This topic outlines the reporting process for Australia’s Payment Times Reporting Scheme, applicable to reporting periods starting July 1, 2024. This schema version is supported in Finance version **10.0.45** and in the following builds of earlier versions:
> - **10.0.44**: 10.0.xxxx.xx
> - **10.0.43**: 10.0.2177.xx
> - **10.0.42**: 10.0.2095.xx

## Prepare your environment to generate a PTRS

### Identify small business suppliers

Before you generate the report, you must identify vendors as small business suppliers and import the required electronic configurations.

Large businesses can use the Small Business Identification (SBI) tool to identify their small business suppliers. The current functionality doesn't include the process of recovering the list of small business suppliers from the SBI tool and then updating Microsoft Dynamics 365 Finance. However, the categorization of this type of suppliers is available in the **Accounts payable** module.

Follow these steps to identify small business suppliers.

1. Go to **Accounts payable** \> **Vendors** \> **All vendors**.
2. Select the required vendor, and then, in the **Vendor profile** section, set the **Small vendor** option to **Yes**.
3. Select **Save**.
4. Repeat steps 2 and 3 to identify each small business supplier that is registered in the legal entity.
5. Close the page.

### Common payment term

**Payment Terms** section of the report contains the **Receivable terms compared to most common payment term** field that is intended to indicate whether the group's receivable terms are longer, shorter or the same as its 
payment terms to Australian small business suppliers. For this comparison, the system uses the **Terms of payment** specified in **Accounts payable parameters** > **Ledger and Sales tax** > **Cash flow forecast** as the **Receivable terms**. 

### eInvoice capable

**Miscellaneous** section of the report contains the **Percentage of Peppol enabled small business procurement** field that is intended to indicate the percentage of all small business trade credit payments in the reporting period that were Peppol eInvoice enabled payments. According to the "Payment Times Reporting: Guidance Materials": _a payment is considered eInvoice capable when the receiving reporting entity is set up to receive eInvoices and has no business rules that block or reroute them_. For more information, refer to the "Payment Times Reporting: Guidance Materials" published by Payment Times Reporting Regulator. 

To identify that the legal entity is "eInvoice capable", follow these steps.

1. Go to **Accountrs receivable** > **Setup** > **Electronic document property types**
2. Create a new custom property and set:
   - **Type**: **Peppol**
   - **Applicable to**: **Legal entities**
3. Go to **Organization administration** > **Organizations** > **Legal entities**, select the reporting or subsidiary legal entity whose data is consolidated by the reporting legal entity and click **Electronic document properties** on the Action pane.
4. Select the **Peppol** electronic document property in the list and specify **Yes** in the **Value** column. If the **Value** is not filled in of filled in with **No**, the legal entity is considered as not "eInvoice capable".
5. Repeat steps 3 and 4 for each legal entity whose data is consolidated by the reporting legal entity.

### Import electronic configurations

In Finance, import the following versions or later of these Electronic reporting (ER) configurations:

| ER configuration name | Type | Description |
|-----------------------|------|-------------|
| Statistics on invoices | Model | Generic model for invoice and payment statistics. |
| Payment times bill model mapping | Model mapping | Model mapping for invoice and payment times statistics. |
| Payment times - PTRS 2024 (AU) | Format (Excel) | Payment Times Reporting Scheme for Australia for reporting periods starting July 1, 2024. |
| Payment times bill (AU) | Format (Excel, CSV) | Payment Times Reporting Scheme for Australia for reporting periods before July 1, 2024. |

For more information about how to import ER configurations, see [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

## Statistics on invoices process

Before you generate the **Payment times** report, run the **Statistics on invoices** process to generate a specific view of the payments history. This process is created for other features and consumed by the **Payment times** report process to get all invoices that have been fully and partially paid. You can run the process in real time, or you can schedule it to run in the background through batch processing.

1. Go to **Accounts payable** \> **Periodic tasks** \> **Statistics on invoices**.
2. Select **Calculate statistics**.
3. Select the **From** and **To** dates. These dates represent the period that should be reported.
4. Optionally, select one or more vendor posting profiles and vendor groups. These parameter let you easily include vendor transactions for all vendors, a group of vendors, or a single vendor on the report that is generated. To select all available vendors, leave these fields blank. These settings apply only to the reporting legal entity. Starting from the July 1, 2024 reporting period, your organization may be required by the Australian Payment Times Reporting Regulator to consolidate data from multiple legal entities into a single reporting entity. For further details, refer to the official guidance materials published by the Australian Government.
5. Optionally, to consolidate data from multiple legal entities into a single reporting entity, expand the **Cross company** FastTab select the relevant legal entities, along with the appropriate **Posting profile** and **Vendor group** for each.

![Statistics on invoices page](../media/apac-aus-ptrs-calculate-statistics-dialog.png)

6. Select **OK** to run the process.

> [!NOTE]
> When the **Calculate statistics** process is run based on the selected parameters, it selects all invoices that were fully or partially settled during a specific period for all the selected vendors. Payments for vendors that aren't small business suppliers are also included. The report includes the amount of all payments for the selected legal entities and the current (reporting) legal entity. The identification of the small vendor supplier can be found in the header section under the **Small business** slicer.

![Statistics on invoices page](../media/apac-aus-ptrs-statistics-page.png)

> [!NOTE]
> The **Cross company** FastTab, along with the option to consolidate data from multiple legal entities into a single reporting entity, is available only for legal entities with primary address in Australia.

### Payment times report pre-processing and generation

PTRS processing lets you create or update the booking period, and prepare all the information and metrics that are required on the **Payment times** report. The processing takes into account the payment terms that are specified for **Invoices**, **Purchase orders** and **Purchase agreements**.

Follow these steps to prepare dataset and report data and generate the report.

1. On the **Statistics on invoices** page, select **Payment times report** on the Action pane.
2. Select **PTRS processing** on the Action pane, and create the related reporting period by specifying the **From** and **To** dates.
3. Optionally, mark the **Recalculate dataset** checkbox to recalculated the **Dataset** for the selected period. It is not necessary to select the **Recalculate dataset** checkbox when generating the dataset for the first time for a reporting period. This function only avialable for reporting periods starting July 1, 2024.
4. Optionally, expand the **Run in the background** FastTab and configure the batch parameters to process the dataset in the background.
5. Select **OK**. As a result, the dataset for the PTRS is generated together with the report data. Dataset generation is avialable for reporting periods starting July 1, 2024 only. Records in the dataset are categorized for inclusion or exclusion in key regulatory datasets, based on the subsidiary's location and vendor attributes:
   - **Trade Credit Arrangements (TCP) Dataset**
     - For foreign subsidiaries (legal entities with a non-AU primary address), include payments to Australian vendors that meet at least one of the following:
       - Contain an ABN (Tax exempt number) with country code AU
       - Contain a Registration ID of VAT ID category with country code AU
     - For Australian subsidiaries (legal entities with an AU primary address), include all vendor payments made by the controlled entity.
   - **Small Business TCP (SBTCP) Dataset**: A subset of the TCP dataset, capturing payments made to Australian small business suppliers.
6. To see the dataset with all the necessary information for PTRS, click the **Dataset** on the Action pane of the **Payment times report** page. The **Dataset** function is avialable for reporting periods starting July 1, 2024 only.
7. Review the generated dataset and PTRS data. Some of the prepared information can be edited. If any dataset fields that impact the main PTRS report have been modified, you may need to recalculate the PTRS data. To do this, run the **PTRS processing** again for the same period without selecting **Recalculate dataset**. This will update only the PTRS data without altering the dataset itself.
8. Select **PTRS report** to generate the report in Excel format that is used to enter the payment information in the authority portal. On the **Statistics on invoices** dialog, in the **Format mapping** field, select the **Payment times - PTRS 2024 (AU)** format and click **OK**. To generate the PTRS in the format applicable to periods before July 1, 2024, select the **Payment times bill (AU)** format.
9. Enter the required amount in the **Exclude credit card payments with payment amount less then** field. This function only avialable for reporting periods starting July 1, 2024.
10. You can also generate the PTRS in batch mode by expanding the **Run in the background** FastTab and configuring the batch parameters accordingly. When an electronic report is generated in batch mode, you can find related batch information and the generated output file as an attachment by going to **Organization administration** > **Electronic reporting** > **Electronic reporting jobs**. For more information about how to configure a destination for each ER format configuration and its output component, see [Electronic reporting (ER) destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).
11. By default, each Payment Times report is assigned the **Status** of **In progress**.  When the report is submitted to the government, you can change its **Status** to **Submitted**. **Payment times report** in the **Submitted** status cannot be modified.
12. To modify and generate a correction of a submitted **Payment times report**, change its **Status** back to **In progress**.
13. Optionally, the generated file can be attached to the **Payment times report** using **Document management**. This helps track the history of report generation and keeps the report output easily accessible. For more information, see [Configure document management](../../../fin-ops-core/dev-itpro/organization-administration/configure-document-management.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
