---
# required metadata

title: Create a buy and sell leave request workflow
description: Create a buy and sell leave request workflow to manage to buy and sell leave requests consistently in Dynamics 365 Human Resources.
author: twheeloc
ms.date: 07/09/2024
ms.topic: how-to
# optional metadata

ms.search.form: LeavePlanFormPart, LeaveAbsenceWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ajitchandran
ms.search.validFrom: 2020-08-20
ms.dyn365.ops.version: Human Resources

---

# Create a buy and sell leave request workflow

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

You can create a workflow in Dynamics 365 Human Resources to consistently manage your buy and sell leave requests. A **Buy and sell leave** workflow lets you:

- Define tasks
- Determine who must complete the tasks
- Specify who can approve or reject requests

## Create a buy and sell leave request workflow

1. On the **Leave and absence** page, select the **Links** tab.

2. Under **Setup**, select **Human resource workflows**.

3. Select **New**, and then select **Buy and sell leave request**. 

4. When the **Open this file?** message box appears, select **Open** and sign in with your company credentials.

5. Use the workflow editor to create a workflow for your leave requests. For more information about working with workflows, see [Create workflows overview](../fin-ops-core/fin-ops/organization-administration/create-workflow.md?toc=%2fdynamics365%2fcommerce%2ftoc.json.)

## Leave and absence request workflow data elements

You can use the following data elements to create conditional or automatic approvals in workflows for buy and sell leave requests:

- **Amount**
- **Buy and sell leave policy**
- **Company**
- **Created by**
- **Created date and time**
- **End date**
- **Leave type**
- **Modified by**
- **Modified date and time**
- **Request ID**
- **Start date**
- **Status** 
- **Submission date**
- **Submitted by**
- **Submitted by Human resources**
- **Submitted by Manager**
- **Submitted on behalf**
- **Worker**

## Workflow examples

These examples show how you can create different types of workflow conditions by using these data elements:

- Use **Submitted by Human resources** and **Submitted by manager** in an automatic action to automatically approve buy and sell leave requests that these roles submit on behalf of employees. For more information about automatic actions, see [Configure approval processes in a workflow](../fin-ops-core/fin-ops/organization-administration/configure-approval-process-workflow.md).

- Use **Leave type** in a conditional statement or automatic action to control how the workflow routes requests with certain leave types.

## See also

[Leave and absence overview](hr-leave-and-absence-overview.md)<br>
[Manage buy and sell leave policies](hr-leave-and-absence-manage-buy-and-sell-leave-policies.md)<br>
[Buy and sell leave](hr-employee-self-service-buy-sell-leave.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
