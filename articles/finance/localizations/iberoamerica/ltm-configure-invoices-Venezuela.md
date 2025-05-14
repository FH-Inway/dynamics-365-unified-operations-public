---
title: Configure sales and purchase invoices for Venezuela
description: Learn about sales and purchase invoices for Venezuela.
author: Fhernandez0088
ms.date: 05/15/2025
ms.topic: how-to
ms.reviewer: johnmichalak
ms.author: v-cpicon
ms.custom: bap-template
---

# Configure sales and purchase invoices for Venezuela

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to start to use fiscal documents that are specific to Venezuela through the Latin American (LATAM) features in purchase and sales transactions. The LATAM localization uses the concept of **document classes** to refer to fiscal documents such as invoices, credit notes, and debit notes. These documents might have to be completed with specific information, such as the typification, sales point, branch, invoice number structure, and additional fields that should be completed.

## Configure a sales invoice

Configure the following pages to use them in future sales transactions:

- Document class type
- Document class letter
- Sales point 
- Document class
- Document class sales point
- Number sequence
- Journal names

To complete the sales invoice configuration, follow these steps.

1. Create the **document class type** that represents the fiscal documents that will be used in future transactions. Examples include invoices, credit notes, debit notes, and packing slips. Learn more in [Document class type for Latin America](ltm-core-document-class-type.md).
1. Create at least one **Establecimiento** as a **sales point prefix** that is part of the document number **XXXX**-XXXXXXXX. Enable the **Validate CA** option. Learn more in [Sales point prefixes for Latin America](ltm-core-sales-point-prefixes.md).
1. Create the **document classes** that are required for the commercial activity of the company according to the requirements of the Venezuelan fiscal authorities.
1. Enable the **Require CA number** option.
1. Set the **document mask** with the required number of characters for the sales point prefix **XXXX** and the document number **XXXXXXXX**. Set the entry to **Automatic**, **Assignment before post**, and **Mandatory** for both the prefix and the document number. Learn more in [Document classes for Latin America](ltm-core-document-class.md).
1. In every document class that belongs to the company, create a **document class sales point**. On the **Document class point** page, select a sales point. The length of the sales point prefix must match the length of the document mask prefix. For **Secuencial**, create a number sequence as an alphanumeric format of eight characters (XXXX-**XXXXXXXX**). The length of this number sequence must match the length of the document mask. Learn more in [Document class sales point for Latin America](ltm-core-document-class-sales-point.md).
1. Configure the **Sales CA** option in the document class sales point. Learn more in [Sales authorization code for Latin America](iberoamerica/ltm-core-sales-ca.md).
1. Create a **customer set**, and add the document classes that you created in the previous steps. The customer set contains the document classes that can be used in a customer transaction when it's assigned to its LATAM configuration. Learn more in [Customer sets for Latin America](ltm-core-customers-set.md).

## Configure a vendor invoice

Vendor invoices have the same configuration requirements as sales invoices, but automatically generated numeration isn't required. To configure a vendor invoice, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**, and create one document class for each fiscal document that the company receives from vendors. Examples include purchase invoices, purchase credit notes, and purchase debit notes.
1. Add a document class type.
1. Add a document class letter.
1. On each **Document class** page, in the **Journal names** section, add the journal names that the document classes can be used in.
1. Set the **Establecimiento** as a sales point that is part of the document number **XXXX**-XXXXXXXX.
1. Set the document mask with the required number of characters for the **Establecimiento** as a sales point (**XXXX**-XXXXXXXX). The document number includes the **Sequencial** (XXXX-**XXXXXXXX**). Set the entry to **Manual**, **Assignment before post**, and **Mandatory** for both the prefix and the document number.
1. Enable the **Require CA number** option for the codification required.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
