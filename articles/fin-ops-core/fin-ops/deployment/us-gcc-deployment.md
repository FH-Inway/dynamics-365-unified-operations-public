---
title: Dynamics 365 Finance and Supply Chain Management in US Government Community Cloud (GCC)
description: Learn about Microsoft Dynamics 365 US Government products that are available to qualified government and private entities.
author: hasaid
ms.author: epegors
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 01/22/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-11-09
---

# Dynamics 365 Finance and Supply Chain Management in US Government Community Cloud (GCC)

[!include [banner](../../../finance/includes/banner.md)]

Select Microsoft Dynamics 365 United States (US) Government products are available to qualified government and private entities. Those entities are limited to the following types:

- US federal, state, local, tribal, and territorial government entities
- Private entities that use Dynamics 365 US Government to provide solutions to government entities or to qualified members of the cloud community
- Private entities that have customer data that is subject to government regulations, and Dynamics 365 US Government is the appropriate service to meet the regulatory requirements

For information, see [Dynamics 365 US Government](/power-platform/admin/microsoft-dynamics-365-government).

## Onboarding

To complete the initial onboarding for an implementation project in Microsoft Dynamics Lifecycle Services, follow the instructions in [Onboard an implementation project](../../dev-itpro/organization-administration/onboard.md). However, don't use the link to public Lifecycle Services that is provided in those instructions. Instead, use the following URL to open Lifecycle Services for US Government Community Cloud (GCC): <https://gov.lcs.microsoftdynamics.us>.

After the initial onboarding is completed, follow the instructions in [Project onboarding](../../dev-itpro/lifecycle-services/project-onboarding.md). Once again, use [Lifecycle Services for GCC](https://gov.lcs.microsoftdynamics.us) instead of public Lifecycle Services.

## Environment deployment

After you've completed project onboarding, you can review the additional capabilities of Lifecycle Services that are described in [Lifecycle Services for finance and operations apps customers](../../dev-itpro/lifecycle-services/lcs-works-lcs.md). Then move on to environment deployment.

- To deploy Microsoft-managed environments via Lifecycle Services, follow the instructions in [Lifecycle Services for finance and operations apps customers](../../dev-itpro/lifecycle-services/lcs-works-lcs.md#new-deployment-experience).
- For cloud-hosted environments, see [Deploy and access development environments](../../dev-itpro/dev-tools/access-instances.md). You must also complete the Resource Manager onboarding process for your connectors, as described in [Complete the Azure Resource Manager onboarding process for US government Lifecycle Services projects](../../dev-itpro/deployment/arm-onbarding-us-goverment.md).

> [!NOTE]
> For US Government Lifecycle Services projects, only Azure Government–specific Azure subscriptions are supported.

## Features that aren't available

Some features won't be available for deployment in GCC, or they won't be available to use with Dynamics 365 in GCC. For example, Azure DevOps Services will be unavailable in GCC. However, on-premises Azure DevOps or public Azure DevOps services can be used. For detailed information about feature availability, see [Business Applications US Government Feature Availability](https://aka.ms/BAPFunctionalParity).

## Frequently asked questions

### Are Dynamics 365 Finance and Dynamics 365 Supply Chain Management supported in GCC and GCC-High environments?

Yes. Dynamics 365 Finance and Dynamics 365 Supply Chain Management are supported in both US Government Community Cloud (GCC) and GCC-High environments.

### Can I deploy Copilot features in GCC and GCC-High environments?

Yes, you can deploy Copilot features for Dynamics 365 Finance and Dynamics 365 Supply Chain Management in US Government Community Cloud (GCC) and GCC-High environments. However, Copilot capabilities aren't deployed by default in these environments. Copilot features are only available in GCC and GCC-High environments after an admin installs the required Copilot apps in Dataverse.

Learn more in [Enable Copilot capabilities in finance and operations apps](../../dev-itpro/copilot/enable-copilot.md).

### Can I use public Azure DevOps with Finance and Supply Chain Management in GCC?

Yes, you can use public Azure DevOps services if you don't have requirements for a solution that is certified by the Federal Risk and Authorization Management Program (FEDRAMP). Alternatively, you can use Azure DevOps Server.

### Can I deploy a cloud-hosted environment Tier-1 development environment on an Azure commercial subscription?

No. In [Lifecycle Services for GCC](https://gov.lcs.microsoftdynamics.us) and [Lifecycle Services for GCC High](https://high.lcs.microsoftdynamics.us), you must use an Azure Government subscription to deploy a cloud-hosted environment.

### What can I do if I need a package from the Shared asset library, but it isn't available in Lifecycle Services for GCC?

You can download the same package from the Shared asset library in [public Lifecycle Services](https://lcs.dynamics.com). Alternatively, your partner can help you download the package.

### Is the code upgrade tool available in GCC?

No, the code upgrade tool isn't currently available in GCC. However, you can create a prospect project in [public Lifecycle Services](https://lcs.dynamics.com) and use the code upgrade tool. Note that you won't be able to deploy environments in prospect projects.

### Can my partner open a support ticket on my behalf?

Yes. However, if your partner uses a non-GCC identity, the support ticket will be directed to the public support queue. We recommend that you use customer GCC entitlement in Lifecycle Services to open support tickets.

## See also

- [Dynamics 365 US Government](/power-platform/admin/microsoft-dynamics-365-government)
- [Business Applications US Government Feature Availability](https://aka.ms/BAPFunctionalParity).
- [Lifecycle Services user guide](../../dev-itpro/lifecycle-services/lcs-user-guide.md)
- [Cloud deployment overview](../../dev-itpro/deployment/cloud-deployment-overview.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
