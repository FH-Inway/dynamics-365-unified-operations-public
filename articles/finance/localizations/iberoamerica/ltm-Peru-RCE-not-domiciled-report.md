---
title: Configure printing for the Electronic Purchase Register (RCE) for purchases not domiciled in Peru
description: Learn how to configure printing for the Electronic Purchase Register (RCE) for purchases that aren't domiciled in Peru in Microsoft Dynamics 365 Finance.
author: Fhernandez0088
ms.date: 04/24/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure printing for the Electronic Purchase Register (RCE) for purchases not domiciled in Peru

[!include [banner](../../includes/banner.md)]

This article explains how to configure printing for the Electronic Purchase Register (RCE) for purchases that aren't domiciled in Peru in Microsoft Dynamics 365 Finance. The Excel output version of annex 13.5.2 is also included.

Taxpayers can use the RCE to manage their electronic purchase records. The National Superintendency of Customs and Tax Administration (SUNAT), the fiscal authority in Peru, generates a monthly proposal. This proposal is designed to serve as a comparative tool that taxpayers can use to identify discrepancies in their records.

The RCE for purchases that aren't domiciled in Peru includes annexes 9, 12.8.5, and 13.5.2. 

## Prerequisites

Before you can generate and print the reports, the following prerequisites must be met:

- The legal entity's address must be in Peru.
- You must enable both the general LATAM feature and the country/region-specific LATAM feature for Peru.
- You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- The RCE for purchases that aren't domiciled in Peru consists of the following formats. You must import all these formats.

    - LTM Tax Report
    - LTM Tax Report mapping
    - RCE-ANEXO 9
    - RCE-ANEXO 12.8.5
    - RCE-ANEXO 13.5.2
    - Non-resident Purchase Register

## Additional configuration required for the RCE reports of purchases not domiciled in Peru including the excel output

- You must create a SUNAT tax application code to use on the report. Learn more in [Tax application for Latin America](ltm-core-tax-application.md).
- When you configure document classes for purchase invoices, debit notes, credit notes, and the DUA-DSI declaration (customs legal requirements), the tax application code must be set according to SUNAT table 3, "Types of Payment Receipts or Documents."
- If the DAM-DSI (customs legal requirements) emission year is required for a transaction, you must enable the **Concept 1** field from the document class.
- If the DAM-DSI (customs legal requirements) code from SUNAT table 4 is required for a transaction, use the **Concept 2** field from the document class.
- You can associate invoices and the DUA-DSI declaration through the source document as required.

    1. In Dynamics 365 Finance, go to **Accounts payable** \> **Inquiries and reports** \> **Invoice** \> **Invoice journal**.
    1. On the FastTab for the desired transaction, select **LATAM** \> **Source Documents**.
    1. Select **New**.
    1. Add the required record.

- Set up the tax application code of the tax ID types that are used with the codes from SUNAT table 1. Learn more in [Tax ID types for Latin America](ltm-core-tax-id-type.md).
- When you create a vendor of the **Person** type, you can use the **Phonetic last name** field to add a second last name as required.
- When you create a vendor of the **Organization** type, you can use the **Organization number** field to configure the SUNAT income type code as required.
- Go to **General ledger** \> **Currencies** \> **Currencies**, and complete the currency tax application code with the appropriate three-letter code from SUNAT table 2, "Currency Type."
- Set up the tax application code of the country/region records that are used with the SUNAT country code table. Set up user-defined field 1 with the SUNAT code of the agreement. This setup helps prevent double taxation. Learn more in [Country/region configuration](ltm-core-address-setup.md#countryregion-configuration).

## Configure application-specific parameters for purchases not domiciled in Peru including the excel output

To configure application-specific parameters for purchases that aren't domiciled in Peru, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configurations**.
1. In the **LTM Tax report** group, for each format that is listed in the [Prerequisites](#prerequisites) section, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** FastTab, select **VendorIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all document classes that are required for vendor transactions.
1. To ensure that the report shows the transactions that meet the configured conditions, set all the **Lookup result** fields to **No**, and specify **Blank** and **Non-blank** conditions.
1. On the **Lookups** FastTab, select **TaxType**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **RIGV**. Then, in the **Tax code** field, select the tax code that is configured for General Sales Tax (IGV) withholdings.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **OC**. Then, in the **Tax code** field, select the tax code that is configured for other concepts.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **VA**. Then, in the **Tax code** field, select the tax code that is configured for taxed and/or untaxed acquisitions.
1. To ensure that the report shows the transactions that meet the configured conditions, set all the **Lookup result** fields to **N/A**, and specify **Blank** and **Non-blank** conditions.

## Generate an RCE annex report

To generate any RCE annex report, follow these steps.

1. In Dynamics 365 Finance, go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, select a format listed in the [Prerequisites](#prerequisites) section.
1. Select **OK**.
1. In the **Tax application ID** field, enter the tax application code that was created for this report.
1. In the **From date** and **To date** fields, set the date range for the report.
1. Select **OK**.
