---
title: Import customer payment with JBA file format
description: Learn how to import EFT files with a JBA file format for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransCustPaym, SrsReportViewerForm
ms.dyn365.ops.version: Version 7.0.0
---

# Import customer payment with JBA file format

[!include [banner](../../includes/banner.md)]

This article explains how to import electronic funds transfer (EFT) files with a Japanese Bankers Association (JBA) file format for Japan in Microsoft Dynamics 365 Finance.

In Japan, the JBA file format is commonly used for EFT among banks. 

The following procedure was created using the demo company data JPMF.

To import EFT files with a JBA file format, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Payments \> Payment journal**.
1. Select **New**.
1. In the **Name** field, enter "CustPay".
1. Select **Lines**.
1. Select **Functions**.
1. Select **Import payments**.
1. In the **Method of payment** field, enter a value. For example, enter the method of payment that uses JBA(JP) - Format A.  
1. Select **OK**.
1. Select the file to upload.  
1. Select **OK**.
1. Close the report. The payment amount and description are imported and a control report is generated.  
1. In the **Account** field, enter "JPMF-000001".
1. Select **Post**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
