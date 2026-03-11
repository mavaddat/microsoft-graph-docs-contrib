---
title: "b2BRegistrationMetricsInitial resource type"
description: "Represents the initial snapshot of B2B registration metrics when the relationship was first discovered."
author: "akhil-potturi"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# b2BRegistrationMetricsInitial resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents the initial snapshot of B2B registration metrics captured when the relationship between two tenants was first discovered, establishing a baseline for guest user counts.

## Properties
|Property|Type|Description|
|:---|:---|:---|
|createdDateTime|DateTimeOffset|Timestamp which represents the date time that B2B registration data was initially aggregated.|
|watermarkDateTime|DateTimeOffset|Timestamp which represents the earliest segment of data missing within the aggregation window. When no data is missing, this value will be within one day of the associated createdDateTime property.|
|inboundTotalUsers|Decimal|Count of B2B guest users invited and accepted into the calling tenant from the related tenant at the time of initial aggregation.|
|outboundTotalUsers|Decimal|Count of B2B guest users invited and accepted from the calling tenant and provisioned into the related tenant at the time of initial aggregation.|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.b2BRegistrationMetricsInitial"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.b2BRegistrationMetricsInitial",
  "createdDateTime": "String (timestamp)",
  "watermarkDateTime": "String (timestamp)",
  "inboundTotalUsers": "Decimal",
  "outboundTotalUsers": "Decimal"
}
```

