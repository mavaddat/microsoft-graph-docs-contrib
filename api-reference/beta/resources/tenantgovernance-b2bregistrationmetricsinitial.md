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

Represents the initial snapshot of B2B registration metrics captured when the relationship between two tenants was first discovered, establishing a baseline for guest counts.

## Properties
|Property|Type|Description|
|:---|:---|:---|
|createdDateTime|DateTimeOffset|Timestamp that represents the date time that B2B registration data was initially aggregated.|
|watermarkDateTime|DateTimeOffset|Timestamp that represents the earliest segment of data missing within the aggregation window. When no data is missing, this value is within one day of the associated createdDateTime property.|
|inboundTotalUsers|Int64|Count of B2B guests invited and accepted from the related tenant into the calling tenant at the time of initial aggregation.|
|outboundTotalUsers|Int64|Count of B2B guests invited and accepted from the calling tenant that are provisioned into the related tenant at the time of initial aggregation.|

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
  "inboundTotalUsers": "Int64",
  "outboundTotalUsers": "Int64"
}
```

