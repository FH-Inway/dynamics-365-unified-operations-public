---
title: Chat with finance and operations data (preview)
description: Learn how to configure finance and operations data as knowledge sources to enable chat experiences with your enterprise data
author: jaredha
ms.author: jaredha
ms.reviewer: johnmichalak
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 02/24/2025

---

# Chat with finance and operations data (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The Microsoft agent platform enables you to chat with your finance and operations data to enable users to ask questions of an agent that derives the answers from the structured finance and operations data to which the user has access. You can enable this feature in Copilot Studio by adding finance and operations data as knowledge sources to your agents to give you the flexibility to add the right knowledge for your desired agent experiences. For more information, see [Knowledge sources overview](/microsoft-copilot-studio/knowledge-copilot-studio)

## Adding knowledge sources to your copilots
You can add your finance and operations structured data as a knowledge source in many different agent experiences. For example, you can configure [virtual entities for finance and operations apps](../power-platform/virtual-entities-overview.md) as knowledge sources in your agent. You can also add a native Dataverse table as a knowledge source for an agent to provide relevant information and insights to the end user in the targeted agent experience. You can then synchronize your finance and operations data to Dataverse using a data sync utility like [Dual-write](../data-entities/dual-write/dual-write-overview.md), and have the data available for Q&A as a knowledge source from the Dataverse table. The virtual entities and tables can be added to Copilot for finance and operations apps, custom agents, Microsoft 365 copilot, or other agents that support knowledge sources.

### Add knowledge to Copilot for finance and operations apps or custom agents
Extending Copilot for finance and operations apps with knowledge sources enables users of the in-app sidecar chat to ask questions about the structured data within the context of the application. You can add this same experience to your custom agents by adding the finance and operations data as a knowledge source to the agent in Copilot Studio. For more information about how to add the knowledge source to these agents, see [Add a Dataverse knowledge source](/microsoft-copilot-studio/knowledge-add-dataverse).

### Extend Microsoft 365 Copilot with finance and operations data
Microsoft 365 Copilot is the default experience for engaging with content and resources across your organization. You can extend this experience by adding finance and operations data as a knowledge source to enable users to ask questions about the ERP data directly from Microsoft 365 Copilot. This is done by adding and creating a new declarative agent. In this agent, you add all the actions and knowledge you want to have available to users of the agent and publish the agent to Microsoft 365 Copilot.

For more information about creating and publishing declarative agents to extend Microsoft 365 Copilot, including [adding knowledge to the agent](/microsoft-copilot-studio/microsoft-copilot-extend-copilot-extensions#add-knowledge-to-a-copilot-agent),
see [Extend Microsoft 365 Copilot with Copilot agents](/microsoft-copilot-studio/microsoft-copilot-extend-copilot-extensions).
