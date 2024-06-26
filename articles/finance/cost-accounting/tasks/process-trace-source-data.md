--- 
title: Process and trace source data
description: Learn about how you can process and trace source data and the origin of a specific cost entry, including a step-by-step process detailing how to process data.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 03/27/2023
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form:
ms.dyn365.ops.version: AX 7.0.0 
---

# Process and trace source data

[!include [banner](../../includes/banner.md)]

All data processing is run by jobs. For each job and data provider, a journal is created to document that the process has been run, and that the entries were processed in the current job. Use this procedure to set up a data source and then  trace the origin of a specific cost entry. This recording uses the USP2 demo data company USP2. Before you complete this task, make sure that you play the following task guides: "Create a cost accounting ledger," "Define cost control units," and "Manage data source for the cost accounting ledger."

1. Go to **Cost accounting > Ledger setup > Cost accounting ledgers**.
2. In the list, find and select the desired record.
    * Select the cost accounting ledger that you created earlier.  
3. Click **Actual versions**.
4. On the Action Pane, click **Source data processing**.
5. Click **General ledger entry transfer journals**.
6. In the list, find and select the desired record.
7. Click **Journal entries**.
8. In the list, mark the selected row.
9. Click **Cost entries**.
10. Click **Source entry**.
11. On the Action Pane, click **Source data processing**.
12. Click **General ledger**.
13. In the **Fiscal calendar period** field, enter or select a value.
    * For this example, select Fiscal 2017 Period 9.  
14. Click **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
