---
title: Create customer and vendor records with an address in Venezuela
description: Learn how to create customer and vendor records that have an address in Venezuela.
author: Fhernandez0088
ms.date: 05/02/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe

---

# Create customer and vendor records with an address in Venezuela

[!INCLUDE[banner](../../includes/banner.md)]

The Venezuelan customer and vendor configuration contains the fiscal information that is required by the fiscal authorities. It also includes a reference to the document classes that can be used in transactions with customers and vendors.

## Prerequisites

Before you create records for customers and vendors who are in Venezuela, the following setup must be completed:

- Set up address formats that are specific to Venezuela. These formats must use Venezuela as the country and states/provinces for provinces.
- Create tax codes to use for value-added tax (VAT), including VAT 16%, VAT 8%, VAT 31% and VAT 0%.
- Create tax codes to use for income and VAT withholding taxes in invoices, credit notes and debit notes.
- Set up sales tax groups that contain the tax codes that you created.
- Set up item sales tax groups that contain the tax codes that you created.
- Create document classes to use with customer and vendor invoices, credit notes, debit notes, packing slips, and so on. Learn more in [Configure sales and purchase invoices for Venezuela](ltm-configure-invoices-Venezuela.md).
- Set up a customer and vendor set that contains all the document classes that will be used.
- Set up a tax ID for each type of tax identification that your customers and vendors have.
- Set up a taxpayer type for each type of taxpayer that your customers and vendors have.

## Create a record for a customer in Venezuela

To create a record for a customer in Venezuela, follow these steps.

1. Go to **Accounts receivable** \> **Customers** \> **All customers**, and select **New**.
1. In the **Type** field, select **Organization** for **Sociedad** or **Person** for **Persona natural**.
1. In the **Customer group** field, select a local group.
1. In the **Address** section, select **New**, and provide a name for the address.
1. In the **Country/region** field, select **Venezuela**.
1. Enter the street and street number.
1. Select a **state/province**, and mark the address as primary.
1. To create a record for the company phone number, in the **Contact information** section, select **New**.
1. In the **Sales demographic** section, set the currency to **VES** (legal currency).
1. Configure the terms of payments and the invoice account.
1. Set the delivery terms, mode of delivery, and delivery reason.
1. Select a sales tax group that contains all the tax codes that can have transactions with this customer.
1. In the **LATAM** section, enter the following information:

    - In the **Customer set** field, select a set that contains the document classes to use with the customer.
    - In the **Taxpayer type** field, select a taxpayer that represents an organization. 
    - In the **Based in country/region** field, select **Venezuela**.
    - In the **Country document type** field, select a tax ID type. For example, select **RIF-J** (Unique Taxpayer Registry).
    - Complete the **Country document number** field with the customer's tax ID number.

> [!NOTE]
> This procedure describes the main settings that are required for localization. You can set other fields that are required for other Microsoft Dynamics 365 Finance features that you must use.

## Create a record for a vendor in Venezuela

To create a record for a vendor in Venezuela, follow these steps.

1. Go to **Accounts payable** \> **Vendors** \> **All vendors**, and select **New**.
1. In the **Type** field, select **Organization** for **Sociedad** or **Person** for **Persona natural**.
1. In the **Vendor group** field, select a local group.
1. In the **Address** section, select **New**, and provide a name for the address.
1. In the **Country/region** field, select **Venezuela**.
1. Enter the street and street number.
1. Select a **state/province**, and mark the address as primary.
1. To create a record for the company phone number, in the **Contact information** section, select **New**.
1. In the **Sales demographic** section, set the currency to **VES** (legal currency).
1. Configure the terms of payments and the invoice account.
1. Set the delivery terms, mode of delivery, and delivery reason.
1. Select a sales tax group that contains all the tax codes that can have transactions with this vendor.
1. In the **LATAM** section, enter the following information:

    - In the **Vendor set** field, select a set that contains the document classes to use with the vendor.
    - In the **Taxpayer type** field, select a taxpayer that represents the organization. 
    - In the **Based in country/region** field, select **Venezuela**.
    - In the **Country document type** field, select a tax ID type. For example, select **RIF-J** (Unique Taxpayer Registry).
    - Complete the **Country document number** field with the vendor's tax ID number.

> [!NOTE]
> This procedure describes the main settings that are required for localization. You can set other fields that are required for other Finance features that you must use.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

