---
title: Enable cash flow forecasting
description: Learn how to configure the Cash flow forecasts feature in Finance Insights, including a step-by-step process detailing how to enable this setting.
author: ShivamPandeyMSFT
ms.author: shpandey
ms.topic: how-to
ms.date: 10/11/2023
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-07-24
ms.search.form: 
ms.dyn365.ops.version: AX 10.0.13
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
---

# Enable cash flow forecasting

[!include [banner](../includes/banner.md)]

This article explains how to configure the Cash flow forecasts feature in Finance insights.

> [!NOTE]
> To use payment predictions in the cash flow, you must set up the Customer payment predictions feature as described in [Enable customer payment predictions](enable-cust-paymnt-prediction.md).
  
1. Go to **Cash and bank management \> Cash flow forecast setup**, and add the liquidity accounts that should be included in the forecasts. Also set up the liquidity account for payments on the **Accounts receivable** and **Accounts payable** tabs. Be sure to recalculate the cash flow forecast.

    > [!NOTE]
    > If liquidity accounts aren't set up, the cash flow can't be generated.
    >
    > For more information about how to set up cash flow forecasts, see [Cash flow forecasting](../cash-bank-management/cash-flow-forecasting.md).

2. Go to **Cash and bank management \> Setup \> Finance Insights \> Cash flow forecasts**, and follow these steps:

    1. On the **Cash flow forecast** tab, select **Enable feature**.
    2. Select **Create prediction model**.

> [!NOTE]
> The **Cash flow forecast** model training requires data with 100 or more transactions that span more than one year. We recommend that you have at least two years of data with more than 1,000 transactions.

For more information about the cash flow forecasting capability, see [Cash flow forecasting](cash-flow-forecast-intro.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
