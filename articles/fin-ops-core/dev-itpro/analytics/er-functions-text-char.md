---
title: CHAR ER function
description: Learn about how the CHAR Electronic reporting (ER) function is used, including syntax strings, arguments, return values, usage notes, and examples.
author: kfend
ms.author: filatovm
ms.topic: article
ms.date: 12/12/2019
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
---

# CHAR ER function

[!include [banner](../includes/banner.md)]

The `CHAR` function returns a *String* value that presents a single character that is referenced by the specified Unicode number.

## Syntax

```vb
CHAR (number)
```

## Arguments

`number`: *Integer*

A number that corresponds to an expected single character.

## Return values

*String*

The resulting text value.

## Usage notes

The string that this function returns depends on the encoding that is selected in the parent **FILE** format element. For a list of the supported encodings, see [Encoding class](/dotnet/api/system.text.encoding).

## Example

`CHAR (255)` returns **"ÿ"**.

## Additional resources

[Text functions](er-functions-category-text.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
