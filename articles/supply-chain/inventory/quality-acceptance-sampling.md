---
title:  Acceptance sampling (preview)
description: Learn how to set up acceptance sampling to quality control products batches by inspecting representative samples.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: QMSAQLDefectType, QMSAQLInspectionLevel, QMSAQLChart, InventTestTable, InventTestGroup, InventItemSampling, InventTestAssociationTable, QMSAQLIndex
ms.topic: how-to
ms.date: 07/28/2025
ms.custom: 
  - bap-template
---

# Acceptance sampling (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.46 GA -->

*Acceptance sampling* is a quality control method used to evaluate a batch of products by inspecting a representative sample. Instead of checking every item, a subset of items is examined to determine whether the entire lot meets predefined quality standards. This approach is widely used in manufacturing and supply chain operations to balance inspection effort with quality assurance.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Acceptance sampling overview

### Defect types and categories

In many practical applications, sampled items are inspected for different *types* of defects, each of which is typically placed in one of the following *categories*:

- **Critical defects** – Defects that could cause harm or render a product unsafe or unusable. Even a single critical defect might lead to rejection of the entire lot.
- **Major defects** – Defects that significantly reduce the usability or performance of a product but don't pose safety risks. A limited number of major defects might be acceptable depending on the sampling plan.
- **Minor defects** – Defects that don't affect a product's function or safety but might impact appearance or user satisfaction. A higher tolerance is usually allowed for minor defects.

Acceptance criteria are defined in advance, often using standards like ANSI/ASQ Z1.4 or ISO 2859-1, which specify how many defects of each category are permissible in a sample before the lot is rejected. This structured approach helps ensure consistent product quality while optimizing inspection resources.

### Single and double sampling plans

In acceptance sampling, single and double sampling plans represent two different strategies for determining whether a lot meets quality standards. A single sampling plan involves selecting and inspecting one sample from the lot. Based on the number of defects found, the lot is either accepted or rejected. This method is straightforward and commonly used when simplicity and speed are important. A double sampling plan introduces a second step. If the first sample yields an inconclusive result, a second sample is taken. The final decision is then based on the combined results of both samples. This strategy can reduce inspection effort over time while maintaining decision accuracy. In this solution, only the single sampling strategy is supported, meaning each lot is evaluated using one sample and a fixed acceptance threshold.

### Acceptance sampling charts

Acceptance sampling uses two types of charts to validate whether a lot passes or fails an inspection: a *sampling code letter chart* and an *acceptable quality limit chart*.

The *sampling code letter chart* defines code letters for each combination of lot size and inspection level. The selected code letter is then used as input to the acceptable quality limit chart. An *inspection level* is a code or category defined by a business user. It indicates the extent of inspection based on the importance of the product, the production history, and customer requirements. There are two categories of inspection levels:
    - *General inspection level* – Used for routine, thorough inspections
    - *Special inspection level* – Apply to less critical checks with smaller sample sizes.

The following image shows an example of a code letter chart. In this example, if you have a lot size between 151 and 280 and use a general inspection level II, then code letter G should be used as input in the acceptable quality limit chart.

:::image type="content" source="media/code-letter-chart.jpg" alt-text="Example of a code letter chart" lightbox="media/code-letter-chart.jpg":::

The *acceptable quality limit chart* defines the acceptable quality level for each combination of sampling code letter and acceptable quality level (AQL) index. The AQL indexes are determined by business users and are based on how critical the product is, industry standards, customer requirements, and the acceptable level of risk. Lower indexes are used for high-risk or critical items, while higher AQLs are acceptable for less critical products where some defects are tolerable. Businesses can, for example, use index 0.1% for testing for critical defects, 0.65% for major defects, and 2.5% for minor defects. The selected code letter and AQL index resolve to find the sample size and acceptable quality level for the test.

The following image shows an example of an acceptable quality limit chart. In this example, if you use code letter G with an AQL index of 2.5%, then up to two defects will be accepted for the lot to pass, but three or more defects will cause the lot to fail inspection. If the code letter G is used for AQL index 0.65%, then the arrow in the chart indicates that an AQL level for a different code letter should be used. In this case, the code letter with the nearest AQL values is F, which has a different sample size than code letter G, and zero defects will be accepted for the lot to pass.

:::image type="content" source="media/sampling-plan-chart.jpg" alt-text="Example of an acceptable quality limit chart" lightbox="media/sampling-plan-chart.jpg":::

In Supply Chain Management, you can load all the data for generating the sampling code letter chart and the acceptable quality limit chart from a template. The template generates inspection levels, AQL indexes, and lot size ranges. Once these values are loaded from the template, you can customize the charts as needed.

<!-- KFM: 
You can learn more about how to use the charts in the following video: 

> [!VIDEO 1e6ef0b8-0c35-4560-9f2a-926da8a6fd9b]

-->

### <a name="orders-methods-associations"></a>Quality orders, item sampling methods, and quality associations

Supply Chain Management uses *quality orders* to schedule and manage testing based on acceptance sampling. To enable this functionality, you must define an appropriate item sampling method that supports acceptance sampling.

Supply Chain Management uses *item sampling methods* to define how much of a product should be inspected during a quality order. It specifies the sample quantity or percentage to be tested from a lot, and is essential for enabling acceptance sampling in quality control processes. You can learn more about item sampling in [Quality management item sampling](quality-item-sampling.md).

Item sampling methods take effect when they're assigned to *quality associations*. Supply Chain Management uses quality associations to establish and apply rules that automatically trigger a quality order based on specific events, such as product receipt, production output, or inventory movement. Each quality association links a product, process, or condition to a quality inspection requirement, ensuring consistent and automated quality control. You can learn more about quality associations in [Quality associations](quality-associations.md).

When a quality order is triggered based on an event defined in a quality association, the system automatically creates a quality order that can be used for acceptance sampling. The quality association links the triggering event (such as a product receipt or production output) to a specific test process. If the associated item sampling record is configured for acceptance sampling, the generated quality order uses the defined sampling criteria to determine how much of the lot should be inspected.

On the quality order for acceptance sampling, the various categories of tests (critical, major, and minor), their sample sizes, and acceptable quality levels are clearly indicated. If a test falls outside a quality level, then the entire quality order fails during validation.

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.45 or later.
- The feature that is named *(Preview) Acceptance sampling* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set up acceptance sampling charts

To set up your acceptance sampling charts, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Acceptance sampling** \> **Acceptance sampling chart**.
1. Use the buttons on the Action Pane to add a new chart or edit a selected one.
1. On the header of the new or selected chart, set the following fields:
    - **Acceptance sampling chart name** – Enter a name for the sampling chart.
    - **Description** – Enter a short description of the sampling chart.

1. To get started quickly, you can choose start by copying an existing cart or loading a predefined template. If you'd like to do this, select one of the following options in the Action Pane. Be careful, because all of the settings for the current chart (other than name and description) will be replaced with the template or copied chart.
    - **Load AQL chart template** – Load all the data needed for the acceptance sampling chart from a predefined template. The template is loaded from a predefined JSON file. The content of the file is aligned with the ANSI/ASQ Z1.4 or ISO 2859-1 standards.
    - **Copy** – Copy data from another chart. The system asks you to choose an existing chart to copy from.

1. On the **Inspection levels to include** FastTab, use the buttons in the toolbar to add and remove inspection levels for the current chart. The inspection levels are used as a criteria to find the applicable code letter in the code letter chart. You can find more information about inspection levels in [Acceptance sampling charts](#acceptance-sampling-charts).

1. On the **AQL indexes to include** FastTab, use the buttons in the toolbar to add and remove AQL indexes for the current chart. The AQL index defines the maximum acceptable defect rate in a sample that determines whether a production lot passes or fails inspection. You can find more information about the use of AQL indexes in [Acceptance sampling charts](#acceptance-sampling-charts).

1. On the **Lot/batch size ranges** FastTab, use the buttons in the toolbar to add and remove lot/batch size ranges for the current chart. Use the **Unlimited** button in the toolbar to set a range to have no upper limit (this sets the **To** field to *Unlimited* for the selected row). The lot/batch size ranges are groupings of total units in a production batch used as input in the code letter chart to find the applicable code letter. You can find more information about the use of lot/batch size ranges in  [Acceptance sampling charts](#acceptance-sampling-charts).

## Set up inspection levels and acceptance sampling indexes

If you don't use the option to load your charts from a template, you must create the inspection levels and sampling indexes manually.

### Setup inspection levels

An inspection level is a code or category set by the business user that indicates the extent of inspection based on the importance of the product, the production history, and customer requirements. It's used as input to the code letter chart, and guides how many samples you take from a lot. Follow these steps to create them manually:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Acceptance sampling** \> **Inspection levels**.
1. Select **New** to create a new inspection level and set the following fields:
    - **Inspection level** – The identification of the inspection level.
    - **Inspection level type** – Chose between the two types *General* or *Special*, which are used as a criteria to find the code letter in the code letter chart. You can learn more about how to use these level designations in [Acceptance sampling charts](#acceptance-sampling-charts).
    - **Description** – User defined description of the inspection level.

### Set up acceptance sampling indexes

 The AQL indexes are determined by business users and are based on how critical the product is, industry standards, customer requirements, and the acceptable level of risk. If you don't want to use the option to generate the AQL indexes by loading the AQL chart template, then you can use the following steps to create them manually:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Acceptance sampling** \> **Acceptance sampling indexes**.
1. Select **New** to create a new inspection level and set the following fields:
    - **Acceptable quality limit index** – The identification of the acceptance sampling index. The AQL index defines the maximum acceptable defect rate in a sample that determines whether a production lot passes or fails inspection.
    - **Description** – User defined description of the acceptance sampling index.

1. When you're done setting up the chart, select **Validate** in the Action Pane to validate the integrity of the data in the plan. The system checks your settings and if the chart is valid, it sets the **Validated** field to *Yes*. Only validated charts can be used for acceptance sampling.

## View the sampling size code letter chart

When an acceptance sampling chart is created and validated, you can view. To view the sampling size code letter chart, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Acceptance sampling** \> **Acceptance sampling chart**.
1. Select the acceptance sampling chart where you want to view the sampling size code letter chart.
1. On the Action Pane, select **Sampling size code letter chart**. On the Action Pane of the sampling size code letter chart, you can open the corresponding acceptable quality limit chart by selecting **Acceptable quality limit chart**.

## View or edit the acceptable quality limit chart

When an acceptance sampling chart is created and validated, you can view or make edits to the acceptable quality limit chart. To edit the acceptable quality limit chart, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Acceptance sampling** \> **Acceptance sampling chart**.
1. Select the acceptance sampling chart where you want to edit the acceptable quality limit chart.
1. On the Action Pane select *Acceptable quality limit chart* to open the chart.
1. On the Action Pane of the chart, use the following options to make edits:
    - **Up** – Use this option to add an arrow pointing upwards in the selected cell in the chart. The arrow indicates in which direction the the AQL levels and sample size must be found. You can find more information about the use of the arrows in the acceptable quality limit chart in [Acceptance sampling charts](#acceptance-sampling-charts).
    - **Down** – Use this option, to add an arrow pointing downwards in the selected cell in the chart. The arrow indicates in which direction the the AQL levels and sample size must be found. You can find more information about the use of the arrows in the acceptable quality limit chart in [Acceptance sampling charts](#acceptance-sampling-charts).  
    - **Accept** Use this option to set the acceptance level in the selected cell. The acceptance level the maximum number of defects allowed for a given sample size range and AQL index. You can find more information about the use of the acceptable quality limit chart in [Acceptance sampling charts](#acceptance-sampling-charts).

## Set up defect types

Defect types identify the types of defects that users test for, such as *paint chipped*, *screen cracked*, *packaging damaged*, and so on. Each defect type is categorized with a defect category of *Critical*, *Major*, or *Minor*.

To set up defect types, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Acceptance sampling** \> **Defect types**.
1. Select **New** to create a new defect type and set the following fields:
    - **Defect type** – Identification of the type of defect to be tested for.
    - **Description** – Elaborated description of the defect type.
    - **Defect category** –  Categorize the defect type with one of the three following fixed categories:
        - *Critical* – Could cause harm or render a product unsafe or unusable. Even a single critical defect might lead to rejection of the entire lot.
        - *Major* – Significantly reduces the usability or performance of a product but don't pose safety risks. A limited number of major defects might be acceptable depending on the sampling plan.
        - *Minor* – Doesn't affect function or safety but might impact appearance or user satisfaction. A higher tolerance is usually allowed for minor defects

## Set up a test for acceptance sampling

You must define each of the tests that you want to use on quality orders, and each test must be associated with one of the defect types that  you set up in the previous section. Learn more about tests for quality orders in [Quality management tests](quality-tests.md).

## Set up a test group for acceptance sampling

Each of the tests that you use for acceptance sampling must be associated a *test group*. A test group is a collection of tests needed on a quality order. Each quality association has a test group assigned, which it uses for automatic generation of quality orders. You can learn more about the use of test groups in [Quality management test groups](quality-test-groups.md)

## Set up item sampling for acceptance testing

Use *item sampling* records to define how much of a product should be inspected during a quality order. Each one specifies the sample quantity or percentage to be tested from a lot, and is essential for enabling acceptance sampling in quality control processes. Learn more about how item sampling is used in acceptance sampling in [Quality orders, item sampling methods, and quality associations](#orders-methods-associations). For general information about item sampling, see [Quality management item sampling](quality-item-sampling.md).

To set up item samplings for acceptance sampling, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Item sampling**.
1. Select **New** to create a new item sampling and set the following fields:
    - **Item sampling** – Enter a name for the item sampling record.
    - **Description** – Enter a short description of the item sampling record.
    - **Sampling Scope** – Select the scope to use when evaluating if quality work should be created. When set to *Shipment* or *Load*, those entities are used if available. If not, the *Order* is used.
    - **Use acceptance sampling charts** – Choose one of the following options:
        - *Single* – Use acceptance sampling. The value indicates that you'll use a single sampling plan. Learn more in [Single and double sampling plans](#single-and-double-sampling-plans).
        - *None* – Don't use acceptance sampling for quality inspection.

1. On the **Acceptance sampling** FastTab, set the following required fields:
    - **Acceptance sampling chart name** – Select the sampling chart you want to use for this item sampling.
    - **Description** – Field that displays the name of the select acceptance sampling chart.
    - **Inspection level** – Select which inspection level you want to use for this item sampling. An inspection level is a code or category that is determined by the business user. It indicates the extent of inspection based on the importance of the product, the production history, and customer requirements. Learn more about the use of inspection levels: [Acceptance sampling charts](#acceptance-sampling-charts).
    - **Description** – Displays the description of the selected AQL index.
    - **Minor AQL%** – Enter the AQL index for minor defects for the item sampling. The AQL indexes are determined by business users and are based on how critical the product is, industry standards, customer requirements, and the acceptable level of risk. Learn more how to use AQL indexes here: [Acceptance sampling charts](#acceptance-sampling-charts).
    - **Description** – Displays the description of the selected AQL index.
    - **Major AQL%** – Enter the AQL index for major defects for the item sampling. The AQL indexes are determined by business users and are based on how critical the product is, industry standards, customer requirements, and the acceptable level of risk. Learn more how to use AQL indexes here: [Acceptance sampling charts](#acceptance-sampling-charts).
    - **Description** – Displays the description of the selected AQL index.
    - **Critical AQL%** – Enter the AQL index for critical defects for the item sampling. The AQL indexes are determined by business users and are based on how critical the product is, industry standards, customer requirements, and the acceptable level of risk. Learn more how to use AQL indexes here: [Acceptance sampling charts](#acceptance-sampling-charts).
    - **Description** – Displays the description of the selected AQL index.

## Set up a quality association for acceptance sampling

Supply Chain Management uses quality associations to establish an apply rules that automatically trigger a quality order based on specific events, such as product receipt, production output, or inventory movement. Each quality association links a product, process, or condition to a quality inspection requirement, ensuring consistent and automated quality control. You can learn more about quality associations in [Quality associations](quality-associations.md).

When a quality order is triggered based on an event defined in a quality association, the system automatically creates a quality order that can be used for acceptance sampling. The quality association links the triggering event (such as a product receipt or production output) to a specific test process. If the associated item sampling is configured for acceptance sampling, the generated quality order uses the defined sampling criteria to determine how much of the lot should be inspected.

To set up a quality association for acceptance sampling, follow the instructions provided in [Quality associations](quality-associations.md). When you're setting up your quality associations on the **Quality associations** page, pay special attention to following settings, which are specific to acceptance sampling:

- Use the **Item sampling** field on the **Specifications** FastTab to select an item sampling record. This setting is required to enable acceptance sampling for the quality association.
- Use the **Test group** field on the **Specifications** FastTab to select a test group that contains the tests you want to use for acceptance sampling. The test group must contain tests that are associated with defect types that you set up in [Set up defect types](#set-up-defect-types).

## Using acceptance sampling on quality orders

When a quality order is created for acceptance sampling, the **Acceptance sampling** tab is available on the header of the quality order. This tab includes a grid that contains line items for each test that needs to be conducted. The grid provides the following information:

- **Defect category** – Indicates one of the three fixed categories of the test *Critical*, *Major*, or *Minor*.
- **Defect type** – Indicates the type of the test defined in the configuration. Learn more about defect types here: [Set up defect types](#set-up-defect-types).
- **Acceptable quality level index** – Indicates the AQL index for the specific test as specified on the configuration of the item sampling for the quality order.
- **Sample size** – The sample size of the test.
- **Target Ac** – Maximum number of defects accepted for the test to fail.
- **Target Re** – Minimum number of defects for the test to fail.
- **Test result** – Graphical indication if the test has passed or failed.

To enter test results, go to the **Quality orders** page and select the quality order you want to work with. Then either enter the results directly into the test lines in the bottom grid or select **Quick result entry** from the Action Pane to use the quick-entry form.
