---
title: Generate invoice lines when you import vendor invoices
description: Learn about the functionality for automatically generating invoice lines on vendor invoices when invoices are imported.
author: sunfzam
ms.author: shpandey
ms.topic: how-to
ms.date: 12/17/2024
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-08-30
ms.dyn365.ops.version: 10.0.23
---

# Generate invoice lines when you import vendor invoices

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article describes the functionality for automatically generating invoice lines on vendor invoices when invoices are imported.

Sometimes, vendor invoices contain only header information without line details, and the vendor consistently sends the invoices in a fixed pattern:

- Invoices always contain the same lines as the purchase order.
- Invoices always contain the same lines based on the goods shipped, with prices based on the purchase order.
  
To streamline the process, invoice lines can be automatically derived from the purchase order or product receipt. To enable automatic creation of invoice lines, follow these steps.

## Enable the settings

1. Go to **Accounts payable \> Setup \> Accounts payable parameters**.
2. On the **Vendor invoice automation** tab, under **Automatic line creation for imported invoices**, set the **Automatically create invoice lines** option to **Yes**. 
3. In the **Choose default quantity for automatic invoice lines creation** field, select the quantity that should be used to automatically generate invoice lines:

    - **Ordered quantity** – Lines are generated from purchase order lines. This value is the default value.
    - **Product receipt quantity** – The purchase order number is used to find the relevant product receipts. It then uses the product receipt quantities to generate invoice lines.

    This parameter is used only when the purchase order number range is specified during invoice import, but the product receipt range isn't specified. If the product receipt range is specified, the line is always derived from the product receipt instead of the purchase order.

4. Set the **Allow invoice to be imported with no derived lines** parameter. This parameter determines whether invoice import is blocked if there are no derived invoice lines.

## Data entity changes

To support the functionality that's described in this article, three fields are added to the **Vendor invoice header** data entity:

- **HeaderOnlyImport** – This field must be set to **Yes** to generate lines for invoice headers.
- **PurchIdRange** – The list of purchase order numbers. The invoice numbers can be a range, such as **PO0001..PO0009** (where two dots separate the start and end of the range), or discrete values, such as **PO0001,PO0003,PO0006**. All purchase orders must belong to the same vendor account on the invoice header. Otherwise, you receive the following error message: "Failed to generate invoice lines. Purchase orders have different vendor accounts."
- **PackingslipRange** – The list of product receipt numbers. Vendor invoice lines can be created from product receipts. However, product receipt numbers aren't typically included on vendor invoices. Only enter the product receipt numbers into this field if you can clearly identify which product receipts are for which specific invoices. Invoice lines can be generated based on product receipts. If this field is used, the setting of the **Choose default quantity for automatic invoice lines creation** field on the **Accounts payable parameters** page is ignored. 

> [!NOTE]
> If multiple product receipt numbers are entered, several pending vendor invoices that have the same invoice number are created. You must manually consolidate these invoices before you can process the invoice further. In future releases, the invoices are automatically consolidated.

All product receipts must belong to the same vendor account on the invoice header.

## Result

If lines are successfully generated, the following message is logged in the vendor invoice automation history: "Automatically create invoice lines: Succeeded."

If lines don't generate, the following error message is logged: "Automatically create invoice lines: Failed."

### Import prepayment invoice

The prepayment invoice can be imported directly via data entity **Vendor invoice header** when the parameter **Automatically create invoice lines** is enabled.

- **HeaderOnlyImport** – Set to **Yes** to generate lines for prepayment invoice.
- **PurchIdRange** – The **Purchase order number** that set the prepayment amount.
- **VENDORINVOICETYPE** – This is **"VendorAdvance"** to indicate a prepayment invoice.
- **IMPORTEDAMOUNT** – The **Amount** on the prepayment invoice.

The import of a prepayment invoice isn't accepted when the prepayment invoice has already been generated without a settlement under the purchase order.

### Import purchase order number

When a vendor invoice is associated with a single purchase order, the purchase order number (PurchId) is given in the vendor invoice header entity to support the following functionality:

- **Currency code derivation and validation** – The currency code is automatically derived from the purchase order if the currency code is not given in the vendor invoice header entity. The validation error is raised when the imported invoice has a different currency code against the one specified on the purchase order. 
- **Financial dimension defaulting** – The invoice header's financial dimension values are derived from the purchase order header. The corresponding financial dimension on the invoice lines is derived from the vendor invoice header during the import of invoice lines. This behavior ensures consistency between invoices that are imported by using the Data Management Framework (DMF) and invoices that are created by using the **Pending vendor invoice** page.
- **Vendor invoice workflow** – If the invoice validation fails, the invoice is redirected to the purchase order originator to address any discrepancies. The correct purchase order number ensures the vendor invoice is redirected to the right purchase order originator during the workflow process. 
