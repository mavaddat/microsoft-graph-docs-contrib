---
title: "multiTenantApplicationMetricsRecent resource type"
description: "Represents the most recent snapshot of multi-tenant application metrics."
author: "akhil-potturi"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# multiTenantApplicationMetricsRecent resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents the most recent snapshot of multi-tenant application metrics, showing current application usage across tenant boundaries.

## Properties
|Property|Type|Description|
|:---|:---|:---|
|inboundMonthlyTotalApplications|Decimal|**TODO: Add Description**|
|outboundMonthlyTotalApplications|Decimal|**TODO: Add Description**|
|updateDateTime|DateTimeOffset|**TODO: Add Description**|
|watermarkDateTime|DateTimeOffset|**TODO: Add Description**|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.multiTenantApplicationMetricsRecent"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.multiTenantApplicationMetricsRecent",
  "updateDateTime": "String (timestamp)",
  "watermarkDateTime": "String (timestamp)",
  "inboundMonthlyTotalApplications": "Decimal",
  "outboundMonthlyTotalApplications": "Decimal"
}
```

