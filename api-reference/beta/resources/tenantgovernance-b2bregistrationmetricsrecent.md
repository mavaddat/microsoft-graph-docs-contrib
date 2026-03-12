---
title: "b2BRegistrationMetricsRecent resource type"
description: "Represents the most recent snapshot of B2B registration metrics."
author: "akhil-potturi"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# b2BRegistrationMetricsRecent resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents the most recent snapshot of B2B registration metrics, showing current guest counts between related tenants.

## Properties
|Property|Type|Description|
|:---|:---|:---|
|updateDateTime|DateTimeOffset|Timestamp that represents the most recent time B2B registration data was aggregated and have sufficiently changed for the related tenant.|
|watermarkDateTime|DateTimeOffset|Timestamp that represents the earliest segment of data missing within the aggregation window. When no data is missing, this value is within one day of the associated updateDateTime property.|
|inboundTotalUsers|Int64|Count of B2B guests invited and accepted from the related tenant into the calling tenant at the time of initial aggregation.|
|outboundTotalUsers|Int64|Count of B2B guests invited and accepted from the calling tenant that are provisioned into the related tenant at the time of initial aggregation.|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.b2BRegistrationMetricsRecent"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.b2BRegistrationMetricsRecent",
  "updateDateTime": "String (timestamp)",
  "watermarkDateTime": "String (timestamp)",
  "inboundTotalUsers": "Int64",
  "outboundTotalUsers": "Int64"
}
```

