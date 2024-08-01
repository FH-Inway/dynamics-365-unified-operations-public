---
title: Margin price adjustments (preview)
description: Learn how to set up and use margin price adjustments, including a list of configuration you must complete to use margin component price adjustments.
author: sherry-zheng
ms.author: chuzheng
ms.topic: how-to
ms.date: 04/03/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.region: Global
ms.search.form: GUPPriceComponentCode, GUPPriceComponentCodeSetup, GUPPricingTree, RetailPeriodicDiscount, GUPParameters
---

# Margin price adjustments (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article describes how to set up and use margin price adjustments.

Pricing management lets you use *margin price adjustments* to move item prices up or down from the base price. You can set up these adjustments by including one or more price component codes of the *Margin component price adjustment* type in your price structures. Price adjustments are compounded across price component codes and add up to the total price adjustment.

In scenarios where you build your selling price based on the inventory standard cost or purchase price, it represents the layers of the margin components that add up to those base prices.

Margin component price adjustments can be associated with many types of agreements, promotions, and events. They let you easily adjust prices without changing the base price.

To use margin component price adjustments, you must complete the following configuration:

- Create one or more [price component codes](price-component-code.md) to set up the different types of margin price adjustments that you can include in your price structures.
- Create one or more [price structures](price-structure-overview.md) to define how your margin price adjustments combine with other price elements (such as base prices and discounts) to determine the final unit price.
- Set up one or more [margin price adjustment pricing rules](margin-discount-pricing-rules.md) to configure the margin price adjustments that you need, and to define which customers and items they apply to, and how they're calculated. You'll associate each price adjustment with a specific price component code and then define the details of the calculation.

For information about how to create pricing rules for each margin price adjustment (and discount), see [Pricing rules for discounts and margin price adjustments](margin-discount-pricing-rules.md).

For example, the following illustration shows a price structure that contains two sequential margin component price adjustments (*General price adjustments* and *Seasonal price adjustments*).

[<img src="media/price-component-code-setup.png" alt="Price structure on the Price component code setup page." title="Price structure on the Price component code setup page" width="720" />](media/price-component-code-setup.png#lightbox)
