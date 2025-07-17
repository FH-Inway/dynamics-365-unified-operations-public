---
title: Use Check and promissory note for Türkiye
description: Learn how to use check and promissory note in the Republic of Türkiye. 
author: v-omerorhan 
ms.author: v-omerorhan 
ms.topic: how-to 
ms.date: 07/15/2025 
ms.reviewer: johnmichalak
ms.search.region: Türkiye 
ms.search.validFrom: 2020-02-03 
ms.search.form: CheckAndPromissoryNote 
ms.dyn365.ops.version: 10.0.9 
ms.assetid: b2b22868-de68-439f-914c-78c6930b7340
---

# Use Check and promissory note for Türkiye
[!INCLUDE[banner](../../includes/banner.md)]

In Türkiye, checks and promissory notes are widely used commercial payment instruments that require careful tracking and accounting in accordance with regulations. 
The Check and promissory note module in Dynamics 365 Finance provides end-to-end functionality to manage the lifecycle of these financial documents, including their receipt, issuance, transfer, collection, endorsement, return, and rediscounting.

This module ensures compliance with the requirements by offering specialized configuration options, automated journal entries, portfolio tracking, and rediscount calculations.

Key capabilities of the Check and promissory note are as below; 

- Define and manage check/promissory note transaction codes.
- Group documents using portfolio codes (received/issued).
- Record and track the full lifecycle of commercial papers.
- Generate and reverse rediscount entries.
- Integrate with customer/vendor payments, bank transactions, and posting profiles.

## Configure Check and promissory notes parameters

This section provides general information about the parameters for check and promissory note feature for Türkiye.

The **Check and promissory note parameters** page allows you to define company-wide settings for managing the lifecycle of checks and promissory notes. 
These parameters determine how documents behave in journals, which default accounts are used, and how legal requirements are applied.

You can access the **Check and promissory note parameters** page by navigating to **Cash and bank management > Setup > Check and promissory operations > Check and promissory note parameters**.

Here are the details for the fields; 

- **General** Tab

| Field | Description |
|------------|-------------|
| Settlement status | Defines the default settlement behavior for checks and promissory notes. If set to `None`, no automatic settlement is applied when transactions are posted. |
| Customer method of payment | Specifies the default method of payment to be used for customers when recording check or promissory note transactions. |
| Vendor method of payment | Specifies the default method of payment to be used for vendors during check or promissory note operations. |
| Portfolio account type | Indicates the type of account used to represent portfolios in accounting entries. Typically set to `Bank`, but can vary depending on how portfolios are configured. |
| Use due date | Enables due date control on check and promissory note documents. When turned on, the system tracks and validates due dates during operations. |
| The Printed number field is mandatory | If enabled, the check or note number must be entered before a transaction can be posted. Useful for ensuring traceability of printed documents. |
| Control of out date for check | When enabled, prevents entry of an issue (out) date that is later than the due date of the check. Ensures compliance with date logic. |
| Is reverse date | If enabled, the system allows reversal postings to use the original transaction’s date, which is important for maintaining accurate historical records. |

- **Rediscount** Tab

    - **Overview** Tab

| Field name | Description |
|------------|-------------|
| Journal name | Specifies the default journal that will be used when posting rediscount transactions. This journal must be previously created and set up under **General ledger > Journal names**. |
| Exchange rate type | Defines which exchange rate type will be used for rediscount calculations involving foreign currency checks or promissory notes. For example, `Forex Buying` or `Banknote Buying`. |
| Detail level | Determines the level of detail that will be shown in the rediscount journal lines. Options typically include `Details` (per check/note) or `Summary` (per portfolio or account). |
| Interest calculation type | Selects the basis on which interest will be calculated. The option `Calculated period date` means the interest is calculated based on the actual number of days between the posting date and maturity date. |
| Automatic posting | If enabled, rediscount entries will be automatically posted after generation. If disabled, the entries must be reviewed and posted manually. |

  - **Accounts receivable** Tab

| Field  | Description  |
| ------ | ------- |
| Rediscount account of notes receivable | Specifies the general ledger account used to post rediscounted notes receivable. |
| Rediscount interest expense account    | Specifies the general ledger account for posting interest expenses from rediscount operations. |

- **Accounts payable** Tab

| Field  | Description |
| ------- | -------- |
| Rediscount account of notes payable | Specifies the general ledger account used to post rediscounted notes receivable. |
| Rediscount interest income account | Specifies the general ledger account for posting interest expenses from rediscount operations. |

- **Check dimensions** Tab

| Field | Description |
|----|----|
| COA dimension | Used for coding rediscount calculations at the chart of accounts level. |
| Portfolio dimension | Links system check numbers to portfolio account dimensions (e.g., 101, 103, etc.). |
| Customer dimension | Applies if vendor (320*) or customer (120*) accounts track check numbers. |
| Vendor dimension | Applies if vendor (320*) or customer (120*) accounts track check numbers. |
| Bank dimension | Applies if bank accounts (102*) use check dimension tracking. |

- **Number sequences** Tab

| Field  | Description  |
| ------- | -------- |
| System number of check | Automatically generated unique identifier for each check or promissory note entered into the system. |
| Check payroll number   | Number sequence assigned to identify check payroll batches. |
| Check movement number  | Sequence number used to identify each transaction line for check or promissory note entries (journal transaction number). |
| Last refreshed on    | System-generated reference indicating the last refresh or update point for check sequences. |
| Expiration date   | Number sequence to track the expiration date-related operations, generally used for validity tracking or aging of checks. |

> [!NOTE]  
> Rediscount accounting is typically used at month-end or year-end to reflect accrued interest income or expense related to post-dated checks or promissory notes.

## Define portfolio codes for Check and promissory notes operations

This section provides an overview of the key features and functionalities available on the **Check and promissory notes portfolio codes** page in Microsoft Dynamics 365 Finance. 
By following the steps outlined, you can effectively manage check-promissory note processes within your organization.

The portfolio codes enable organizations to define and manage portfolio codes for financial instruments such as checks and promissory notes, which are widely used in Turkish commercial transactions.
In Türkiye, it is a legal and operational requirement to group such instruments under portfolios for tracking, processing, and reporting purposes. These portfolios help classify received and issued commercial papers and facilitate proper accounting, endorsement, and reconciliation processes.

This page provides a centralized location to:

- Set up portfolio codes with descriptive names.
- Optionally assign default ledger accounts for accounting.
- Categorize portfolios by instrument type (check or promissory note).
- Support financial and legal workflows that rely on portfolio tracking, including customer/vendor payments, protests, collections, and commercial paper reporting.

Here are the details for each field;

| **Field** | **Description** |
| --- | --- |
| Portfolio code | Specifies an unique identifier for each portfolio. |
| Portfolio name | Specifies a descriptive label for the portfolio. |
| Account type | Specifies the type of account associated with the portfolio. |
| Account number | Specifies the account number linked to the portfolio. In Account type field; |
| Portfolio type | Indicates the type of portfolio (e.g., check portfolio, promissory note portfolio). |
| Currency | Specifies the currency in which the portfolio transactions are conducted. |
| Bank account for collection | Specifies the bank account used for collecting checks or promissory notes. |

> [!NOTE]
> Each portfolio must be defined with a specific currency. A portfolio can only be used for transactions in the currency assigned to it.

To create a new portfolio, follow these steps; 

1. Go to **Cash and bank management > Setup > Check and promissory note operations > Check and promissory note portfolio codes**.
2. Select **New**.
3. In the **Portfolio code** field, enter an unique code.
4. In the **Portfolio name** field, enter a name for portfolio.
5. Select an account type in the **Account type** field.
6. Select an account number in the **Account number** field.

    -  If **Bank** is selected, a bank account must be selected for accounting. 
    -  If **Ledger** is selected, a main account must be selected for accounting.

7. Select a portfolio type in the **Portfolio type** field.
 
    -  **Check received**: Select this option for portfolios that track checks received from customers.
    -  **Check given**: Select this option for portfolios used to track checks issued by the company.
    -  **Promissory note received**: Select this option for portfolios that manage promissory notes received from customers.
    -  **Promissory note given**: Select this option for portfolios used to track promissory notes issued by the company.

8. Select a currency code in the **Currency** field.
9. Select a bank account for the collection in the **Bank account for collection** field. The bank account that is used as the offset account during check collection transactions must be selected for the portfolio.

## Define transaction codes for check and promissory note operations

This section explains how to define transaction codes to create a check and promissory note transaction in Microsoft Dynamics 365 Finance.

The **Check or promissory note transaction codes** page is used to define standardized transaction codes for managing checks and promissory notes in Dynamics 365 Finance. 
These codes represent actions such as endorsement, collection, return, protest, or cancellation, and are essential for tracking the legal and financial status of commercial paper. 

Transaction codes are central to managing check and promissory note operations in Türkiye. 
In Dynamics 365 Finance, each type of check or promissory note movement—such as receipt, issue, transfer, collection, return, or bounce—is represented by a unique transaction code.

This page allows users to configure these codes to support financial and legal processes, including automated posting, matching, and categorization. 
These codes are then used in the **Check-promissory note journal** to determine how each document is recorded and processed.

The page is used to:

  - Create codes that represent different types of financial movements for checks and promissory notes.
  - Assign behavior parameters to each code, such as whether it's a receipt, issue, collection, or return.
  - Link transaction codes with appropriate journal names and accounts to ensure correct ledger postings.
  - Enable automatic matching (settlement) of customer/vendor balances based on the selected transaction.

Here are the details for the each field; 

| Field                     | Description                                                                                                   |
|---------------------------|---------------------------------------------------------------------------------------------------------------|
| Transaction code          | Specifies a unique identifier (up to 10 characters) for the transaction.                                      |
| Against transaction code  | Used for transfer operations where two linked transactions are needed (receipt + issue).                      |
| Transaction code description | Specifies a descriptive name that explains the purpose of the transaction.                              |
| Journal name              | Specifies the journal name used when the check and promissory note journal is posted.                        |
| Receipt                   | Specifies that this code is used to receive a check/promissory note into a portfolio.                        |
| Issue                     | Specifies that this code is used to issue a check/promissory note from a portfolio.                          |
| Collection                | Specifies the transaction as a collection event for issued or received documents.                            |
| Return                    | Specifies the transaction as a return of a previously issued or received check/promissory note.              |
| Bounce check              | Specifies the transaction as a bounced check.                                                                |
| New check                 | Used when entering a new check or promissory note into the system.                                           |
| Against transaction code  | Specifies the related transaction code used in transfer transactions between portfolios.                     |
| Account type              | Specifies the offset account type: Customer, Vendor, Ledger, Bank, Portfolio or COA.                         |
| Account number            | Specifies the default account to use when this transaction code is selected.                                 |
| Auto settlement           | Enables automatic matching of open customer/vendor balances when posting.                                   |
| Matching type             | Determines how matching is done (by due date, transaction date, etc.).                                       |
| Bank transaction type     | Optional field to classify bank-related check movements.                                                     |

To create a transaction code for check and promissory note process; 

1. Go to **Cash and bank management > Setup > Check and promissory note operations > Check or promissory note transaction codes**.
2. Select **New**.
3. In the **Transaction code** field, enter an unique code.
4. In the **Transaction code description** field, enter a name for transaction code.
5. Select **Against transaction code**, it specifies the related transaction code that should be automatically triggered when the selected transaction code is used in a journal.
For example, when transferring a check between two portfolios, you can define an against transaction code to automatically generate both the outgoing and incoming movements within the same journal.
6. Assign a **Journal name** to specify which journal will be used for posting.
7. Set the appropriate flags to define the behavior of the transaction in the relevant field:

    -  Select **Receipt** if the transaction represents the receipt of a check or promissory note.
    -  Select **Issue** if the transaction represents issuing a document.
    -  Select **Collection**, **Return**, or **Bounce check** as needed.
    -  Enable **New check** if this is the first entry of the document into the system.

8. In the **Account type** field, choose the type of account to post against (e.g., Customer, Vendor, Ledger).
9. Select or enter the **Account number** if a default is required.
10. Select **Against transaction code** to link the outgoing and incoming movements if the transaction is part of a transfer (e.g., between two portfolios).
11. Select **Auto settlement** if you want the system to automatically settle open transactions.
12. Choose a **Matching type** to define how settlement will be matched (e.g., by due date or transaction date).
13. Select or enter a **Bank transaction type** to track the check or promissory note in bank transactions.
14. Select **Save**.

The transaction code is now available for use in the Check-Promissory note journal and related processes.

> [!NOTE]
> Only the relevant flags for a single type of transaction should be selected. For example, don't select both **Receipt** and **Return**.

## Define Bank branch names for Check and promissory note operations

This section defines how to select bank and branch information for bank check records.
The **Bank branch name** is used to define and manage the relationship between banks and their branches in Türkiye. This information is essential for processes that require accurate identification of bank and branch codes, such as bank check transactions.
The **Bank branch name** allows users to configure and reference standardized bank and branch information based on the official registry used in the Turkish banking system. Each bank and its associated branches are uniquely identified by a combination of codes.

Here is the explanation of the each field:

| **Field** | **Description** |
| --- | --- |
| Bank groups | A unique numeric code representing the bank. |
| Branch code | A unique code representing the specific branch of the bank. |
| Bank branches | The name of the bank branch. |

To create a bank branch, follow these steps;

1. Go to **Cash and bank management > Setup > Check and promissory note operations > Bank branch name**.
2. Select **New**.
3. In the **Bank group** field, select or enter the bank group code.
4. In the **Branch code** field, enter the branch code.
5. In the **Bank branches** field, enter the branch name.
6. Select **Save**.

## Create a new Check and promissory note journal

This topic provides a detailed overview of the **Check and promissory note journal** functionality in Microsoft Dynamics 365 Finance. 

This feature enables organizations operating in Türkiye to manage and track financial transactions related to commercial papers—such as checks and promissory notes—in compliance with Turkish commercial law and local accounting standards.
You can use this journal for:

- Issuance or acceptance of a check or promissory note.
- Receipt or return of a check or promissory note.
- Endorsement checks to third parties.
- Collection or settlement of amounts in check or promissory note.

Each journal line is associated with predefined portfolios, transaction codes, and ledger posting profiles, which support accurate financial categorization and integration with the general ledger. 
This setup ensures that financial movements are posted automatically and in accordance with statutory requirements.

By using this functionality, organizations benefit from:

- Automated posting processes for commercial paper transactions
- Full auditability and compliance with local financial regulations
- Maturity and rediscount tracking capabilities for checks and promissory notes
- Transparent and standardized journal entries for internal and external reporting

Here are the details for the each field for **Check and promissory note journal** page; 

| Field  | Description  |
|-------------|----------|
| Check payroll number  | Specify the unique, system-generated identifier for each journal line.         |
| Transaction code      | Indicate the type of transaction (e.g., CK10 for receipt, CK20 for issue).     |
| Date                  | Specify the transaction date for the check or promissory note.                 |
| Portfolio code        | Indicate the portfolio assigned to the document for classification and tracking.|
| Description           | Describe the purpose or nature of the transaction.                             |
| Reversal date         | Specify the date when the transaction should be reversed, if applicable.       |
| Account type          | Indicate the account category involved (e.g., Customer, Vendor, Bank).         |
| Account number        | Specify the relevant account number for the transaction.                       |
| Posting profile      | Specify the posting profile used to generate ledger entries.                   |
| Average maturity      | Indicate the calculated maturity date based on the document’s due date.        |
| Average maturity day  | Specify the number of days from the transaction date to the maturity date.     |
| Journal batch number  | Specify the system-generated identifier for the posting batch.                 |
| Posted                | Indicate whether the journal has been posted to the ledger.                    |
| Reversal journal ID   | Specify the ID of the journal created when reversing the transaction.          |
| Against transaction ID| Indicate the linked transaction (if part of a transfer or offset pair).        |
| Total                 | Specify the monetary amount of the check or promissory note.                   |

You can use the these functions when you want to create a journal.

Here are the general information for the each function in **Check and promissory note journal**; 

| Button | Description   |
|---------|----------|
| New check             | Creates a new check or promissory note will be manually registered.         |
| Select check          | Indicate that an existing check or note should be selected for processing.       |
| Post                  | Indicate that the journal will be submitted for financial posting.               |
| Journals              | Provides access to the source journal for a check and promissory note journal that has been posted to the ledger. |
| Check reversal journal| Describe the reversal of a previously posted journal for audit compliance.       |
| Transactions          | Indicate that the transaction history of the selected document will be displayed.|
| Check journal list    | Specify that a list of all check journal entries will be displayed for review.   |

When you want to create a **Check and promissory note journal**, select **New** and go to details page.

The **Check and promissory note journal – Header** view is used to enter the main details of a check or promissory note transaction. 
It helps users define how the document will be processed by setting values like the transaction type, account information, portfolio, and dates. 
You can also enter additional information such as payment references or exchange rate settings if needed. 
These details ensure the transaction is correctly recorded, linked to the right accounts, and ready for posting or reversal.

Here are details for the each field in **General** FastTab; 

| Field                      | Description                                                                                     |
|--------------------------------|---------------------------------------------------------------------------------------------|
| Check payroll number       | Specify the system-generated number that uniquely identifies the journal header.                |
| Transaction code           | Specify the movement type (e.g., receipt, issue, return) using a predefined code.               |
| Journal batch number       | Specify the journal batch number that groups the transactions for posting.                      |
| Portfolio code             | Specify the portfolio in which the check or note is tracked (e.g., PA10101).                    |
| Account type               | Indicate the type of related account: Customer, Vendor, Bank, Ledger, or Portfolio.             |
| Account number             | Specify the associated account number for the selected account type.                            |
| Against transaction code   | Indicate the linked transaction code in case of offset (e.g., transfer between portfolios).     |
| Reversal date              | Indicate the date the reversal should occur, if applicable.                                     |
| Reversal journal number    | Indicate the ID of the reversal journal, if this transaction has been reversed.                 |
| Posted                     | Specify whether the transaction has already been posted to the general ledger.                  |
| Description                | Describe the purpose or context of the check/promissory note transaction.                       |
| Date                       | Specify the transaction date of the document.                                                   |
| Bank transaction type        | Specify the nature of the bank movement (optional).                                           |
| Payment reference            | Indicate the reference value associated with the payment.                                     |
| Payment ID                   | Specify an optional identifier for the payment.                                               |
| Activate fixed exchange rate | Indicate whether a fixed exchange rate should be applied to the transaction.                  |
| Fixed exchange rate type     | Specify the rate type used if fixed exchange rate is enabled.                                 |
| Exchange rate                | Specify the applicable fixed exchange rate.                                                   |
| Exchange rate type (Reporting Currency) | Specify the exchange rate type for the reporting currency context.                 |
| Exchange rate (Reporting Currency)       | Specify the exchange rate used for reporting purposes.                            |

## Create a received check or promissory note in Check and promissory journal

This section provides guidance for creating a new check or promissory note entry using the **New check** page in the **Check and promissory note journal**. 

This form is used when a new check or note needs to be registered into the system manually, such as when a check is received from a customer or issued to a vendor.
Users are required to define the document’s identity, financial values, due dates, associated accounts, and ownership information. 
This structured data ensures accurate posting to the general ledger and full lifecycle tracking of the processes.

Here are details of the fields in **Summary** FastTab **Check definition** page;  

| Field                    | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| Currency                 | Indicates the currency of the check or promissory note.                     |
| Check due date           | Indicates the maturity date on which the check or note is payable.          |
| Check printing number    | Specifies the physical number printed on the check or promissory note.      |
| Amount                   | Specifies the monetary value stated on the check or note.                   |
| Portfolio type           | Specifies the portfolio where the check or note will be tracked.            |
| Account type             | Specifies the type of offset account (e.g., Customer, Vendor, Ledger, Bank).|
| Account number           | Specifies the actual account number based on the selected type.             |
| Posting profile          | Indicates the posting profile to be used when creating ledger entries.      |
| Own check                | Specifies if the document is the company’s own check.                       |

Here are details of the fields in **General** FastTab **Check definition** page;  

| Field                        | Description                                                         |
|------------------------------|---------------------------------------------------------------------|
| Drawer                       | Enter the name of the person or company who wrote the check.        |
| Date drawn                   | Specify the date on which the check was written.                    |
| Guarantor                    | Specify the guarantor (used for promissory notes).                  |
| Signed                       | Enter the name of the signer of the document.                       |
| Bank groups                  | Select the bank issuing or receiving the document.                  |
| Branch code                  | Specify the branch code of the bank associated with the transaction.|
| Bank account for collection  | Specify the related bank account number stated on the check.        |
| Bank branches                | Specify the bank branch name issuing or receiving the document.     |
| Bank transaction type        | Indicate the nature of the related bank transaction (optional).     |
| Payment reference            | Optionally enter a payment reference code.                          |
| Payment ID                   | Specify an identifier for payment transactions.                     |
| Activate fixed exchange rate | Enable this field if a fixed exchange rate is to be used.           |
| Fixed exchange rate type     | Specify the type of exchange rate if the fixed rate is activated.   |
| Exchange rate                | Specify the actual exchange rate value if fixed rate is used.       |
| Exchange rate type (Reporting Currency) | Specify the exchange rate used when reporting in different currencies. |
	
After all relevant fields and values have been selected for the check or promissory note, Select **Save** and select **Check transfer journal** in ActionPane. 
Then you will see the check or promissory record in **Lines** Tab in the **Check and promissory note journal**. 
The **Lines** Tab displays all transactions associated with selected checks and promissory notes. 

This section provides guidance on using the **Transactions** FastTab in the **Lines** Tab of the **Check and promissory note journal**. 
The **Transactions** FastTab offers you the ability to review the details of the selected line, access open or settled transactions, and manage matching and cancellation activities directly from within the journal.

You can add new lines from **New check** again if it is needed, you can delete existing lines if needed by **Delete rows**. 

Here are the explanations of the each function in **Transaction** FastTab; 

| Action   | Description  |
|------|--------|
| Delete rows            | Deletes the selected lines. |
| Open transactions      | Displays the open transactions for the account associated with the selected journal line. You can mark the transactions to be settled. Once marked, the matching is completed automatically during posting. |
| Settle transactions    | Displays the transactions for the accounts         |
| Transactions           | Allows to view all posted financial transactions associated with a specific customer or vendor account. It provides a detailed ledger view of each transaction, including invoices, payments, credit notes, settlements, and adjustments. |

## Settle check and promissory note with open transactions

This section provides a detailed explanation of the **Open Transactions** page accessible from the **Lines** tab of the **Check and promissory note journal**. 
The page is used to settle checks and promissory notes payments with open transactions in customer or vendor accounts.

When settling a transaction using a received check or promissory note, you can manually enter an amount to perform a partial settlement. 
This allows you to apply only a portion of the check or note's value to the open transaction.

Here are the details of the each field in **Open transactions** page; 

| Field  | Description |
|--------------------------|----------------|
| Marked                   | Indicates the open transaction to be settled by marking its checkbox. |
| Customer or vendor       | Indicates whether it is a customer or vendor transaction. |
| Account Number           | Specifies the account number associated with this transaction. |
| Name                     | Enter or display the name associated with this account number, typically a customer or vendor name.  |
| Currency                 | Indicates the currency used for this transaction, such as TRY or EUR. |
| Amount                   | Specifies the total amount involved in this transaction in its respective currency value. |
| Open amount              | Specifies any remaining open amount that has not yet been settled for this transaction.|
| Remaining amount         | Indicates any remaining balance after partial settlements have been made on this transaction. |
| Amount to settle         | Specifies how much of this amount is intended to be settled during current processing. |
| Amount of manual settlement | Indicates any manually entered settlement amounts applied towards clearing balances. |
| Date                     | Specifies the date when action was taken on transactions such as settlement entries. |
| Due date                 | Specifies the due date by which the transaction is expected to be settled. |
| Invoice                     | Specifies the invoice number related to the customer or vendor transaction.  |
| Voucher                | Specifies the voucher number associated with the customer or vendor transaction. |

After marked any open transaction, select **Save** and close the page. 
When transferring checks or promissory notes between portfolios for collection or payment purposes, you must select the portfolio that contains the relevant check or promissory note. 
To do this, select **Select check**. 

## Sent check or promissory note to portfolio account

This section provides an overview of the **Select check** page, which allows users to retrieve and transfer previously registered check or promissory note records into the journal for further processing. 
The form displays eligible documents based on the selected portfolio and currency, ensuring accurate classification and compliance with Turkish financial processes.

This form allows users to select commercial paper documents to be transferred into the journal for processing. 
The list of records is filtered depending on the document type and its most recent transaction status:

- **Received checks and promissory notes:** The page displays documents that belong to the selected portfolio and have a last transaction code of type receipt.
- **Given checks and promissory notes:** Only documents that have been written but not yet collected are listed.

Here are the details for each field in **Overview** FastTab;

| Field   | Description    |
| ------------ | ----------------- |
| Currency                | Specifies the currency in which the check is issued.   |
| Check due date          | Specifies the date on which the check is due to be paid.  |
| Check printing number   | Specifies the number physically printed on the check.  |
| Amount                  | Specifies the monetary value of the check.  |
| Portfolio type          | Indicates whether the check is received or issued.  |
| Check payroll number    | Specifies the system-generated identifier for the payroll check.  |
| Account type            | Indicates whether the check is associated with a **Customer** or **Vendor** account. |
| Account number          | Specifies the relevant account number linked to the transaction. |
| Posting profile         | Specifies the posting profile to be used for generating ledger entries related to this transaction. |
| Own check | Specifies that the check is issued by the organization. |

Here are the details for each field in **Receipt checks** Fasttab; 

| Field      | Description  |
| --------- | ----------|
| Drawer     | Specifies the name of the person or company that issued the check. |
| Date drawn | Indicates the date when the check was issued or drawn. |
| Guarantor  | Specifies the name of the guarantor, if applicable, responsible for the check payment. |
| Signed     | Indicates whether the check has been signed.  |
| Bank groups | Specifies the grouo of the bank where the check was drawn.  |
| Branch code | Specifies the bank branch code where the check was drawn. |
| Bank branches | Specifies the bank branch name which the check is issued.  |

To sent the check or promissory note to the portfolio, select **Check transfer journal** and close the page.
Then, you can select **Post** to generate voucher.

After you posted the journal to access the ledger journal and the voucher, select **Journals** in the **Daily** group. 

## Reverse check and promissory note journal

This section explains how to reverse a posted check and promissory note journal.
When you select the **Reverse journal** button on a posted check or promissory note journal, the system automatically creates a reversal journal that mirrors the original journal. 
The reversal is posted to the ledger and is linked to the original journal header to ensure full traceability.

To reverse the journal, follow these steps; 

- Go to **Cash and bank management > Check and promissory note operations > Check and promissory note journal**.
- Select a posted journal that you want to reverse
- Select **Check reversal journal** in **Cancel** group.
- Select **OK** in dialog page.
- Enter or select a date in **Date** field.
- Select **OK** to post the reversal journal. 

The reversal check journal is linked to the original check journal. 
The related reverse transaction can be accessed through the **Reversal journal ID** field in the **Check and promissory journal** list page.

## Creation of company checks and promissory notes and monitoring documents

This section provides guidance on how to view, filter, and manage check and promissory note records and how to create company checks and promissory notes for payments using the **Check and promissory note definitions** page in Dynamics 365 Finance. 
This page offers a centralized view where all received or given checks and promissory notes are listed with key attributes such as type, amount, due date, portfolio, account, and transaction codes. 
It helps ensure accurate document tracking and supports financial transparency in the check lifecycle.

Also, ensures to create company checks or promissory note for payments in Türkiye.

The **Check and promissory note definitions** page is used to:

- View and manage all previously defined check and promissory note documents.
- Filter checks based on attributes such as transaction type, due date, portfolio, account, or currency.
- Track the lifecycle of each check or promissory note including status, portfolio assignment, and associated transactions.
- Access related information such as printing number, account details, and movement records.
- Create and update company checks or promissory notes for payments. 

You can use the following filtering parameters to easily track all check and promissory note documents registered in the system:

| Parameter        | Description                                                           |
| ---------------- | ----------------------------------------------------------------------|
| Check type       | Specifies whether to view received or issued checks.                  |
| Receipt or issue | Specifies whether the last transaction was a receipt or issuance.     |
| Return           | Specifies whether the check has been returned.                        |
| Collection       | Specifies whether the check is in the collection process.             |
| Bounce check     | Specifies if the check has been marked as bounced.                    |
| Transaction code | Specifies the last transaction code used on the check.                |
| Portfolio code   | Filters checks based on their assigned portfolio.                     |
| Account type     | Specifies whether the related account is a customer, vendor, or bank. |
| Bank groups      | Filters by associated bank group.                                     |
| Account number   | Specifies the related customer/vendor/bank account.                   |

Select **Apply filter** to refresh the list based on the selected parameters.
You can see the all details about the checks and promissory notes. 

Here are the details for the each field of the **Check and promissory note definitions** page; 

| Field                  | Description                                                          |
|------------------------|----------------------------------------------------------------------|
| System number of check | Displays the internal unique number of the check or promissory note. |
| Check type             | Indicates whether the document is a received or company (given) check.|
| Check printing number  | Specify the number physically printed on the check.                   |
| Due date               | Displays the check’s maturity date.                                  |
| Due days               | Displays the number of days between the entry date and the due date. |
| Currency               | Displays the transaction currency (e.g., TRY, EUR).                  |
| Amount                 | Displays the value of the check or promissory note.                  |
| Cancel                 | Indicates whether the check has been cancelled.                      |
| Portfolio code         | Displays the assigned portfolio to which the check belongs.          |
| Transaction code       | Shows the last applied transaction code on the check.                |
| Portfolio entry date   | Indicates the date when the check was entered into the portfolio.    |
| Own check              | Specifies if this is an internally issued check (owned by the company).  |
| Account type           | Displays the type of account related to the check (e.g., Customer, Bank).|
| Account number         | Shows the related customer/vendor/bank account.                      |
| Name                   | Displays the name of the related customer/vendor/bank.               |
| Check payroll number   | Shows the payroll reference number to which the check is assigned.   |
| Check movement number  | Shows the last movement document number associated with this check.  |
| Is in use              | Indicates whether the check is currently being used in a transaction.|

### Create company checks or promissory notes for operations

This section provides guidance for creating new check or promissory note records using the **Create a new document** pane on the **Check and promissory note definitions** page in Dynamics 365 Finance. 
This functionality is part of the Turkish localization and supports the mass generation of blank checks with predefined structure and numbering logic.

The form enables users to define portfolio ownership, numbering format, and bank association. 
Once completed, the new check documents are created and automatically added to the system, ready for operational use in payment or collection processes.

Here are the details of the each field in **Create a new document** page; 
    
| Field                       | Description                                                                                      |
| --------------------------- | ------------------------------------------------------------------------------------------------ |
| Portfolio code              | Specifies the portfolio where the newly created checks or notes will be recorded.                |
| Bank groups                 | Specifies the bank group to which the checks belong.                                             |
| Bank account for collection | Indicates the bank account that will be associated with the collection of these checks.          |
| Bank branches               | Specifies the relevant branch of the bank where the checks are held.                             |
| Starting number             | Specifies the starting numeric value to be used when generating the check numbers.               |
| Number of digits            | Defines how many digits will be included in the numeric part of the check number (e.g., 3 → 001).|
| Check printing number       | Specifies a prefix or format that will appear as the printed check number.                       |
| Unit to be created          | Indicates the total number of check or note records to be generated using the specified pattern. |

> [!NOTE]
> In the **Portfolio code** parameter, only the portfolio codes with a **Portfolio type** of **Check given** or **Promissory note given** from the **Check and promissory note portfolio codes** page are listed.

You can create company checks and promissory notes by following the steps below; 

1. Go to **Cash and bank management > Inquiries and reports > Check and promissory note operations > Check and promissory note definitions**.
2. Select **New**.
3. Select **Create promissory note** or **Create check** options that you need.
4. In the **Create a new document** page;
5. Select the portfolio code to which the check or promissory note will be assigned in the **Portfolio code** parameter.
6. Select the bank group to which the check or promissory note belongs in the **Bank groups** parameter.
7. Select the bank branch that will be associated with the collection of checks.
8. Define the **Starting number** as "1" and **Number of digits** as "3", resulting in check numbers like CHC-001, CHC-002, CHC-003 etc.
9. Type a printing number such as "CHC-", in the **Check printing number** field.
10. Type the number of unit to be created as "3".
11. Select **OK** to create.

These checks or promissory notes will now be listed in the **Check and promissory note definitions** page, ready for transaction use in the **Check and promissory note journal**.

### Update check or promissory note information

This section provides guidance on updating existing check or promissory note records using the Update check or promissory note function in the Check and promissory note definitions page in Microsoft Dynamics 365 Finance. 

This function is used when a previously registered check or promissory note needs to be corrected or updated with new values, such as changing the portfolio, amount, or due date.
When you want to update the check or promissory note **Check or promissory note update**; 

1. Select check or promissory note that you want to update in the list.
2. Select **Check or promissory update**.
3. Update the portfolio code in Portfolio code parameter if it is needed.
4. Enter or update the amount of the check or promissory note in **Amount** field.
5. Enter or update the due date in **Due date** field.
6. Select **Update**. 

> [!NOTE]
> To use the generated company checks or promissory notes in the **Check and promissory note journal**, you must enter the **Amount** using the **Check and promissory note update** function.

**Cancel** action allows you to invalidate checks or promissory notes that have not been used in any financial transactions or that have been returned. 
This action is only available for documents that meet the cancellation criteria based on their current status.

You can use the **Check or promissory note transactions** to acces the transactions for the relevant check or promissory note. 

## Configure rediscount calculations for check and promissory note operations

This section provides guidance on performing rediscount calculations for checks and promissory notes using the Rediscount Calculation page in Microsoft Dynamics 365 Finance. 

Rediscounting is a financial operation in Türkye, typically performed at the end of a fiscal period to reflect the current value of checks and promissory notes that have not yet matured.
The Rediscount calculation feature in Dynamics 365 Finance allows organizations to compute interest income or expenses for postdated commercial papers and reflect them accurately in the general ledger.

The rediscount calculation functionality helps to:

  - Calculate interest income for receivable checks and promissory notes.
  - Calculate interest expense for payable checks and promissory notes.
  - Generate rediscount journal entries automatically.
  - Reverse rediscount journals in the following fiscal period.

**Accounts** FastTab is used to define the ledger accounts for receivable and payable rediscount transactions. 
The default accounts are retrieved automatically from the **Check and promissory note parameters**.

The journal numbers for the current period and the next period, including those used for reverse posting, are displayed for reference in **Posting** FastTab.
You can see the informations about the check and promissory notes after rediscount calculation in **Lines** FastTab.

Here are the details of the each field; 

| Field                          | Description                                        |
|--------------------------------|----------------------------------------------------|
| System number of check         | Displays the unique number assigned to each check.  |
| Check printing number          | Specifies the date when the check was received. |
| Portfolio type                 | Indicate the type of portfolio associated with the check, such as received or issued. |
| Portfolio code                 | Specifies the portfolio code of the check or promissory note. |
| Transaction code               | Specifies the code that represents the type of transaction being recorded. |
| Transaction name               | Specifies the name of the transaction code. |
| Transferring customer          | Specifies the customer account that originally submitted the check or promissory note when it was first entered into the system. |
| Transferring customer name     | Specifies the customer name of transferring customer.   |
| Own check                      | Specifies if the document is the company’s own check. |
| Currency                       | Displays currency of the check or promissory note.  |
| Amount in transaction currency | Displays the amount of the check or promissory note in transaction currency.  |
| Check due date                 | Indicates the due date of the check or promissory note. |
| Due day by reference date      | Indicates the day difference between check due date and reference date. |
| Exchange rate                  | Indicates the currency exchange rate in which the check amount is due.  |
| Rediscount amount              | Specifies the rediscount amount after rediscount calculation. |

### Define interest rates for rediscount calculation

This section provides guidance on defining interest rates that will be used during rediscount calculations for checks and promissory notes in Dynamics 365 Finance. 
Rediscount interest rates are applied to checks and promissory notes that have not yet matured at the end of a fiscal period.

By defining the interest rates, organizations ensure accurate rediscount value calculations and proper posting to general ledger accounts.
You can define the interest rates in currency basis for the check or promissory notes.

Here are the details of each field in **Interest rates** page;

| Field             | Description                                             |
| ----------------- | ------------------------------------------------------- |
| Date              | Specifies the reference date of interest rate.          |
| Currency          | Specifies the currency of the interest rate.            |                          
| Interest rate (%) | Indicates the interest rate for rediscount calculation. | 

> [!NOTE]
> Ensure that the legal rediscount rate has been published by the Central Bank of the Republic of Türkiye (CBRT).

## Calculate rediscount amount for checks and promissory notes

This section provides an overview of the rediscount calculation logic for checks and promissory notes in Dynamics 365 Finance, specifically within the Turkish localization.

Rediscounting is a financial adjustment process applied to post-dated checks and promissory notes that have not yet matured at the end of a fiscal period. 
The purpose of this process is to reflect the time value of money by rediscounting the future receivable or payable to its present value.

In Türkiye, rediscount calculations are typically performed at month-end or year-end for both customer (receivable) and vendor (payable) documents. The system calculates the rediscount amount based on three key factors:
  
  - The number of remaining days until maturity
  - The applicable interest rate
  - The nominal value of the document

By automating rediscount journal postings and reversals, Dynamics 365 Finance enables organizations to maintain compliant and accurate financial records while reducing manual work. 
Rediscount entries are generally reversed in the following fiscal period, restoring the original document value after reporting requirements have been fulfilled.

Here are the details of the parameters in **Check and promissory note rediscount calculation** page;  

| Field                  | Description                                                                                |
|------------------------|-----------------------------------------------------------------------------------------------|
| Version ID             | Specifies the version code for the period in which the discount calculation will be performed. |
| Current reference date | Defines the reference date for the discount calculation. The period reference date must be the last day of the month. |
| Next reference date    | Defines the reference date for the next period's discount calculation. The next period reference date must be the first day of the month and cannot be before the period reference date. The system will record a reverse entry for this date. |
| Exchange rate type     | Specifies the type of currency for foreign currency checks and notes. The value defined in the check-note parameters is used as the default.     |
| Detail level           | Specifies the level of detail for the journal entry when the discount values are posted. The value defined in the check-note parameters is used as the default. |
| Journal name           | Specifies the journal that will be used to post the rediscount transaction. |
| Posted                 | Indicates whether the rediscount journal has been successfully posted. |

To create a rediscount calculation, follow the steps below; 

  1. Go to **Cash and bank management > Inquiries and reports > Check and promissory note operations > Check and promissory note rediscount calculation**.
  2. Define the interest rate for the relevant period in **Interest rates** page and select **Save** and close the page.
  3. Select **New**.
  4. Type a **Version ID** manually.
  5. In the **Current reference date** parameter, enter or select a date.
  6. In the **Next reference date** parameter, enter or select a date.
  7. Select or update the exchange rate type in the **Exchange rate type** parameter if it is needed.
  8. Select an option for calculation in **Detail level** parameter.
  9. Select a journal name for posting the calculation results in the **Journal name** parameter.
  10. Select **Save**.
  11. Select **Calculate** to calculate the rediscount amounts.
  12. Select **Post**. 

After posting process, you can see the journals in **Journals** group in **Postings** FastTab.
If you want to reverse the rediscount journals, select **Reverse** in ActionPane. You can see the reversal journal in **Reversal journals** group in **Postings** FastTab.

## Check or promissory note transactions

This page provides a list of all posted transactions related to checks and promissory notes. It also enables tracking and monitoring of these financial documents.
It allows you to define and manage the types of movements that can be applied to checks and promissory notes in the system.

Each transaction code represents a financial operation such as:

- Receiving a check/note from a customer
- Issuing a promissory note to a vendor
- Transferring a check between portfolios
- Endorsing or protesting a note
- Handling collection, return, or bounce

To access the Check or promissory note transactions, go to **Cash and bank managament > Inquiries and reports > Check and promissory note operations > Check and promissory note transactions**. 

Here are the details for the **Overview** FastTab; 

| Field | Description |
|------|-------|
| Check movement number           | System-generated number for tracking the movement of checks. |
| System number of check          | Unique identifier assigned by the system to each check.  |
| Check printing number           | Number assigned to a check when it is printed. |
| Check type                      | Specifies the type of check (e.g., received, issued). |
| Portfolio code                  | Code representing the portfolio to which the check belongs. |
| Name                            | Name associated with the transaction.  |
| Transaction code                | Code representing the type of transaction.  |
| Check due date                  | Date by which the check is due. |
| Currency                        | Currency in which the check is issued. |
| Amount                          | Amount of the check. |
| Account type                    | Type of account involved in the transaction (e.g., customer, vendor). |
| Account number                  | Account number associated with the transaction. |
| Posting profile                 | Profile used for posting the transaction. |
| Date                            | Date of the transaction. |
| Journal batch number            | Batch number of the journal entry. |
| Voucher                         | Voucher number associated with the transaction. |
| Posted                          | Indicates whether the transaction has been posted. |
| Is in use                       | Indicates whether the check is currently in use. |
| Check reversal transaction number | Transaction number for the reversal of the check. |

Here are the details for the **General** FastTab; 

| Field | Description |
|------|-------|
| Bank transaction type           | Specifies the type of bank transaction.           |
| Payment reference               | Reference number for the payment.                 |
| Payment ID                      | Unique identifier for the payment.                |
| Fixed exchange rate             | Indicates whether a fixed exchange rate is used.  |
| Activate fixed exchange rate    | Option to activate the fixed exchange rate.       |
| Fixed exchange rate type        | Type of fixed exchange rate used.                 |
| Exchange rate                   | Exchange rate applied to the transaction.         |
| Reporting currency              | Currency used for reporting purposes.             |
| Exchange rate type              | Type of exchange rate used.                       |

Here are the details for the buttons in **Check or promissory note transactions** page;

| Button | Description |
|------|-------|
| Reverse transaction  | Allows you to reverse a  posted transaction.  |
| Check and promissory note definitions | Access the definitions and parameters set for checks and promissory notes. |
| Check and promissory note journal | Access the check and promissory note journal entries.|
| Journal | Access the posted check and promissory note journal entries related to checks and promissory notes.|

The **Check and promissory note** feature in Dynamics 365 Finance helps businesses manage all steps related to checks and promissory notes. 
You can easily create, record, transfer, and track these documents throughout their lifecycle.

This module supports using automated processes like transaction codes and rediscount calculations. You can quickly see the status of each document and make sure records are accurate..

Using this feature improves control, ensures compliance, and makes check and promissory note operations easier and more reliable.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
