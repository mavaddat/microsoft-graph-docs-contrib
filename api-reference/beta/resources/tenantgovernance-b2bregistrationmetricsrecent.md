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

Represents the most recent snapshot of B2B registration metrics, showing current guest user counts between related tenants.

## Properties
|Property|Type|Description|
|:---|:---|:---|
|updateDateTime|DateTimeOffset|Timestamp which represents the most recent time B2B registration data was aggregated and found to have sufficiently changed for the related tenant.|
|watermarkDateTime|DateTimeOffset|Timestamp which represents the earliest segment of data missing within the aggregation window. When no data is missing, this value will be within one day of the associated updateDateTime property.|
|inboundTotalUsers|Int64|Count of B2B guest users invited and accepted into the calling tenant from the related tenant.|
|outboundTotalUsers|Int64|Count of B2B guest users invited and accepted from the calling tenant and provisioned into the related tenant.|

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

