--- 
title: Create a kanban rule for multiple activities
description: Learn how to create a kanban rule that includes multiple activities from a production flow with a step-by-step process for creating a new kanban rule. 
author: johanhoffmann
ms.author: johanho
ms.topic: how-to
ms.date: 08/29/2018
ms.custom:
ms.reviewer: kamaybac   
audience: Application User  
ms.search.form: KanbanRules, LeanProductionFlowActivityLookup, KanbanFlowSelection, InventItemIdLookupSimple, KanbanCreateScheduled, Kanban 
---

# Create a kanban rule for multiple activities

[!include [banner](../../includes/banner.md)]

This procedure shows how to create a kanban rule that includes multiple activities from a production flow. The demo data company used to create this task is USMF. This task is intended for the process engineer or the value stream manager, as they prepare production of a new or modified product in a lean environment.


## Create a new kanban rule
1. Go to Product information management > Lean manufacturing > Kanban rules.
2. Click New.
3. In the Replenishment strategy field, select 'Scheduled'.
4. In the First plan activity field, enter or select a value.
    * Select SpeakerAssemblyAndPolish.  
5. Select the Multiple activities check box.
    * The purpose is to include more than one activity in the kanban rule. You choose a path in the production flow when you select the last plan activity.  
6. In the Last plan activity field, enter or select a value.
    * Select SpeakerTestAndPackaging. After you select the value, a page automatically opens. Select the kanban flow SpeakerAssemblyAndPolish > SpeakerTestAndPackaging. Click OK.  
7. Expand the Details section.
8. In the Product field, enter or select a value.
    * Select Item L0006.  

## Create kanban and view jobs
1. Expand the Kanbans section.
2. Click Add.
3. In the Number of new kanbans field, enter '1'.
    * This will create one kanban.  
4. Set Product quantity to '3'.
    * Kanban will process 3 products.  
5. In the Due date/time field, enter a date and time.
    * You can enter Today.  
6. Click Create.
7. Click Details.
    * Notice that the kanban has two process jobs from the production flow. The first one is SpeakerAssemblyAndPolish, and the second one is SpeakerTestAndPackaging.  
    * This is the last step!  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]