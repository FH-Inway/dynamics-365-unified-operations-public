--- 
title: Registration IDs setup for France
description: Learn how to create and enter Registration IDs setup for France for legal entities, customers, vendors. 
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 04/13/2026
ms.custom:
ms.reviewer: johnmichalak 
audience: Application User
ms.search.region: France
ms.search.validFrom: 2026-06-30
ms.search.form: CustTable, VendTable, OMLegalEntity
ms.dyn365.ops.version: Version 7.0.0 
---

# Registration numbers setup for France

In France, invoices must identify both the issuing or receiving legal entities and their establishments involved in the transaction.
To support this requirement, Dynamics 365 Finance uses [Registration IDs](../../../fin-ops-core/dev-itpro/organization-administration/registration-ids.md) 
together with [Invoice party applicability rules](../../../fin-ops-core/dev-itpro/organization-administration/invoice-party-applicability-rules.md) 
to determine which identifiers must be validated and stored when an invoice is posted.

This section explains how to configure **Registration IDs** for France.

## Supported Registration types for France

Create and use the following **Registration types** configured for the **FRA** country/region:

| Registration type | Description | Restricted to | Unique |
|---|---|---|---|
| SIREN | Official identifier of a French legal entity | Organization | Yes |
| SIRET | Official identifier of a French establishment | Organization | No |
| VAT ID | Official tax identification number for VAT purposes| Organization | Yes |

Each Registration type is configured with:

- Country/region: FRA
- Can be updated: No

The **SIRET** Registration type is configured as non‑unique to allow the legal entity head office and the corresponding head‑office Establishment to share the same identifier where applicable.

## Registration categories

Each **Registration type** must be assigned to a **Registration category** that is used for validation and reporting.

For France, the following **Registration categories** are configured:

| Registration type | Registration category |
|---|---|
| VAT ID | VAT ID |
| SIRET | SIRET |
| SIREN  | Enterprise ID (COID) |

**Invoice party applicability rules** are then defined for these categories to determine:

- which invoice party roles must provide a Registration ID
- and which address purposes are evaluated during invoice posting

### Example 1

For example, a VAT ID-type registration number is required for legal entity, customers and vendors with primary address in France:

![Screenshot of an example VAT ID setup for France.](../media/emea-fra-vat-id-setup.png)

### Example 2

If customers or vendors have their primary address outside France but are also registered for VAT in France, you can extend the French VAT ID registration settings by assigning the **Head company** purpose in the **Customer** and **Vendor** registration setup:

![Screenshot of an example VAT ID setup for France for head company.](../media/emea-fra-vat-id-setup-head-company.png)

When these settings are enabled, on invoice posting runtime the system first attempts to retrieve a French VAT ID–type registration ID from the customer or vendor address that:

- belongs to the French country/region privided the delivery or ship-from address defined for the invoice is in France, and
- is assigned the **Head company** purpose.

If no such registration ID is found, the system falls back to the primary address, provided it is also in French country/region as the delivery or ship-from address of the invoice, and retrieves the French VAT ID from there.

### Example 3

The **SIREN** is the official identifier of a legal entity in France. It must be specified on invoices as part of the business identification details of the parties, in accordance with French invoicing requirements.

![Screenshot of an example SIREN setup for France for head company.](../media/emea-fra-vat-id-setup-siren-fr.png)

### Example 4

The **SIRET** is the unique identifier of an establishment in France, composed of the company’s SIREN and an additional code that distinguishes each location.

![Screenshot of an example SIRET setup for France for head company.](../media/emea-fra-vat-id-setup-siret-fr.png)


### Example 5

If your legal entity has establishments outside France and the [Multiple VAT registration numbers](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/global/emea-multiple-vat-registration-numbers) feature is enabled, addresses in those countries/regions should already be configured with the required VAT ID–type registration IDs.

In this case:

- Assign the **Head company** purpose to these addresses.
- Add the **Head company** purpose to the VAT ID registration category for the relevant countries in the Legal entity settings.
- Create [Establishments](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/organization-administration/organizations-organizational-hierarchies#establishments) for each country where your company is registered for VAT.
- For each establishment, configure a primary address in the corresponding country/region. This address does not require a VAT ID–type registration ID.

For example, if your French legal entity has VAT ID registration in Germany:

![Screenshot of an example VAT ID setup for France - multiple tax registration ids.](../media/emea-fra-vat-id-setup-multi-tax-legal-entity.png)

With this setup, when an establishment in Germany is selected on the invoice, on invoice posting runtime the system retrieves the German VAT ID from the legal entity address in Germany that is assigned the **Head company** purpose. 

### Example 6

When your legal entity has its primary address outside France (for example, in Germany) and also has one or many establishments in France, additional setup is required to ensure correct identification in French invoices:

- Assign the **Head company** purpose to the legal entity address in France that represents the head office.
- For this address, configure the required registration IDs, including **SIREN**, **SIRET**, and **VAT ID**.

In addition:

- Create as many [establishments](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/organization-administration/organizations-organizational-hierarchies#establishments) in France as there are registered SIRET numbers for your company.
- For each establishment, define a primary address in France and assign the corresponding SIRET registration ID.

The **Registration categories** for France should then be configured as follows.

**SIREN** registration type for France.

![Screenshot of an example SIREN setup for France.](../media/emea-fra-vat-id-setup-siren.png)

**VAT ID** registration type for France.

![Screenshot of an example VAT ID setup for France with primary address outside France.](../media/emea-fra-vat-id-setup-vat-id.png)

> [!NOTE]
> For correct VAT reporting in multiple tax registration scenario, the [Multiple VAT registration numbers](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/global/emea-multiple-vat-registration-numbers) feature must be enabled.

**SIRET** registration type for France.

![Screenshot of an example SIRET setup for France.](../media/emea-fra-vat-id-setup-siret.png)

At the same time, the **VAT ID** registration settings for Germany should be configured based on the legal entity’s **primary address** in Germany for correct invoicing from Germany:

- Ensure that the German VAT ID–type registration ID is configured for this address.
- Configure the **VAT ID** registration category for Germany to include the **primary address** in Legal entity settings.

![Screenshot of an example VAT ID setup for Germany.](../media/emea-fra-vat-id-setup-deu-vat-id.png)

## Legal entity Registration IDs

Set up a Registration ID of **VAT ID**, **SIREN** and **SIRET** types and assign them to the legal entity’s address with the **Head company** purpose or to the **primary address**.

![Screenshot of an example Registration IDs setup for French legal entity.](../media/emea-fra-vat-id-setup-le-reg-ids.png)

> [!NOTE]
> Registration IDs are date-sensitive. Ensure that the **Effective** date is specified on the **General** tab of the **Registration IDs** FastTab.

## Establishment Registration IDs

Each [Establishment](../../../fin-ops-core/fin-ops/organization-administration/organizations-organizational-hierarchies.md#establishments) represents a physical or operational unit of legal entity in France.

If your legal entity has only one establishment in France, disable the following parameters:

| Parameter name | Parameter location in Finance | Description |
|----------------|-----------------|-------------|
| **Require establishment on vendor invoice** checkbox | **Accounts payable** > **Setup** > **Accounts payable parameters** > **Invoice** tab > **Invoice** FastTab | When enabled, the system enforces establishment requirements on vendor invoice header or lines: <br>• Enables the **Establishment** field on vendor invoice documents. <br> • Applies defaulting logic to automatically populate the **Establishment** where possible, based on **Site** setup or **Financial dimensions** on the document. <br>• Validates that an **Establishment** is specified before posting and prevents posting if the field is empty. <br> > **NOTE**: The **Establishment** value can't be changed after the invoice is posted. |
| **Require establishment on customer invoice** checkbox |  **Accounts receivable** > **Setup** > **Accounts receivable parameters** > **Updates** tab > **Invoice** FastTab | When enabled, the system enforces establishment requirements on the customer invoice header. <br>• Enables the **Establishment** field on customer invoice documents. <br> • Applies defaulting logic to automatically populate the **Establishment** where possible, based on **Site** setup or **Financial dimensions** on the document. <br>• Validates that an **Establishment** is specified before posting and prevents posting if the field is empty. <br> > **NOTE**: The **Establishment** value can't be changed after the invoice is posted. |
| **Require establishment on project invoice** checkbox | **Project management and accounting** > **Setup** > **Project management and accounting parameters** > **Invoice** tab | When enabled, the system enforces establishment requirements on the project invoice header. <br>• Enables the **Establishment** field on project invoice documents. <br> • Applies defaulting logic to automatically populate the **Establishment** where possible, based on **Financial dimensions** on the document. <br>• Validates that an **Establishment** is specified before posting and prevents posting if the field is empty. <br> > **NOTE**: The **Establishment** value can't be changed after the invoice is posted. |

If your legal entity has multiple establishments in France, enable these parameters accordingly in module parameters and set up a Registration ID of **SIRET** type for each of the establishments and assign it to the establishment's address with the **Invoice** purpose or to the **primary address** of that establishment.

![Screenshot of an example Registration IDs setup for French establishment.](../media/emea-fra-vat-id-setup-establishment-reg-id.png)

> [!NOTE]
> Registration IDs are date-sensitive. Ensure that the **Effective** date is specified on the **General** tab of the **Registration IDs** FastTab.

## Customer and vendor Registration IDs

Customers and vendors may also have establishment‑level Registration IDs assigned to their addresses.

Set up a Registration ID of **VAT ID**, **SIREN** and **SIRET** types and assign them to the customers and vendors address with the **Head company** purpose or to the **primary address**.

![Screenshot of an example Registration IDs setup for French customer head company.](../media/emea-fra-vat-id-setup-cust-head-com-reg-ids.png)

Set up a Registration ID of **SIRET** type and assign it to the customers and vendors address with the **Invoice** purpose. If customer or vendor has multiple establishments, set up a Registration ID of **SIRET** type for each address of that customer or vendor that represents an establishment and assign **Invoice** and **Delivery** purposes to those addresses.

![Screenshot of an example Registration IDs setup for French customer delivery establishment.](../media/emea-fra-vat-id-setup-cust-invoice-reg-id.png)

> [!NOTE]
> Registration IDs are date-sensitive. Ensure that the **Effective** date is specified on the **General** tab of the **Registration IDs** FastTab.

In France, a counterparty may operate under the legal status of entrepreneur individuel (for example, as a micro‑entrepreneur), where a natural person conducts business activities 
in their own name and is assigned official business identifiers such as SIREN, SIRET, or VAT ID.
Such counterparties must be configured as **Organization** party type in Dynamics 365 Finance to allow establishment‑level Registration IDs to be assigned and validated during invoice posting.

## Validation and storage of Registration IDs on invoice posting

When [Invoice party applicability rules](../../../fin-ops-core/dev-itpro/organization-administration/invoice-party-applicability-rules.md) are used:

- the applicable Registration IDs are resolved per invoice
- invoice posting process controls that required Registration IDs are defined per invoice
- after posting, all applicable Registration IDs are immutably stored on the invoice for audit and reporting purposes.

