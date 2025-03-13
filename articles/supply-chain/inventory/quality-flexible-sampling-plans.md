﻿---
title: Flexible sampling plans (preview)
description: 
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Flexible sampling plans (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

A flexible sampling plan defines the criteria for inspecting units of items that are randomly picked from a lot to determine if the entire lot passes or fails based on the results of the inspected samplings. Typically, the number of units chosen for inspection is proportional to the total size of the lot based on rational criterion. The quality association defined for a plan identifies the activity to be inspected. For example, the activity might be a quality order to inspect a product before it is released to a customer in a sales order, or it could be a quality order to inspect a manufactured product upon completion of production.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

Flexible sampling plans offer other features that allow you to modify your criteria over time based on prior testing results.

- **Sampling size variations** – Flexible sampling provides the ability to vary your item sampling over time based on test findings. For example, for the first five rounds of testing, you inspect 50% of the receipt. Assuming no quality failures were found in those rounds, you may decide to reduce the inspection sampling size to only 10% of the receipt for subsequent rounds. Rounds identify the number of times that a test is performed at a specific level before moving to the next level in the testing plan. For example, if a level requires 5 rounds of testing, then the assigned item sampling should be used for all 5 rounds before moving to the next level, which may use a different item sampling.

- **Test group flexibility** – Using a flexible sampling plan, you can change a plan's current test group, which identifies the individual tests performed, to a different test group based on inspection results. For example, if prior testing results show minimal problems in the quality of receipts, you might choose to change the test group to a less stringent set of tests. You can also specify different test groups for different levels in a flexible sampling plan.

- **Skip lot inspections** – Skip lot inspections, which are an alternative to lot-by-lot inspections, allow you to skip a set number of goods during testing. For example, a Quality manager may set up a flexible sampling plan for a long-time supplier to inspect a quantity of 10 units and then skip the next 10 units. This decision was made based on the vendor having demonstrated that the quality of their receipts is very good. Receipts that do not require inspection are put away and a quality order is not generated. With the flexibility to perform lot-by-lot inspections instead of unit-by-unit inspections, as well as the use of other features such as sampling size variations, skip lot inspections, and test group flexibility, this type of inspection plan helps to minimize time, costs, handling damage, and inspection errors for your company.

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The feature that is named *Advanced quality management* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Setting up flexible sampling plans

To set up your flexible sampling plans, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Flexible sampling plans**

1. For your new or selected sampling plan, make the following settings in the header:

    - **Flexible sampling plan code** - Enter a name for the sampling plan. 
    - **Name**  – Enter a short description of the sampling plan.

1. On the Action Pane you have following option.
    - **Add** Add a new sampling plan.
    - **Delete** Remove an existing plan. (You can't delete a plan if quality orders are using the plan or if activities are being tracked against it.)
    - **Copy plan** - Copy content from another plan to the selected plan.
    - **Alert role** - Select a security role to be notified when a specified number of failures for a level is reached.
    - **Last level** - Select the level number for the last activity to be performed in this flexible sampling plan process. 

1. Use the grid on the **Details** FastTab to set up the plan. Use the buttons on the Action Pane to add and remove lines in the grid. For new or selected lines make the follwoing settings:

    - **Level** – Select or view the level number assigned to this activity. The plan will be processed in the descending order of the levels.
    - **Item sampling** – Select or view the **Item sampling** that determines the sampling size of the quality order for the activity, for example a 10 percent sampling or a 50-unit quantity sampling.
    - **Test group** – Select or view the **Test group** that determines the set of tests of the quality order for the activity.
    - **Rounds** – Set or view the number of testing rounds for the specific flexible sampling plan level that must pass quality order validation to advance to the next level. Once you select a level for the **Last level** field, any **Rounds** value you entered for that level is removed from the plan. It is removed from the plan intentionally to allow the last level to continue indefinitely until several failures regress the plan to a prior level. **Note:** The last level in the testing plan does not allow rounds because all future tests would then remain at this level indefinitely until the appropriate number of fails is met to revert the plan to a prior level. Assume a quality association has been set up to test purchase order registrations for a certain vendor. The vendor's flexible sampling plan requires that 10% of every registration be tested for 5 rounds. So if I receive 100 units, then a quality order is generated to test 10 of those units. The quality order for the first registration passes. However, the second quality order fails, but the next three pass. If round 6 passes, then the first level in the plan is accomplished as the number of passed rounds required has been met.
    - **Time span (days)** – Enter or view the number of days by which the specified number of rounds must be completed. This field is optional. **Note:** This field works in conjunction with the **Rounds** field. If a time span is defined, then the specified number of rounds must pass inspection within this time frame to advance testing to the next level. For example, if you set the time span to 60 days and the rounds to 10, then ten quality orders for this quality association must pass within 60 days to advance to the next level in the plan.
    - **Skip** – Select this check box to enable skip lot sampling, which allows for only a fraction of the submitted lots to be inspected. When you select this check box, you must enter the skip range in the **Frequency** fields.
    - **Test frequency** – If the **Skip** field is selected, enter the first number in the Skip range.
    - **Out of frequency** – If the **Skip** field is selected, enter the last number in the Skip range. Assume the quality association is set for Production order registrations. The flexible sampling plan associated with this reference type uses the Skip feature where the **Test frequency** field is set to **1** and **out of frequency** is set to **5**. Based on these settings, a quality order is generated to test 1 out of every 5 registrations. The determination as to which registrations of the 5 are tested and which ones are skipped is randomly made.
    - **Number of fails** – Enter or view the number of failed tests allowed before the flexible sampling plan reverts to a previous testing level, which may be more or less restrictive than the current test based on prior testing results. If the **Consecutive** check box is also selected, then the number of fails must be consecutive fails before the plan reverts to a prior level. A vendor might initially define a plan to test 10 out of 40 receipts to minimize costs associated with testing. However, because recent testing results support a notable increase in failures, the current level ends and a different level to test 20 out of 40 receipts replaces it. To the contrary, if the vendor's testing quality is consistent with no failures, then the level may be replaced by a level that requires a lower number of fails.
    - **Consecutive** – Select this check box if the number of fails specified in the **Number of fails** field must be consecutive failures. If selected and the number of consecutive fails is reached, then the appropriate action based on the fail action level and code is initiated. If the number of fails allowed is set to **2** and this check box is selected, then two consecutive fails generate a predefined fail action, such as issuing an alert notification to the Quality manager.
    - **Fail action level** – Enter or view the level of action that is initiated when the quantity in the **Number of fails** field is reached. This action indicates that more testing is required. If the **Consecutive** check box is also selected, then the number of fails must be consecutive fails to initiate the action. For example, if two consecutive quality orders fail at Level 3, then the action defined may require that testing start over at Level 1. You can assign any prior level that is currently defined in the flexible sampling plan that is at least equal to or less than the current level.
    - **Fail action code** – Select the action code that defines the action to take when the failure criteria is met or exceeded for the flexible sampling plan. All of the actions return the test sampling process to the fail action level.

## Set up the quality association for the flexible sampling plan

Quality orders using the flexible sampling plans are set up to be automatically generated by setting up a quality assoication that refers to a specific sampling plan. To set up a quality association that uses a flexible sampling plan, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Flexible sampling plans** 



Learn more in [Quality associations](quality-associations.md).

You set up new flexible sampling plans on the **Flexible sampling plans** page. Each plan is made up of different testing levels that identify the testing process, such as which test group and/or item sampling, and the order in which the levels are performed. For each plan you create, if the **Alert** or **Expire AVL/Alert** option is set up for a plan level, then you can assign an alert role to be notified if the specified number of failures for that level is reached.

After you set up the criteria for each of the plan's levels, you then establish the quality association for the plan to identify the testing activities (for example, purchases, specific vendor account, and specific item) and to generate quality orders based on test results. You establish the quality association on the **Specifications** FastTab on the **Quality associations** page.

**Example:** A manufacturing company currently uses item sampling functionality for testing goods received in shipments. However, to reduce costs associated with testing, they need greater flexibility in their testing approach. The company's testing statistics over the past year show minimal exceptions were found during their inspections of a particular item. To reduce costs, they decide to implement flexible sampling. With flexible sampling they can not only vary or reduce the sampling size based on prior testing results, but they can skip certain lots from testing as well.

To set up a new flexible sampling plan, go to **Inventory management** \> **Setup** \> **Quality control** \> **Flexible sampling plans**. Then use the buttons and settings described in the following subsections.

## Track activities for flexible sampling plans

To inquire about and track activities associated to a flexible sampling plan, you use the **Flexible sampling plan activities** page. For example, the activities for a plan might specify which test groups and samplings were used for creating quality orders, as well as which quality orders were skipped based on skipping criteria defined in the plan.

Each activity captures pertinent information about the account, item, and testing level at the most granular level. For example, if a flexible sampling plan code is associated with a quality association for All vendors and a specific Item quality group, then the information displayed includes the reference type (Purchase), vendor's account number, specific item number, and the current testing level.

To set up a new flexible sampling plan, go to **Inventory management** \> **Periodic** \> **Quality management** \> **Flexible sampling plan activities**. Then use the buttons and settings described in the following subsections.

### Buttons for tracking activities on the Flexible sampling plan activities page

- **Flexible sampling plan activity summary** – View a summary of activity for the selected flexible sampling plan code.
- **Flexible sampling plan activity details** – View the specific details of the flexible sampling plan you select.
- **Flexible sampling plans** – View the specific activity details for the flexible sampling plan you select. You can also create a new flexible sampling plan from this page.

### Fields for tracking activities on the Flexible sampling plan activities page

- **Flexible sampling plan code** – The identifier for the flexible sampling plan.
- **Reference type** – The type of reference for the activity (*Sales*, *Purchase*, *Production*, *Co-product production*, *Route operation*, or *Quarantine*).
- **Account** – The account identifier for the reference type. If the reference type is Sales, then this field displays the customer's account number.
- **Item number** – The identifier for the item associated with the reference type. If the reference type is Sales, then this field displays the identifier for the item sold.
- **Resource** – The resource, such as a person or a machine, when the quality association is the reference type **route operation**.
- **Current level** – The level at which the selected flexible sampling plan is currently being tested.

## View activity details for Flexible sampling plans

To view specific details of all activities that have occurred against an active Flexible sampling plan, go to **Inventory management** \> **Periodic** \> **Quality management** \> **Flexible sampling plan activities**. Then use the buttons and settings described in the following subsections.

### Buttons for viewing activity details the Flexible sampling plan activities page

- **Flexible sampling plan activity summary** – View a summary of current activities for the selected flexible sampling plan.
- **Overall activity statistics** – View the following statistics in graphical format:
    - Current round activity (Rounds) – Illustrates the number of rounds that passed and failed.
    - Current round activity (Quality orders) – Illustrates the number of quality orders that were created and the number that were skipped.
    - Overall statistics – Illustrates the current round activity for both the rounds and the quality orders.
- **Change activity level** – Select a new activity level and reason code for this flexible sampling plan and enter a free-form reference. For example, assume a flexible sampling plan is defined for a specific item and vendor, and the vendor later initiates a new manufacturing process. You can assign a new flexible sampling plan level manually, as there may be issues with this new process.
- **Delete current level** – Delete the activities for the current level. For example, if you want to repeat the current level of testing, you can use this action to delete activities for the current level and then repeat the testing process for this level.
- **Delete all activities** – Delete all activities for this flexible sampling plan. For example, if you want to repeat all testing levels for this plan, you might want to delete all activities and then start again.

### Fields for viewing activity details the Flexible sampling plan activities page

- **Flexible sampling plan code** – The identifier of the flexible sampling plan. **Note:** You can double-click the flexible sampling plan code to open the related flexible sampling plan to view the details for this plan. To return to activity details, close the flexible sampling plan after you view it.
- **Reference type** – The type of reference for the activities, such as Purchase, Sales, Production, Co-product production, Quarantine, or Route operation.
- **Item number** – The identifier of the item associated with the reference type. For example, if the reference type is **Sales**, then this field displays the identifier of the item sold.
- **Account selection** – The account identifier of the reference type. For example, if the reference type is **Sales**, then this field displays the customer's account number.
- **First activity** – The date on which the first activity was recorded against this reference of the flexible sampling plan.
- **Created date and time** – The date and time that this activity was created for this specific reference to the flexible sampling plan.
- **Level** – The current level of testing for this activity in the overall testing plan.
- **Test group** – The identifier for the test group that was responsible for creating the quality order for this level in the flexible sampling plan.
- **Round number** – The number of the last round of passed tests at the current level.
- **Item sampling** – The identifier for the item sampling code that was used when creating the quality order for this level in the flexible sampling plan.
- **Skip** – If selected, then this flexible sampling plan used skip lot sampling in the testing process.
- **Frequency** – If skip lot sampling is allowed for this flexible sampling plan, then this is the last number in the range that was skipped during testing.
- **Quality order** – The quality order number if a quality order was created for this activity. If a quality order was not created for the activity, for example, if skipping occurred, then this field is blank.
- **Status** – The status of the quality order if a quality order was generated for the activity. The status values are **Pass, Fail** or **Skipped**.
- **Validated by** – The identifier for the worker responsible for testing at the current level and who validated the quality order as **Pass** or **Fail**, if one was generated.
- **Validated date and time** – The date and time when the quality order was validated, if applicable.
- **Fail action level** – If the activity failed, then this is the level to which testing returns to begin retesting the activity as specified in the related flexible sampling plan.
- **Fail action code** – If retesting is required as indicated in the **Fail action level** field, then the action code in this field defines the action needed. If retesting is not required, then this field is blank. The fail actions codes are:
    - **Alert** – Return the test sampling to the previous action level and issue an alert to the alert role specified.
    - **Expire AVL/Alert** – Return the test sampling to the previous action level, issue an alert to the alert role specified, and change the vendor or item in the Approved Vendor List (AVL) to "expired" if the quality association is purchasing and an AVL is in effect for the vendor.
    - **None** – Return the test sampling to the previous action level.
- **Pass action level** – If the activity level passes, then this is the level to which testing continues as specified in the related flexible sampling plan. This level is often the next level but flexibility is supported so that any level can be chosen.
- **Reason code** – The identifier for the reason code used if the current level of activity in this plan was manually changed to a prior level.
- **Reference** – A brief description of a change to the activity, such as a change to the status of a Quality Order.
- **Modified by** – The identifier for the user who changed the activity.
- **Modified date and time** – The date and time that the user changed the activity.

## Viewing activity summaries for Flexible sampling plans

To view a summary of activities associated to a flexible sampling plan in summary form, go to **Inventory management** \> **Periodic** \> **Quality management** \> **Flexible sampling plan activities**. Then use the buttons and settings described in the following subsections.

### Buttons for viewing activity summaries the Flexible sampling plan activities page

- **Flexible sampling plan activity details** – View activity details for the selected flexible sampling plan.
- **Activity graph** – View a graphic that illustrates the number of rounds that passed and failed and the number of quality orders that were created and skipped.
- **Change activity level** – Select a new activity level and reason code for this plan and enter a free-form reference. For example, assume a flexible sampling plan is defined for a specific item and vendor, and the vendor later initiates a new manufacturing process. You can create a new flexible sampling plan level manually, as there may be issues with this new process.
- **Quality associations** – View the rules that are defined for the quality association that is used by this flexible sampling plan.
- **Non conformances** – View nonconformances that are related to the selected flexible sampling plan.
- **Quality orders** – View the quality orders that are related to the selected flexible sampling plan.

### Fields for viewing activity summaries the Flexible sampling plan activities page

- **Flexible sampling plan code** – The identifier for the flexible sampling plan.
- **Reference type** – The type of reference for the activity.
    - Sales
    - Purchase
    - Production
    - Co-product production
    - Route operation
    - Quarantine
- **Type** – View the type of CAPA process.
- **Item number** – The identifier of the item associated with the reference type. If the reference type is **Sales**, then this field displays the identifier of the item sold.
- **Account selection** – The account identifier of the reference type. For example, if the reference type is **Sales**, then this field displays the customer's account number.
- **Resource** – The resource, such as a person or a machine, when the quality association is the reference type **route operation**.
- **Current level activity** – View a summary of activity for the current level for this flexible sampling plan.
    - **Level** – The current level number in the overall testing plan.
    - **Item sampling** – The item sampling that is being used at this current level of testing.
    - **Test group** – The test group assigned to create quality orders for this level.
    - **Round** – The number of the last round of passed tests at the current level.
    - **First date** – The date on which testing began at this level.
- **Current level details (Flexible sampling plan)** – View the details of activity for the current level of activity for this flexible sampling plan. This section provides easy access to how the current level was defined based on the criteria for this specific flexible sampling plan.
    - **Rounds** – The number of passed testing rounds required for this current level in the related flexible sampling plan.
    - **Fails** – The number of failures allowed before the testing process for this flexible sampling level stops and is replaced by a different and potentially more stringent item sampling.
    - **Time span (days)** – The number of days over which the specified number of rounds must be completed before you can advance to the next testing level. This field works with the **Rounds** field. Both conditions must be met to advance to the next testing level.
    - **Consecutive** – Select this check box if the number specified in the **Fails** field must to be consecutive fails.
    - **Skip** – Select this check box to use skip lot sampling in your testing process. If you choose not to use skip lot sampling, leave this check box blank.
    - **Frequency** – If you select the **Skip** check box, enter the beginning and ending range of lots to be skipped during testing.
    - **Fail action level** – The level at which the current testing process will stop if the number of failed tests prior to this level reach the number specified in the **Fails** field. When this occurs, the Fail action code is activated and more stringent.
    - **Fail action code** – The action code that defines the action taken when the failure criteria are met or exceeded for a quality order. All the actions return the testing to the Fail action level specified.
    - **Pass action level** – If the activity level passes, then this is the level to which testing continues as specified in the related flexible sampling plan. This level is often the next level, but flexibility is supported so that any level can be chosen.
- **Current round activity** – View a summary of results for the current round of activity for this flexible sampling plan.
    - **Number of potential tests** – The number of possible tests to be performed at this level.
    - **Number of Quality orders created** – The number of quality orders created as of this round.
    - **Number of Quality orders skipped** – The number of quality orders that were skipped as of this round.
    - **Number of tests passed** – The number of tests that passed this level of testing.
    - **Number of tests failed** – The number of tests that failed this level of testing.
    - **Next level** – The number of the next level in the testing process.
    - **Fail action triggered** – Indicates whether the failed action was initiated.
    - **Fail action reason code** – The identifier for the fail action code if the fail action was initiated.
