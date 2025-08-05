---
title: Uninstall Business performance analytics
description: Learn how to uninstall Business performance analytics.
author: lizmota
ms.author: jiwo
ms.topic: faq
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.date: 9/11/2024
---

# Uninstall Business performance analytics

Two options are available for uninstalling Business performance analytics: code-based uninstallation and manual uninstallation.

If you must reinstall Business performance analytics after you uninstall it, wait four hours before reinstallation.

> [!NOTE]
> If you uninstall and then reinstall Business performance analytics, no new reports that were created are saved.

## Option 1: Code-based uninstallation

1. Sign in to the [Microsoft Power Platform admin center](https://admin.powerplatform.microsoft.com/) by using Dataverse admin credentials.
2. Select the environment where you want to uninstall Business performance analytics.
3. Select the environment URL that is provided in the details. You're redirected to the sign-in page for the Dataverse environment.
4. Open your browser's developer tools by selecting **Ctrl**+**Shift**+**I** or going to **More tools** \> **Developer tools**. Then select the **Console** tab to open the developer console.
5. Copy the following JavaScript code, and paste it into the developer console to start the uninstallation process.

    ```javascript
    // Get the current org URL
    const ORG = window.location.hostname;
    const WEB_API = `https://${ORG}/api/data/v9.2`;
    const SOLUTIONS = [
        "msdyn_BpaAnchor",
        "msdyn_Bpa",
        "msdyn_BpaReports",
        "msdyn_BpaPlugins",
        "msdyn_BpaPermissions",
        "msdyn_BpaTables",
        "msdyn_BpaControls",
        "msdyn_BpaTablesAnchorSolution",
        "msdyn_BpaTablesUserRoles",
        "msdyn_BpaAnalyticalTablesWorkspace",
        "msdyn_BpaAnalyticalTables",
        "msdyn_BpaTablesTransformationJobFlows",
        "msdyn_BpaTablesDataProcessingConfigurations",
        "msdyn_BpaTablesDataLakeSynchronizationWorkspace",
        "msdyn_BpaTablesDataLakeSynchronization",
        "msdyn_BpaTablesVirtualEntitiesWorkspace",
        "msdyn_BpaTablesVirtualEntities",
        "msdyn_BpaTablesManagedDataLake",
        "msdyn_BpaPipelinePlugins",
        "msdyn_BpaTablesSecurity",
        "msdyn_BpaConfig"
    ];
    
    // Get all solutions
    let _getSolutions = () => {
        var requestOptions = {
            method: "GET",
        };
        return fetch(
            `${WEB_API}/solutions?$filter=(isvisible%20eq%20true)&$select=solutionid,friendlyname,uniquename`,
            requestOptions
        ).then((response) => response.json());
    };
    
    // Delete the solution by solution ID
    let _deleteSolution = (solutionid) => {
        var requestOptions = {
            method: "DELETE",
        };
        return fetch(`${WEB_API}/solutions(${solutionid})`, requestOptions);
    };
    let start = async () => {
        console.info("Uninstalling BPA solutions");
        let installedSolutions = (await _getSolutions()).value;
    
        // Sort the installed BPA solutions 
         let installedBPASoltuins = installedSolutions
            .filter((i) => SOLUTIONS.indexOf(i.uniquename) > -1)
            .sort(
                (i, j) =>
                    SOLUTIONS.indexOf(i.uniquename) - SOLUTIONS.indexOf(j.uniquename)
            );
        for (let solution of installedBPASoltuins) {
            console.info(`Removing solution ${solution.friendlyname}`);
            await _deleteSolution(solution.solutionid);
        }
        console.info("BPA Solutions removed successfully");
    };
    
    start();
    ```

Deletion of all the solutions requires approximately 20 minutes. If the operation is successful, you receive the following message: "Business performance analytics solutions removed successfully."

## Option 2: Manual uninstallation

You can manually uninstall Business performance analytics through the Power Platform admin center. The solutions must be manually deleted in the following order:

1. Business performance analytics anchor solution
2. Business performance analytics solution
3. Business performance analytics reports 
4. Business performance analytics plugins solution
5. Business performance analytics permissions 
6. Business performance analytics tables
7. Business performance analytics controls
8. Business performance analytics tables anchor solution
9. Business performance analytics tables user roles 
10. Business performance analytics analytical tables workspace
11. Business performance analytics analytical tables
12. Business performance analytics tables transformation job flows
13. Business performance analytics tables data processing configuration 
14. Business performance analytics tables data lake synchronization workspace
15. Business performance analytics tables data lake synchronization
16. Business performance analytics tables virtual entities workspace
17. Business performance analytics tables virtual entities
18. Business performance analytics tables managed data lake 
19. Business performance analytics pipeline plugins solution
20. Business performance analytics tables security 
21. Business performance analytics config 

To delete each of the preceding solutions, follow these steps.

1. In [Power Apps](https://make.preview.powerapps.com/), on the left navigation pane, select **Solutions**.
2. Select the solution to delete, and then select **Delete**.
3. Select **Delete** again to confirm the operation.
4. Wait for the **Deleting** message box to disappear.

Deletion of all the solution requires approximately 20 minutes. If the operation is successful, you receive the following message: "Successfully deleted solution."
