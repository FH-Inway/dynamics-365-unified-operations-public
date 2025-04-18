---
title: Apply updates to cloud environments
description: Learn about how to use Lifecycle Services (LCS) to apply a binary update or an application (AOT) deployable package to a cloud environment.
author: laneswenka
ms.author: laswenka
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/17/2025
ms.reviewer: johnmichalak
ms.assetid: 341a229f-d9c3-4678-b353-d08d5b2c1caf
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1
---

# Apply updates to cloud environments

[!include [banner](../includes/banner.md)]

This article describes how you can use Microsoft Dynamics Lifecycle Services (LCS) to automatically apply updates to cloud environments. 

> [!IMPORTANT]
> Updates are applied using deployable packages. Applying updates causes system downtime. All relevant services are stopped, and you won't be able to use your environments while the package is being applied. You should plan accordingly.

## Supported environments
All customer-managed and Microsoft-managed environments deployed through Lifecycle Services are supported. For more information about self-service environments, see [Update an environment](updateenvironment-newinfrastructure.md).

> [!NOTE]
> If you have a build environment, you can only use LCS to apply Binary updates and Data upgrade packages. You can't use LCS to apply an Application Deployable package.

For other environments (listed below), you must use Remote Desktop Protocol (RDP) to connect to the environment and install from the command line. For information about manual package deployment, see [Install deployable packages from the command line](install-deployable-package.md).

- Local development environments (Downloadable virtual hard disk [VHD])
- Multi-box dev/test environments in Microsoft Azure (Partner and trial projects)

## Key concepts

Before you begin, you should understand *deployable packages*, *runbooks*, and the *AXInstaller*. A deployable package is a unit of deployment that can be applied in any environment. A deployable package can be a binary update to the platform or other runtime components, an updated application (AOT) package, or a new application (AOT) package. The AXInstaller creates a runbook that enables installing a package. Learn more in [Packages, runbooks, and the AXUpdateInstaller in depth](apply-deployable-package-system.md#packages-runbooks-and-the-axupdateinstaller-in-depth) at the end of this article.

## Supported package types

- **AOT deployable package** – A deployable package that is generated from application metadata and source code. This deployable package is created in a development or build environment.
- **Application and Platform Binary update package** – A deployable package that contains dynamic-link libraries (DLLs) and other binaries and metadata that the platform and application depend on. This is a package released by Microsoft. This is available from the **All binary updates** tile from LCS.
- **Platform update package** – A deployable package that contains dynamic-link libraries (DLLs) and other binaries and metadata that the platform depends on. This is a package released by Microsoft. This is available from the **Platform binary updates** tile from LCS.
- **Commerce deployable package** – A combination of various packages that are generated after the Commerce code is combined.
- **Merged package** – A package that is created by combining one package of each type. For example, you can merge one binary update package and one AOT package, or one AOT package and one Commerce deployable package. The packages are merged in the Asset library for the project in LCS.
> [!NOTE] 
> A binary package and a Commerce deployable package can't be included in the same merged package.
>
> For information about how to download an update from LCS and what you see in the tiles based on your environment version, see [Download updates from Lifecycle Services (LCS)](../migration-upgrade/download-hotfix-lcs.md).
>
> If your environment is on an application version 8.1 and later, then the **Platform Update package** doesn't apply to your environment. Starting with 8.1 and later releases, **Application and Platform Binary update package** applies since application and platform are combined into a single cumulative package and is released by Microsoft. Note that you won't apply granular X++ hotfixes and will get all application and platform updates together. On the **Environment details** page, clicking on **View detailed version information** won't have details on the granular hotfixes or KBs applied as there's no way to apply them. 

## Prerequisite steps

- **Make sure that the package that should be applied is valid** - When a package is uploaded to the Asset library, it isn't analyzed. If you select the package, the package status appears in the right pane as **Not Validated**. A package must pass validation before it can be applied in an environment by using the following procedures. The status of the package is updated in the Asset library to indicate whether the package is valid. We require validation to help ensure that production environments aren't affected by packages that don't meet the guidelines.

    There are three types of validations:

    - Basic package format validations
    - Platform version checks
    - Types of packages

- **Make sure that the package is applied in a sandbox environment before it's applied in the production environment.** To help ensure that the production environment is always in a good state, we want to make sure that the package is tested in a sandbox environment before it's applied in the production environment. Therefore, before you request that the package be applied in your production environment, make sure that it has been applied in your sandbox environment by using the automated flows.
- **If you want to apply multiple packages, create a merged package that can be applied first in a sandbox environment and then in the production environment.** Application of a single package in an average environment requires about 5 hours of downtime. To avoid more hours of downtime when you must apply multiple packages, you can create a single combined package that contains one package of each type. If you select a binary package and an application deployable package in the Asset library, a **Merge** button becomes available on the toolbar. By clicking this button, you can merge the two packages into a single package and therefore reduce the total downtime by half.
- **Make sure that the application binary update package is applied to your dev/build environment AFTER it is applied to your sandbox and production environment** - If the application binary package is applied on your dev/build environment and this raises the platform build version to be higher than your target sandbox or production environment, you are blocked from applying any AOT packages that are produced from this dev/build environment. To apply AOT packages produced from a dev/build environment, your dev/build instance must be equal to or lower than your target environments.

## Apply a package to a nonproduction environment by using LCS

> [!NOTE]
> For self-service type environments, see [Update an environment](updateenvironment-newinfrastructure.md).

Before you begin, verify that the deployable package has been uploaded to the Asset library in LCS.

1. For a binary update, upload the package directly to the Asset library. For information about how to download an update from LCS, see [Download updates from Lifecycle Services (LCS)](../migration-upgrade/download-hotfix-lcs.md). For an application (AOT) deployable package that results from an X++ hotfix, or from application customizations and extensions, create the deployable package in your development or build environment, and then upload it to the Asset library.
2. Open the **Environment details** view for the environment where you want to apply the update.
3. Click **Maintain** &gt; **Apply updates** to apply an update.
4. Select the package to apply. Use the filter at the top to find your package.
5. Click **Apply**. Notice that the status in the upper-right corner of the **Environment details** view changes from **Queued** to **In Progress**, and an **Environment updates** section now shows the progress of the package. You can refresh the page to check the status. 
6. Continue to refresh the page to see the status updates for the package application request. When the package has been applied, the environment status changes to **Deployed**, and the servicing status changes to **Completed**.     

## Apply a package to a production environment by using LCS

In a production environment, customers can schedule a downtime for when they want the update to be applied. For self-service type environments, see [Update an environment](updateenvironment-newinfrastructure.md).  

> [!IMPORTANT]
> An important prerequisite for applying a package to a production environment is that the package must be successfully applied to at least one sandbox environment in the same project. 

## Troubleshoot package deployment failures

If package deployment fails, see [Troubleshoot package application issues](deployable-package-troubleshooting.md).

## Applying updates and extensions

If you're updating a Tier-2 Sandbox or Production environment on application version 8.1.2.x or newer and have initialized Cloud Scale Unit, you also need to update Commerce channel components. For more information, see [Update Retail Cloud Scale Unit](Update-retail-channel.md).

If you're using components (such as Modern POS), after you've applied updates and extensions in your environment, you must also update your in-store components. For more information, see [Configure, install, and activate Modern POS (MPOS)](../../../commerce/retail-modern-pos-device-activation.md).

## Packages, runbooks, and the AXUpdateInstaller in depth

Deployable packages, runbooks, and the AXUpdateInstaller are the tools you use to apply updates. 

**Deployable package** – A deployable package is a unit of deployment that can be applied in an environment. A deployable package can be a binary update to the platform or other runtime components, an updated application (AOT) package, or a new application (AOT) package. 

[![Example of a deployable package.](./media/applypackage_deployablepackage.jpg)](./media/applypackage_deployablepackage.jpg)

**Runbook** – The deployment runbook is a series of steps that are generated in order to apply the deployable package to the target environment. Some steps are automated, and some steps are manual. AXUpdateInstaller lets you run these steps 1 at a time and in the correct order.

**AXUpdateInstaller** – When you create a customization package from Microsoft Visual Studio or a Microsoft binary update, the installer executable is bundled together with the deployable package. The installer generates the runbook for the specified topology. The installer can also run steps in order, according to the runbook for a specific topology.

## More information

[Install deployable packages from the command line](install-deployable-package.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
