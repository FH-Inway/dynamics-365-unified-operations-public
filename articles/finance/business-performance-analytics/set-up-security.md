---
title: Set up security for Business performance analytics
description: Learn how to set up security for Business performance analytics, including outlines for the admin role, the process of setting up roles, and dimension security.
author: jkhaira7
ms.author: jkhaira
ms.topic: how-to
ms.date: 12/12/2023
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
---

# Set up security for Business performance analytics

[!include [banner](../includes/banner.md)]

The setup of security in the Business performance analytics app is a critical step in ensuring the security of your organization's data. This article provides an overview of the setup process for role-based, dimension, and report security, and explains how to add users to the app.

## Admin role

The first user who signs in to the app is assigned the **BPA admin** role. This role allows the user to access the **Administrator** section of Business performance analytics, where they can set up security.

The admin is automatically assigned the **Microsoft report viewer** role and the **All access** dimension group.

- The **Microsoft report viewer** role allows a user to view all reports that Microsoft provides in Business performance analytics.
- The **All access** dimension group allows a user to view data for all dimensions, without any filters.

## Set up roles

A role defines which reports a user can access. Use roles to organize how Business performance analytics users can access reports.

## Dimension security

Dimension security lets admins control which data is visible on a report. The process of setting up dimension security has two steps:

1. **Set up dimensions.** Select the dimensions that you want to secure. During public preview, you can select up to five dimensions from the ledger and reporting dimensions. Any change to the selection of dimensions might affect the dimension groups that are created and the users who are assigned them.
2. **Set up dimension groups.** You can create dimension groups only after step 1 is completed. A dimension group filters report data so that only the filtered values in a given dimension attribute are visible to users who are assigned that dimension group. You can assign one or more dimension groups to a user to control what data is visible on a report. At least one dimension group must be assigned to each user.

>[!Important]
>You can only apply dimension security across facts that reference that dimension group. However, only one dataset is available in Business performance analytics. This means a user can create a link between tables that can't be secured through dimension groups if those tables don't have any dimensions referenced in the dimension groups. 


> [!NOTE]
> If you assign many dimension groups to a single user, the user's reports might take longer to be loaded.

### Set up dimensions

To set up dimensions to secure access to data, follow these steps.

1. In Business performance analytics, on the **Administration** or **Dimensions** page, select **Set up dimensions**.
2. Select up to five dimensions to secure access to data. If you don't secure a dimension, all users can access the values in that dimension.
3. Select **Save**.

### Set up dimension groups

To set up dimension groups, follow these steps.

1. In Business performance analytics, on the **Administration** page, select **Set up dimension groups**. Alternatively, on the **Dimension groups** page, select **New**.
2. Enter a name for the dimension group, and then select **Next**.

    When the **Set up dimensions to secure** step is completed, the selected dimensions are shown.

3. Select **Select specific values** to select the exact dimension values to use in a dimension group. To add a range of dimension values, use a **Between** operator. You can add a maximum of five ranges.
4. Select **Preview results** to preview the values that will be filtered based on your selections. In this way, you can determine what values for each dimension will be visible to the users who are assigned this dimension group.

    > [!NOTE]
    > If you don't select a dimension value filter for a given dimension, all values will be shown on the report. However, the dimension filters for other dimensions will still be applied.

5. When you've made your selections for all dimensions that must be secured, select **Next**. You can review the selections on the **Review** tab of the **New dimension group** dialog box.
6. Select **Save** to create the dimension group.

> [!NOTE]
> The dimension group creation process doesn't confirm that you've selected a valid combination of dimension values. If you select an invalid combination of dimension values, the dimension group will filter out all records on reports. To test that the combination of dimension values is valid, open a report as a user who's assigned the dimension group.

Within a given dimension group, a record must satisfy all the filter conditions for the data to be visible to the user on a report. If there are any conflicting criteria or non-valid combinations, no data will be shown.

### Dimension group examples

#### Dimension group example 1

A user is assigned one dimension group, **Test dimension group**. This dimension group has the following filters:

- **Legal entity:** USMF and CNMF
- **Cost center:** Between 000001 and 000003
- **Department:** 000004

If the cost center and department numbers are linked so that they must match, no data will be available to the user who's assigned this dimension group.

#### Dimension group example 2

A user is assigned one dimension group, **Test dimension group**. This dimension group has the following filters:

- **Legal entity:** USMF and CNMF
- **Cost center:** Between 10000 and 20000
- **Department:** 000004

If all cost centers have values that are below 10000, there will be no valid combinations. Therefore, no data will be available to the user who's assigned this dimension group.

#### Dimension group example 3

If a user is assigned two or more dimension groups, a record must satisfy the filter conditions of at least one of them for the data to be visible to the user on a report. For this example, a user is assigned two dimension groups: **Test dimension group** and **Group x**. These dimension groups have the following filters:

**Test dimension group:**

- **Legal entity:** USMF and CNMF
- **Cost center:** Between 000001 and 000003
- **Department:** Marketing 01

**Group x:**

- **Legal entity:** USMF
- **Cost center:** All
- **Department:** All

The user will be able to view records for legal entities USMF and CNMF. For legal entity USMF, the user will see all cost centers and all department combinations. For legal entity CNMF, the user will see only records where the cost center is between 000001 and 000003 and the department is Marketing 01.

#### Dimension group example 4

If a user is assigned an **All access** dimension group or a dimension group that has no filters, the user will have full visibility into the data on a report. For example, a user is assigned a dimension group that has the following filters:

- **Legal entity:**
- **Cost center:** All
- **Department:** All

Because no filter is defined for **Legal entity**, and the **All** filter is used for **Cost center** and **Department**, the user will see records that have all combinations of legal entities, cost centers, and departments.

## Set up users

After you've set up the roles and dimension groups, you can set up users so that they have access to Business performance analytics.

To set up users, follow these steps.

1. In Business performance analytics, on the **Administration** or **Users** page, select **Set up user**.
2. Search for the user name or email address to set up in Business performance analytics. The search field searches Microsoft Dataverse for users. You can set up only one user at a time.

    > [!NOTE]
    > If a new user is added to Microsoft Entra ID, it might take some time for the user to become available.

3. Select **Next**.
4. Assign at least one role and one dimension group to the user. To make this user a Business performance analytics admin, select **App administrator**.
5. Select **Save**.
