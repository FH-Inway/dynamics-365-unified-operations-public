---
title: Document class letter for Latin America
description: Learn about the document class letter configuration for Latin America, including prerequisites and and outline for setting up a document class letter.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 07/01/2024
ms.custom: bap-template
ms.reviewer: johnmichalak 
---

# Document class letter for Latin America

[!include [banner](../../includes/banner.md)]

You can create the letter codes that are part of the fiscal documents configuration which is used in transactions with third parties.

Document classes without a letter configuration are supported. If a document class doesn't have a letter configuration, the **Prefix** field must be left blank.

## Prerequisites

Before you can create the letter codes for the configuration, the length of the document class letter prefix must be configured on the **LATAM Parameters** page.

## Set up a document class letter

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class letter**.
2. In the **Document class letter Id** field, enter a code to identify the register that's being created.
3. In the **Description** field, enter a description of the document class letter.

    > [!NOTE]
    > The **Document class letter Id** and **Description** fields are mandatory.

4. Complete the prefix by specifying the letter or letters that are required to identify the document class.
5. On the Action Pane, select **Save**.
