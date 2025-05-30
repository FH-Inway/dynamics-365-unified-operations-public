---
title: Accounting source explorer
description: Learn about the Accounting source explorer page, which you can use for detailed analysis of the source information behind general ledger accounting entries.
author: RyanCCarlson2
ms.author: rcarlson
ms.topic: concept-article
ms.date: 12/13/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: AccountingSourceExplorer
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 57b95899-7298-43c0-8034-45b5d993cbf2
---

# Accounting source explorer

[!include [banner](../includes/banner.md)]

This article provides information about the **Accounting source explorer** page, which you can use for detailed analysis of the source information behind general ledger accounting entries.

The **Accounting source explorer** page shows source information. You can use it either as a stand-alone tool or to analyze the details behind general ledger accounting entries. For example, you can use the page to get the most detailed source information for a balance in the trail balance or for a voucher transaction. You can then use the **Export to MS Excel** feature to further slice and dice the information in Microsoft Excel (for example, in a PivotTable or on a PivotTable report). 

### Advanced file export 
With the appliation release 10.0.45 a new feature is available titled **Accounting Source Explorer Advanced File Export** that can be enabled in feature management.  Once this feature is enabled, you will see a new option under the export mentu to select **Multiledger export**. Selecting this option will present a dialog to allow multiple companies to be selected for export for a given fical period.  You will see the selection of a Fiscal calendar and period is required to select the set of companies you are interested in exporting to Excel. 
You do not need to use the advanced filtering to load data into the form before using the Multiledger export feature. Simply click Export - Multiledger export to begin the process of exporting data from multiple companies. 

The **Accounting source explorer** page always shows the same total amount per ledger account as General ledger shows (for example, in a trial balance). As in a trial balance, you can display segments in separate columns. Just select the appropriate financial dimension set. 

You can use parameters to define a date interval for the analysis. This functionality also resembles the functionality in a trial balance.

For all documents that use the source document framework, the **Accounting source explorer** page shows additional information, based on accounting distributions and, if applicable, project accounting distributions. This information includes the **Monetary amount type**, **Project**, **Activity**, **Category**, and **Line property** values. Here are some examples of the analysis that you can do:

- Variances between purchase orders and vendor invoices, because each variance is represented by a monetary amount type, such as charge variance
- Billable versus non-billable hours and expenses per project, business unit, and main account

For source documents that use the source document reference identities concept, the **Accounting source explorer** page shows even more details, such as the **Customer**, **Vendor**, **Worker**, **Product**, **Quantity**, **Unit text**, and **Description** values. Here are some examples of the analysis that you can do:

- Hotel expenses per business unit and hotel brand for a fiscal period, based on expense reports
- Discounts per vendor, product, department

For these documents, you can also navigate to the actual source document from the **Accounting source explorer** page.

> [!NOTE]
> As of in Microsoft Dynamics 365 version 10.0.43, a **Enable financial tags for Accounting source explorer** feature is available in feature management. For more information, see [Financial tags](../general-ledger/financial-tag.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
