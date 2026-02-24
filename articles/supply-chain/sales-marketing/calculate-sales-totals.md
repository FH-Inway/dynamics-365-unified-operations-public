---
title: Configure the Calculate sales totals batch job
description: Learn how to use and configure the Calculate sales totals batch job in Dynamics 365 Finance & Operations, including parameters, performance guidance, and recommended usage.
author: AditiPattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form: Periodic tasks, Batch jobs
ms.topic: how-to
ms.date: 02/25/2025
ms.custom: 
  - bap-template
---

# Configure the *Calculate sales totals* batch job

[!include [banner](../../includes/banner.md)]

The **Calculate sales totals** process recalculates aggregated metrics for **sales orders** and **sales quotations**. These pre‑computed totals improve performance across inquiry pages, workspaces, and reporting experiences by ensuring consistent, up‑to‑date KPI values.

This article describes the purpose of each field on the form, how to schedule the job, and performance considerations.


## Overview

The form allows administrators to control how far back the system recalculates sales totals and whether the job runs interactively or as a scheduled batch process. The recalculation updates:

- Order‑level totals  
- Quotation‑level totals  
- Aggregated values used by workspaces, analytics, and reporting  
- KPI caches across Sales and Retail/Commerce experiences  


## Parameters

### **Ignore documents updated before (days)**  
Defines how many days of activity to include in the recalculation.  
The system computes a cutoff date as:
Cutoff date = Today – <entered number="" of="" days=""></entered>

Only documents updated *after* this date are recalculated.

**Usage guidance**  
- Use **7–30 days** for routine recalculations.  
- Avoid full historical recalculation in high‑volume environments unless necessary.


### **Calculate totals for sales orders**  
Enables recalculation of aggregated totals for **sales orders**, including:

- Order‑level summary totals  
- Line‑level aggregated contributions  
- Delivery totals  
- Remaining quantities and values  
- KPI totals used in workspaces and analytics  

Disable only in niche scenarios where sales orders are not part of the workflow.


### **Calculate totals for sales quotations**  
Recalculates totals for **sales quotations**, including:

- Quotation value summaries  
- Aggregated line‑level metrics  
- Totals used in quotation inquiry and reporting  

Disable if the organization does not use the sales quotation process.


### **Number of threads**  
Controls the degree of **parallel processing** for the recalculation.

- Higher values may improve performance on large datasets.  
- High thread counts can also increase SQL/compute contention.  
- Leave at **0** to let the system decide automatically.


## Run in the background

Standard D365 batch framework capabilities are available, including:

- **Run now**  
- **Schedule** (hourly, nightly, weekly)  
- **Assign batch group**  
- **Set alerts** for completion or failures  

A recurring schedule is recommended to keep sales KPIs fresh.


## Usage recommendations

Run this job:

- After **bulk data imports** (DMF/integrations).  
- After **mass updates** to sales orders or quotations.  
- As part of **month‑end closing**.  
- On a **nightly schedule** to maintain accurate workspace KPI totals.


## Performance considerations

- Avoid full recalculation during **peak business hours**.  
- Prefer targeted recalculation using the *days* parameter.  
- If totals appear incorrect, investigate whether customizations bypass update triggers.
