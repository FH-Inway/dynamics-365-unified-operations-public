--- 
title: Set up Form I-9 document types
description: Access a procedure that shows how to view and set up document types that are used for I-9 verification, including a step-by-step process. 
author: ShielaSogge
ms.author: shielas
ms.topic: how-to
ms.date: 06/04/2025
ms.custom:
ms.reviewer: twheeloc  
audience: Application User 
ms.search.region: USA
ms.search.validFrom: 2016-06-30
ms.search.form:
ms.dyn365.ops.version: AX 7.0.0 
---

# Set up Form I-9 document types

[!include [banner](../../../../includes/banner.md)]

This procedure shows how to view and set up document types that are used for I-9 verification. Before you set up I-9 document types, you must also set up the issuing agencies and identification types. The demo data company used to create this procedure is USMF, which includes examples of the issue agencies and identification types that are needed to complete the procedure.

1. Go to **Human resources \> Workers \> I-9 \> I-9 document types**.
2. Select **New**.
3. In the **I-9 document type** field, enter a value. For example, enter **School ID**.
4. Select the identification type. For example, select **School ID**.

    Examples of identification types include a Social Security number (SSN), visa number, passport ID, and driver's license.

5. Select the I-9 document list that is used for the document type.

    As part of the I-9 process, employees must present documentation that shows the employer their identity and employment authorization. The [US Citizenship and Immigration Services website](https://www.uscis.gov) contains information about which documents are acceptable, and which list they belong to.

6. In the **Form** field, enter the official form number for the document type. For example, enter **School ID**.

    The official form numbers can be found on the [US Citizenship and Immigration Services website](https://www.uscis.gov).

7. Select or clear the **Active** toggle.
8. In the **Expire** field, set the date to **2024-10-27** (October 27, 2024).

    The expiration date is optional.

9. Select the agency that issued the document type. For example, select **Province/territory**.
10. Select **Save**.

[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
