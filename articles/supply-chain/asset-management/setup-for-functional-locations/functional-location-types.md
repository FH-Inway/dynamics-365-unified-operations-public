---
title: Functional location types
description: Learn how to create functional location types in Asset Management, including an outline and step-by-step process on creating a default functional location type.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 06/13/2025
ms.custom: 
  - bap-template
---

# Functional location types

[!include [banner](../../includes/banner.md)]

This article describes how to create functional location types in Asset Management. Functional location types are used to manage requirements for functional locations, including how assets are installed on a functional location. You can set up asset types, maintenance plans, functional location attributes, and asset attribute requirements to be used on a functional location that uses the specific functional location type. When you create a functional location, the functional location type is mandatory.

> [!NOTE]
> To work with functional locations, you must create a default functional location to be used only for the purpose of creating new assets. For that default functional location, you should create a default functional location type that is simple and allows multiple assets to be installed on the default functional location. To learn more about how to set up functional locations, go to [Create functional locations](../functional-locations/create-functional-locations.md).

## Create a default functional location type

This procedure shows how to create a default functional location type to be used for a default functional location.

1. Select **Asset management** \> **Setup** \> **Functional locations** \> **Functional location types**.
2. Select **New** to create a functional location type.
3. Insert a functional location type ID in the **Functional location type** field, for example, *Default*, and a name in the **Name** field.
4. Select a lifecycle model in the **Functional location lifecycle model** field.
5. Select *Yes* on the **Multiple assets** toggle button to allow more assets to be installed on a functional location (the default functional location) using this type.

Now, the default functional location type to be used only on a default functional location is created. You shouldn't add any more requirements or restrictions to this default functional location type.

## Create Functional Location Types

1. Select **Asset Management** \> **Setup** \> **Functional locations** \> **Functional location types**.
2. Select **New** to create a functional location type.
3. Insert a functional location type ID in the **Functional location type** field and a name in the **Name** field.
4. Select a lifecycle model in the **Functional location lifecycle model** field. To learn more about functional location lifecycle states and lifecycle models, go to [Functional location lifecycle states](../setup-for-functional-locations/functional-location-stages.md).
5. Select *Yes* on the **Multiple assets** toggle button if it should be possible to install several assets on a functional location using this functional location type. If you select *No*, you can only install *one* asset on a functional location using this functional location type.
6. Select *Yes* on the **Update asset dimension** toggle button if you want assets installed on a functional location of this type to automatically use the financial dimensions related to the functional location. This means that if you change financial dimensions in the [Create functional locations](../functional-locations/create-functional-locations.md) form, and the functional location uses a functional location type with this toggle button set to *Yes*, financial dimensions are automatically updated on all assets installed on that functional location.
7. The **Asset type** field is used if you want to automatically create *one* asset for the functional location with the same ID and name as the functional location you're creating. For example, this might be relevant if you create a static functional location, such as a building or a pipeline. In that case, select the asset type you want to use for the automatically created asset. Remember that if you make a selection in this field, the **Multiple assets** toggle button must be set to *No*.
8. On the **Asset types** FastTab, select the asset types to be related to the functional location type. Select **Add line** and select the asset types. If you add asset types here, only assets using those asset types can be installed on a functional location using this functional location type. If no asset types are selected on the **Asset types** FastTab, all asset types might be installed.
9. On the **Maintenance plans** FastTab, select the maintenance plans that should automatically be set up on new functional locations using this functional location type. Select **Add line** and select the maintenance plans. If you add maintenance plans here, only those plans can be used on a functional location using this functional location type.
10. On the **Asset attribute requirements** FastTab, set up the asset attributes that should automatically be set up on new functional locations using this functional location type. Select **Add line** and select the attribute. These attribute requirements function as guidelines. They aren't validated against attributes set up on an asset (to see the attributes, go to **Asset management** \> **Assets** \> **All assets**, select an asset in the list page, and on the Action Pane, open the **General** tab and select **Attributes**). The attribute requirements are shown when you install assets on functional locations.
11. On the **Permitted types** FastTab, select the functional location types that should be valid for sub functional location types related to a parent functional location type, which uses the selected functional location type.
12. On the **Attributes** FastTab, select the functional location attributes that should automatically be set up on functional locations using this functional location type. Select **Add line** and select the attribute.

>[!NOTE]
>On the **General** FastTab, you can get an overview of the number of asset types, maintenance plans, asset attribute requirements, permitted types, attributes, and functional locations set up on the functional location type. The **Functional locations** field shows the number of functional locations that use the functional location type. You can use the **Copy** button to copy settings from a functional location type to the selected functional location type.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
