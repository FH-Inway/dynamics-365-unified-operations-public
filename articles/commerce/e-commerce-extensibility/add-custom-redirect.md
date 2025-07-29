---
title: Redirect category and product pages to canonical URLs (preview)
description: Learn how to redirect category and product pages to canonical URLs by extending modules in the Microsoft Dynamics 365 Commerce online SDK.
author: krishnabh
ms.date: 07/30/2025
ms.topic: how-to
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: krishnabh
ms.search.validFrom: 2025-04-07
ms.custom: 
  - bap-template
---

# Redirect category and product pages to canonical URLs (preview)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article explains how to redirect category and product pages to canonical URLs by extending modules in the Microsoft Dynamics 365 Commerce online SDK.

This ensures that users and search engines consistently access the clean, intended version of each page.  

## Importance of canonical URLs 

In the Commerce SDK, category and product pages can be accessed through URLs that include unnecessary or random segments. While these URLs are technically valid, they can lead to:

- Duplicate content issues.
- Poor search engine optimization (SEO) performance.
- Confusing user experiences.

Redirecting to canonical URLs helps maintain a consistent structure, improves search engine indexing, and enhances overall site usability.   

## Prerequisites

- A functioning Dynamics 365 Commerce online SDK environment.
- Familiarity with extending modules.

## How canonical redirects work 

The canonical url redirects works by doing the following:  

- Detecting when the requested URL doesn't match the canonical format.  
- Throwing an instance of HttpRedirectException class with the correct URL set in the **Location** property.  
- Halting further rendering and initiating a redirection to the canonical URL.  

If a user accesses a product page using a noncanonical URL, the module should detect and redirect them to the correct canonical URL. 

For the following example, the module detects the extra `<unecessaryparameter>` segment of the requested URL and issues a redirect to the clean, canonical URL. 

- **Requested URL**: `https://www.fabrikam.com/womens-clothing/<unecessaryparameter>/45678.p` 
- **Canonical URL**: `https://www.fabrikam.com/womens-clothing/45678.p` 

## Implement a custom redirect within a module 

To implement a custom redirect within a module, throw an instance of the HttpRedirectException class at the appropriate location in the module. This action halts the rendering of subsequent modules and initiates a redirect to the URL specified in the **Location** property of the HttpRedirectException class. 

## Example

All e-commerce site pages hosted on the Dynamics 365 Commerce domain include a canonical URL in the HTML `<meta>` tags by default. To implement a redirect based on this canonical URL, you must identify the module responsible for generating it and insert your redirect logic there.

In this example, the category page template uses the category page summary module to generate its canonical URL. The category page summary module references the default page summary module view file, so adding conditional redirect logic in the default page summary module ensures the that redirect occurs wherever category pages are used. 

**Step 1 - Customize the default page summary module**: In the default-page-summary-extension.tsx file (src\modules\default-page-summery-extension\default-page-summary-extension.tsx), customize the default page summary module and implement custom logic to throw the HttpRedirectException error, as shown in the following code sample.

```typescript
import { HttpRedirectException } from '@msdyn365-commerce/core-internal';

if (canonicalUrl && context && context.request && context.request.url && canonicalUrl !== context.request.url.requestUrl.href) {
    const e = new HttpRedirectException(canonicalUrl);
    e.StatusCode = 302 
    throw e;
}
});
```

**Step 2 - Customize the category page summary module**: In the category-page-summary-extension.definition.json file (src\modules\category-page-summary-extension\category-page-summary-extension.definition.json), customize the category page summary module and update the module definition to point to your custom view, as shown in the following code sample.

```json
"module": {
		"view": "../default-page-summery-extension/default-page-summary-extension"
	}
```

**Step 3 - Edit the category page template**:  In the category page template in Dynamics 365 Commerce site builder, replace references to the category page summary module with the custom category page summary extension module. 

> [!NOTE]
> When you implement bulk redirects alongside canonical redirects, take care to avoid creating infinite redirect loops. 

## Additional resources

[Module library overview](../starter-kit-overview.md)

[Page summary module](../dev-itpro/page-summary-module.md)

[Meta tags module](../dev-itpro/metatags-module.md)

[Default page module](../dev-itpro/default-page-module.md)

[Extend module definition](extend-module-definition.md)

[Create new module](create-new-module.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
