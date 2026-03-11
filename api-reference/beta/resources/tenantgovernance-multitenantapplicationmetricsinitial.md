---
title: "multiTenantApplicationMetricsInitial resource type"
description: "Represents the initial snapshot of multi-tenant application metrics when the relationship was first discovered."
author: "akhil-potturi"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# multiTenantApplicationMetricsInitial resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents the initial snapshot of multi-tenant application metrics captured when the relationship was first discovered, establishing a baseline for application usage across tenant boundaries.

## Properties
|Property|Type|Description|
|:---|:---|:---|
|createdDateTime|DateTimeOffset|**TODO: Add Description**|
|inboundMonthlyTotalApplications|Decimal|**TODO: Add Description**|
|outboundMonthlyTotalApplications|Decimal|**TODO: Add Description**|
|watermarkDateTime|DateTimeOffset|**TODO: Add Description**|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.multiTenantApplicationMetricsInitial"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.multiTenantApplicationMetricsInitial",
  "createdDateTime": "String (timestamp)",
  "watermarkDateTime": "String (timestamp)",
  "inboundMonthlyTotalApplications": "Decimal",
  "outboundMonthlyTotalApplications": "Decimal"
}
```

