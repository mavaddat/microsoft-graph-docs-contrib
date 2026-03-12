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
|createdDateTime|DateTimeOffset|Timestamp that represents when multitenant application metrics are initially aggregated for the related tenant.|
|watermarkDateTime|DateTimeOffset|Timestamp that represents the earliest segment of data missing within the aggregation window. When no data is missing, this value is within one day of the associated createdDateTime property.|
|inboundMonthlyTotalApplications|Int64|Count of applications in the related tenant that have been consented into the calling tenant. Lookback period is 30 days.|
|outboundMonthlyTotalApplications|Int64|Count of applications in the calling tenant that have been consented into the related tenant. Lookback period is 30 days.|
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
  "inboundMonthlyTotalApplications": "Int64",
  "outboundMonthlyTotalApplications": "Int64"
}
```

