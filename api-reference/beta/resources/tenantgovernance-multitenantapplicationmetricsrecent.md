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
|updateDateTime|DateTimeOffset|Timestamp which represents when multitenant application metrics are aggregated and found to have sufficiently changed for the related tenant.|
|watermarkDateTime|DateTimeOffset|Timestamp which represents the earliest segment of data missing within the aggregation window. When no data is missing, this value will be within one day of the associated updateDateTime property.|
|inboundMonthlyTotalApplications|Int64|Count of applications in the related tenant that have been consented into the calling tenant. Lookback period is 30 days.|
|outboundMonthlyTotalApplications|Int64|Count of applications in the calling tenant that have been consented into the related tenant. Lookback period is 30 days.|

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
  "inboundMonthlyTotalApplications": "Int64",
  "outboundMonthlyTotalApplications": "Int64"
}
```

