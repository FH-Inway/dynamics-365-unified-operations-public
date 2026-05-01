---
title: Accounting source explorer
description: Learn about the Accounting source explorer page, which you can use for detailed analysis of the source information behind general ledger accounting entries.
author: twheeloc
ms.author: twheeloc
ms.topic: concept-article
ms.date: 06/15/2025
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

The **Accounting source explorer** page in Microsoft Dynamics 365 Finance is an inquiry and analysis tool that helps accounting and finance professionals investigate the detailed source information behind general ledger accounting entries. The **Accounting source explorer** is found under General ledger > Inquiries and reports >  **Accounting source explorer**.

The **Accounting source explorer** page shows source information. Unlike financial statements that present summarized balances (such as the trial balance), the Accounting source explorer enables you to: 
 - View detailed transactional postings
 - Trace result balances back to originating documents
 - Analyze accounting distributions
 - Evaluate financial transaction activity by financial dimension

The **Accounting source explorer** page always shows the same total amount per ledger account as General ledger shows (for example, in a trial balance). As in a trial balance, you can display segments in separate columns. Just select the appropriate financial dimension set. 

For all documents that use the source document framework, the **Accounting source explorer** page shows additional information, based on accounting distributions and, if applicable, project accounting distributions. This information includes the **Monetary amount type**, **Project**, **Activity**, **Category**, and **Line property** values. Here are some examples of the analysis that you can do: 
 - Variances between purchase orders and vendor invoices, because each variance is represented by a monetary amount type, such as charge variance
 - Billable versus non-billable hours and expenses per project, business unit, and main account 

For source documents that use the source document reference identities concept, the Accounting source explorer page shows even more details, such as the **Customer**, **Vendor**, **Worker**, **Product**, **Quantity**, **Unit text**, and **Description** values. Here are some examples of the analysis that you can do: 
 - Hotel expenses per business unit and hotel brand for a fiscal period, based on expense reports
 - Discounts per vendor, product, department 

For these documents, you can also navigate to the actual source document from the **Accounting source explorer** page. 

## Working with filters

The **Accounting source explorer** page relies on filter parameters to limit the volume of retrieved transaction data. Therefore, the page is blank when opening by navigating directly to General ledger > Inquiries and report > Accounting source explorer. 

Select **Advanced filtering** in the Action pane to open the filter options. When the feature **Accounting source explorer updated advanced filtering** is enabled in Feature management more convenient date range selections are available, including different types of date intervals. Additionally, an advanced filter is available that can filter fields such as ledger account and dimensions. These are shown on the **Select parameters** dialog. When this feature is not enabled the Inquiry page opens where the standard query is available.  

### Performance considerations

To ensure accurate results and improve performance:
 - Define appropriate date ranges. Note: start and end dates must be within the same fiscal year
 - Specify financial dimensions as needed
 - Limit data retrieved to less than 1 million transactions

Applying filters helps reduce unnecessary data loading and ensures that transaction analysis is scoped to relevant accounting activity. 

Starting in Dynamics 365 Finance version 10.0.46, a background process called "Accounting source explorer preprocessor" can be enabled via Process automations to improve the loading performance when using the **Accounting source explorer** page. This process automates the generation of **Accounting source explorer** data in the background for quicker selection on subsequent **Accounting source explorer** page runs. In System administration > Setup > **Process automations**, select **Initialize process automations** if you do not see the **Accounting source explorer preprocessor** on the Background processes tab.  

These records can also be generated as needed after opening the **Accounting source explorer** page and is the default functionality. It is recommended using the background process for performance reasons, however.  

## Advanced file export 

Starting in Dynamics 365 Finance version 10.0.45, the **Accounting source explorer advanced file export** feature can be enabled in Feature management. After this feature is enabled, under the export menu, there's a **Multiledger export** option. Selecting this option presents a dialog to allow multiple companies to be selected for export for a given fiscal period. To select the set of companies to export to Excel, select a Fiscal calendar, Fiscal year and Period name. Then select each Ledger name that you want to export to Excel. Each legal entity (ledger name) will be exported to a separate Excel sheet in the same Excel file. 

You don't need to use the advanced filtering to load data into the page before using the **Multiledger export** feature. Select **Export** > **Multiledger export** to begin the process of exporting data from multiple companies. 

### Performance considerations for Advanced file export

 - Limit selected ledgers to only those required. Reducing the number of selected ledgers will decrease the required processing time and improve loading times.
 - Define appropriate date ranges. By default, a fiscal calendar needs to be selected, followed by a fiscal year defined in the selected calendar, and finally a period within the selected fiscal year. If the manual date range setting is in use, date selections should be limited to a fiscal period or a smaller range; large date ranges will incur a significant performance impact.
 - There is a limit of 1,048,576 records per sheet. By default, any records beyond this limit will not be included. 


> [!NOTE]
> As of in Microsoft Dynamics 365 version 10.0.43, a **Enable financial tags for Accounting source explorer** feature is available in Feature management. For more information, see [Financial tags](../general-ledger/financial-tag.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
