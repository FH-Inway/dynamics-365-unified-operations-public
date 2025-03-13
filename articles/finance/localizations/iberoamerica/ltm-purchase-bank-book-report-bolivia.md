---
title: Configure printing for purchase bank books for Bolivia
description: Learn about the required configuration for printing a purchase bank book report for Bolivia.
author: Cpicon85
ms.date: 03/13/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon
---

# Configure printing for purchase bank books for Bolivia

[!include[banner](../../includes/banner.md)]

This article explains how to set up and generate reports for purchase bank books for Bolivia.

The bank book in Bolivia details purchase payments that equal or exceed the amount that is established by the regulations of the National Tax Service (Servicio de Impuestos Nacionales). The **Purchase Bank Book BO** report downloads information about payments of purchase transactions for goods and services on a monthly basis. The downloaded information is in the presentation structure that is requested by the tax authority.

![Purchase bank book report diagram.](../media/LTM-Purchase-bank-book.png)

## Prerequisites

Before you can generate the report, the following prerequisites must be met:

- The legal entity's address must be in Bolivia.
- Both the country/region-specific LATAM feature for Bolivia and the general LATAM feature must be enabled.
- Download the specific report from the Global repository. Learn more in [Download ER configurations from the Global repository of Configuration service](../global/workspace/gsw-import-er-config-dataverse.md).
- Configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- Create a tax application to use on the report. For example, the tax application ID might be **LB**, and the description might be **Libro Bancarizacion**. Learn more in [Tax application for Latin America](ltm-core-tax-application.md).
- Create a field that is named **List 10**. In the **Reference code** section, add two codes: **YES** and **NO**. Learn more in [Field list configuration for Latin America](ltm-core-field-master-lists.md).

## Common configurations for all transaction types

- Create a document class that is named **Orden de pago**, and enable field list 10 as required. You can use field list 10 to specify whether the transaction should be included on the report.
- Configure a document class payment medium that is named **Payment documents**, and configure the tax application code accordingly, based on the medium. For example, the payment medium might be a check, bank transfer, or deposit. For the document class type of each payment medium, select **Unique per entry**. Learn more in [Document class type for Latin America](ltm-core-document-class-type.md).
- Set up a bank account, and configure the settings in the **LATAM** section.

### Configure payment of invoice transactions

Before you make payments for supplier invoices, follow these steps to verify that the document class settings are configured correctly.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**.
1. Select a document class that represents invoices, **Factura**. Verify that you completed the required fields for this type of document. Learn more in [Configure sales and purchase invoices for Bolivia](ltm-Configure-invoices-Bolivia.md).
1. On the Action Pane, select **Tax application**.
1. In the **Tax application ID** field, verify that **LB** is entered.
1. In the **Tax application code** field, enter **4** as the transaction type.
1. In the **Letter code** field, enter **FC** for invoices.
1. In the **User define field 2** field, enter **2** as the type of supporting document.

In the event of a successive tract contract, you might change the value of the **Letter code** field to **CS** and enable the **Concept 3** field of the document class to add the contract number.

### Configure other payments

If you must make payments to suppliers for purchases that don't have an invoice but require withholdings, follow these steps to verify the configuration.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**.
1. Select a document class that represents a supporting document for purchases with withholdings, **Compras con retencion**. Verify that you completed the required fields for this type of document. Learn more in [Configure sales and purchase invoices for Bolivia](ltm-Configure-invoices-Bolivia.md).
1. On the Action Pane, select **Tax application**.
1. In the **Tax application ID** field, verify that **LB** is entered.
1. In the **Tax application code** field, enter **1** as the transaction type.
1. In the **User define field 2** field, enter **410** as the type of supporting document.

If you must make payments to suppliers for real estate purchases, follow these steps to verify the configuration.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**.
1. Select a document class that represents a supporting document for real estate purchases, **Compra de inmuebles**. Verify that you completed the required fields for this type of document. Learn more in [Configure sales and purchase invoices for Bolivia](ltm-Configure-invoices-Bolivia.md).
1. On the Action Pane, select **Tax application**.
1. In the **Tax application ID** field, verify that **LB** is entered.
1. In the **Tax application code** field, enter **2** as the transaction type.
1. In the **User define field 2** field, enter **430** as the type of supporting document.

In the event of a successive tract contract, you might add a **Letter code** field that has the value **CS**. Then, in the **Concepts** section, in the **Concept label 3** field, add the contract number.

## Set up application-specific parameters

To set up application-specific parameters, follow these steps.

1. Open the **Electronic reporting** workspace, and select **Reporting configurations**.
1. Select **Purchase Bank Book BO**, and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **ApplicablePaymentDocuments**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id** field, select the document class that represents a payment order.
1. If you have another document class that represents a payment order, repeat steps 4 through 6 to add it.

## Run the Purchase Bank Book BO report

To run the **Purchase Bank Book BO** report, follow these steps.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, enter or select a value.
1. Select **OK**.
1. In the **TAX application Id** field, specify the tax application code that you created for this report.
1. In the **From date** field, enter a date.
1. In the **To date** field, enter a date.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
