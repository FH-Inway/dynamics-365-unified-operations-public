---
title: Set up and generate an electronic ledger posting report for Peru
description: Learn how to set up and generate an electronic ledger posting report for Peru in Microsoft Dynamics 365 Finance.
author: Fhernandez0088
ms.date: 04/15/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Set up and generate an electronic ledger posting report for Peru

This article explains how to set up and generate an electronic ledger posting report for Peru in Microsoft Dynamics 365 Finance.

The electronic ledger posting report is a digital accounting record that compiles and classifies all the economic transactions of a company in a chronological and detailed manner.

## Prerequisites

Before you can print an electronic ledger posting report, you must fulfill the following prerequisites:
- The legal entity's address must be in country/region Peru.
- You must enable the country/region-specific LATAM feature for Peru and the general LATAM feature.
- You must download the specific report configurations from the Dataverse configuration repository. 
- You must import the following electronic reporting (ER) configurations. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse).
    - Ledger accounting reports
    - Ledger Accounting LATAM
    - Magnetic General Ledger Peru
- You must configure the electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must create a tax application code to use in this report. Learn more in [Tax application for Latin America](/dynamics365/finance/localizations/iberoamerica/ltm-core-tax-application).
- You must configure the application code associated with the transaction currency according to the fiscal regulation.
- You must configure the tax application code associated with the type of country document ID according to the fiscal regulation.
- You must configure the tax application code for the different document classes used in transactions (for example, payment methods, invoices, credit notes, and debit notes) according to the fiscal regulation. 
- You must create a new SSRS Reports/Services reference and configure it as follows:
    1. In the **Report/Service ID** field, enter "LedgerPosting".
    1. In the **Report/Service name** field, enter "LedgerPost".
    1. In the **Report/Service type** field, select an ER configuration.
    1. In the **Model mapping name** field, select **Ledger accounting LTM**.
    1. In the **Data model definition** field, select **MagneticGeneralLedger**.
    1. In the **Format mapping** field, select **Magnetic General Ledger Peru**.
    1. In the list of report/service types, enable **Ledger Posting report**.
    1. In the list of parameters, add "TaxApplicationId" to the **Name** column, and the tax application code you created in the **Value** column.

## Print the ledger posting report for Peru

To print the ledger posting report for Peru, follow these steps.

1. In Dynamics 365 Finance, go to **General Ledger > Inquiries and Reports > LATAM > Ledger Posting Report**.
1. In the Ledger posting report dialog box, configure the filters for the report.
1. In the Report ID field, select the corresponding report/service ID.
1. In the **From date** field, enter the beginning date of the date range for the transactions that you want to print.
1. In the **To date fields**, enter the end date of the date range for the transactions that you want to print.
1. In the **Account number** field, select the account number if you want to print the transactions for a specific account.
1. Select the posting layers you want.
1. Select **Print**.
