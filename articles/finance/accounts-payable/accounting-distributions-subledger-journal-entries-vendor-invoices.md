---
title: Accounting distributions and journal entries for vendor invoices
description: Learn about accounting distributions, which are used to define how an amount will be accounted for on vendor invoices.
author: sunfzam
ms.author: Raynezou
ms.topic: how-to
ms.date: 12/15/2023
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: VendEditInvoice
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 93dc608a-b5b4-4ec3-83c2-618e3d80a583
---

# Accounting distributions and journal entries for vendor invoices

[!include [banner](../includes/banner.md)]

Accounting distributions are used to define how an amount, the expense, tax, or charges are accounted for on a vendor invoice. Every amount that must be accounted for when the vendor invoice is journalized has one or more accounting distributions. 

## Accounting distributions 

You can use the following buttons in the Vendor invoice page to view, and possibly modify, the accounting distributions for each amount on the vendor invoice.
-   **Distribute amounts** – View and modify the accounting distributions for an individual line and any child lines. You can view and modify the accounting distributions for the child line directly from the **Sales tax transactions** page or the **Charges transactions** page.
    -   Modify vendor invoice header amounts, such as charges or currency rounding amounts.
    -   Modify vendor invoice line amounts.
-   **View distributions** – View the accounting distributions for all lines on the document. You can't modify the accounting distributions from this view.
    -   View header and line amounts.

If the vendor invoice references a purchase order, you can split and modify the accounting distributions for lines that contain an item that's not stocked. If the vendor invoice line doesn't reference a purchase order line, you can delete an accounting distribution. You can't split or delete lines for charges, taxes, and line discounts. You can modify the ledger account, but you can't change the amounts or percentages.
> [!NOTE]                                                                                                                                 
> If the parent line contains an item that's not stocked and the accounting distributions are split, the child line is automatically split to match the financial dimensions of the parent line. The accounting distributions for the child line can't be additionally split or deleted. Depending on the setup of the child line, you might be able to modify the ledger account for the accounting distributions of the child line.

## Distributing amounts
When you enter a vendor invoice, each amount is distributed as follows.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Type of vendor invoice line</th>
<th>Order of priority that determines where the main account is displayed from</th>
<th>Order of priority that determines which default financial dimension is displayed</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Stocked product</td>
<td><ol>
<li>The accounting distribution for the purchase order line.</li>
<li>The <strong>Main account</strong> field when Purchase expenditure for product is selected on the <strong>Posting</strong> page. <strong>Cost management > Ledger integration policies setup > Posting > Purchase order</strong>.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the account distribution for the purchase order line.</li>
<li>Use the default financial dimension values on the vendor invoice.</li>
</ol></td>
</tr>
<tr class="even">
<td>A procurement category or a product that is not stocked</td>
<td><ol>
<li>The accounting distribution for the purchase order line, if the vendor invoice line references a purchase order line.</li>
<li>The <strong>Main account</strong> field when Purchase expenditure for expense is selected on the <strong>Posting</strong> page. <strong>Cost management > Ledger integration policies setup > Posting > Purchase order</strong>.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the account distribution for the purchase order line.</li>
<li>If the main account is an allocation account, use the default value from the allocation account definition.</li>
<li>Use the default financial dimension values on the vendor invoice.</li>
<li>Use the financial dimension values from the vendor invoice line.</li>
<li>Use the default financial dimension values from the main account on the <strong>Chart of accounts</strong> page.</li>
</ol></td>
</tr>
<tr class="odd">
<td>Fixed asset</td>
<td><ol>
<li>The accounting distribution for the purchase order line, if the vendor invoice line references a purchase order line.</li>
<li>If <strong>Acquisition</strong> is selected in the <strong>Transaction type</strong> field on the <strong>Vendor invoice</strong> page, the <strong>Main account</strong> field when <strong>Acquisition</strong> is selected on the <strong>Fixed asset posting profiles</strong> page.</li>
<li>If <strong>Acquisition adjustment</strong> is selected on the <strong>Transaction type</strong> field, the <strong>Main account</strong> field when <strong>Acquisition adjustment</strong> is selected on the <strong>Fixed asset posting profiles</strong> page.</li>
</ol></td>
<td><ol>
<li>Use the account distribution for the purchase order line, if the invoice line references a purchase order line.</li>
<li>Use the financial dimension values from the vendor invoice line.</li>
<li>Use the default financial dimension values from the main account on the <strong>Chart of accounts</strong> page.</li>
</ol></td>
</tr>
<tr class="even">
<td>Project defined on the vendor invoice line</td>
<td><ol>
<li>The accounting distribution for the purchase order line, if the invoice line references a purchase order line.</li>
<li>If <strong>Balance</strong> is selected in the <strong>Post costs - item</strong> field in the <strong>Project groups</strong> page, the <strong>Main account</strong> field when <strong>Cost</strong> is selected on the <strong>Ledger posting setup</strong> page.</li>
<li>If <strong>Profit and loss</strong> is selected in the <strong>Post costs - item</strong> field in the <strong>Project groups</strong> page, the <strong>Main account</strong> field when <strong>Cost - item</strong> is selected on the <strong>Ledger posting setup</strong> page.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the account distribution for the purchase order line.</li>
</ol></td>
</tr>
<tr class="odd">
<td>Line discount</td>
<td><ol>
<li>The accounting distribution for the purchase order line, if the invoice line references a purchase order line.</li>
<li>The <strong>Main account</strong> field when <strong>Discount</strong> is selected on the <strong>Posting</strong> page.</li>
<li>If a main account for a discount is not defined on the posting profile, the accounting distribution of the extended price on the purchase order line.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the accounting distribution for the purchase order line.</li>
<li>Use the financial dimensions from the accounting distributions for the extended price on the vendor invoice line.</li>
<li>Use the financial dimension values for the vendor invoice line.</li>
<li>Use the default financial dimension values from the main account on the <strong>Chart of accounts</strong> page.</li>
</ol></td>
</tr>
<tr class="even">
<td>Purchase charge, which is entered on the <strong>Price and discount</strong> tab of the purchase order line</td>
<td><ol>
<li>The accounting distribution for the purchase order line, if the invoice line references a purchase order line.</li>
<li>The accounting distribution of the extended price on the purchase order line.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the account distribution for the purchase order line.</li>
<li>Use the financial dimensions from the accounting distributions for the extended price on the vendor invoice line.</li>
</ol></td>
</tr>
<tr class="odd">
<td>Line charge</td>
<td><ol>
<li>The accounting distribution for the purchase order line, if the invoice line references a purchase order line.</li>
<li>If <strong>Ledger account</strong> is selected in the <strong>Debit type</strong> field on the <strong>Charges code</strong> page, the <strong>Debit Account</strong> field on the <strong>Charges code</strong> page.</li>
<li>If <strong>Item</strong> is selected in the <strong>Debit type</strong> field on the <strong>Charges code</strong> page, the accounting distribution for the extended price on the purchase order line.</li>
<li>If <strong>Customer/Vendor</strong> is selected in the <strong>Debit type</strong> field on the <strong>Charges code</strong> page, the <strong>Credit account</strong> field on the <strong>Charges code</strong> page.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the account distribution for the purchase order line.</li>
<li>Use the financial dimensions from the accounting distributions for the extended price on the vendor invoice line.</li>
<li>Use the financial dimension values from the vendor invoice line.</li>
<li>Use the default financial dimension values from the main account on the <strong>Chart of accounts</strong> page.</li>
</ol></td>
</tr>
<tr class="even">
<td>Tax, with the following condition:
<ul>
<li>The <strong>Apply U.S. taxation rules</strong> option is selected on the <strong>General ledger parameters</strong> page.</li>
</ul></td>
<td><ol>
<li>The accounting distribution for the purchase order line, if the invoice line references a purchase order line.</li>
<li>The accounting distribution of the extended price or charge.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the account distribution for the purchase order line.</li>
<li>Use the financial dimensions from the accounting distributions for the extended price on the vendor invoice line.</li>
<li>Use the financial dimension values from the vendor invoice line.</li>
</ol></td>
</tr>
<tr class="odd">
<td>Tax, with the following conditions:
<ul>
<li>The <strong>Apply U.S. taxation rules</strong> option is cleared on the <strong>General ledger parameters</strong> page.</li>
<li>The <strong>Use tax</strong> field for the sales tax group is cleared on the <strong>Sales tax groups</strong> page.</li>
</ul></td>
<td><ol>
<li>If the tax amount is recoverable, the <strong>Sales tax receivable</strong> field on the <strong>Ledger posting groups</strong> page.</li>
<li>If the tax amount is not recoverable, the extended price or the accounting distribution for the charge.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the account distribution for the purchase order line.</li>
<li>Use the financial dimensions from the extended price or the accounting distributions for the charge on the vendor invoice line.</li>
<li>Use the financial dimension values from the vendor invoice line.</li>
<li>Use the default financial dimension values from the main account on the <strong>Chart of accounts</strong> page.</li>
</ol></td>
</tr>
<tr class="even">
<td>Tax, with the following conditions:
<ul>
<li>The Apply U.S. taxation rules option is cleared on the <strong>General ledger parameters</strong> page.</li>
<li>The <strong>Use tax</strong> field for the sales tax group is selected on the <strong>Sales tax groups</strong> page.</li>
</ul></td>
<td><ol>
<li>If the tax amount is recoverable, the <strong>Sales tax receivable</strong> field on the <strong>Ledger posting groups</strong> page.</li>
<li>If the tax amount is not recoverable, the <strong>Use tax expense</strong> field on the <strong>Ledger posting groups</strong> page.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the account distribution for the purchase order line.</li>
<li>Use the financial dimensions from the extended price or the accounting distributions for the charge on the vendor invoice line.</li>
<li>Use the financial dimension values from the vendor invoice line.</li>
<li>Use the default financial dimension values from the main account on the <strong>Chart of accounts</strong> page.</li>
</ol></td>
</tr>
<tr class="odd">
<td>Header charge</td>
<td><ol>
<li>If <strong>Ledger</strong> account is selected in the <strong>Debit type</strong> field on the <strong>Charges code</strong> page, the <strong>Debit account</strong> field on the <strong>Charges code</strong> page.</li>
<li>If <strong>Customer/Vendor</strong> is selected in the <strong>Debit type</strong> field on the <strong>Charges code</strong> page, the <strong>Credit account</strong> field on the <strong>Charges code</strong> page.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the account distribution for the purchase order line.</li>
<li>If the main account is an allocation account, use the default value from the allocation account definition.</li>
<li>Use the financial dimension default template values from the vendor invoice header.</li>
<li>Use the financial dimension values from the vendor invoice line.</li>
<li>Use the default financial dimension values from the main account on the <strong>Chart of accounts</strong> page.</li>
</ol></td>
</tr>
<tr class="even">
<td>Header discount</td>
<td><ol>
<li>The <strong>Main account</strong> field for the <strong>Vendor invoice discount posting type</strong> on the <strong>Accounts for automatic transactions</strong> page.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the account distribution for the purchase order line.</li>
<li>Use the financial dimensions from the accounting distributions for the extended price on the vendor invoice line.</li>
<li>Use the financial dimension values from the vendor invoice line.</li>
<li>Use the default financial dimension values from the main account on the <strong>Chart of accounts</strong> page.</li>
</ol></td>
</tr>
</tbody>
</table>


## Distributing taxes

Accounting distributions for taxes can't be created until taxes are calculated. To calculate sales taxes, complete one of the following tasks on the **Vendor invoice** page:
-   View the invoice total.
-   View the sales tax.
-   View the subledger journal.
-   View accounting distributions for the complete vendor invoice.
-   Place the vendor invoice on hold.
-   Post the vendor invoice.

## Post document with distribution process splitting
When processing long invoice documents, memory usage can be optimized by activating the **Batch processing** feature. 
1. To enable this feature, go to **Pending vendor invoice list**.
2. Select **Process > Setup > Batch**.
3. After clicking **"Post"**, the **"Post document with distribution process splitting"** post job is triggered. This process is enabled when the **Enable vendor invoice posting to split distribution steps** feature is activated.

## Subledger journals for vendor invoices
Before you post a vendor invoice, view the full accounting entry of the invoice, which includes debits, and credits, to verify that the invoice is being posted to the correct accounts. This view of the full accounting entry is called a subledger journal. 

If the subledger journal entry is incorrect when you preview it before you journalize the vendor invoice, you can't modify the subledger journal entry. Instead, modify the accounting distributions or the posting profile. The accounting distributions are used to define one side of the accounting entry, the debit, or the credit. The offsetting subledger journal account entry is created by using the posting profiles, such as from the vendor account or tax.

## Split vendor invoice posting 

During the posting of pending vendor invoices, the posting process involves a substantial transaction flowing into the source document account framework first and the General ledger subsequently. When the invoice data flows into the source document account framework, massive derivations and validations are applied before the subledger is updated. A performance and memory overflow issue might occur with invoices that contain a lot of lines.

The **Enable the vendor invoice to be posted in two stages** feature creates two batches for pending vendor invoice posting. The first batch posts uses the original invoice posting except creating the subledger journals. The second batch posting creates subledger journals to generate accounting. After the second batch is posted, transferring the subledger to general ledger can be done. This reduces the likelihood of memory overflow and enhance overall performance when the invoice contains thousands of lines. When posting pending vendor invoices has dependencies on other modules or subsequent processes, the original invoice posting process is used.

The following situations use the original posting process:
- Prepayment invoice posting
- Invoice posting with prepayment application
- Invoice posting with budget control enabled
- Project invoice posting
- PO/invoice with Terms of payment of Cash (Beginning in Dynamics 365 Finance version 10.0.39)
- Invoice posting with Accounts payable parameter auto-settlement enabled (Beginning in Dynamics 365 Finance version 10.0.39)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
