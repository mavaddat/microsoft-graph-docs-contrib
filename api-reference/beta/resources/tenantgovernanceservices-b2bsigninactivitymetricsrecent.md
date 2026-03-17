---
title: "b2BSignInActivityMetricsRecent resource type"
description: "Represents the most recent snapshot of B2B sign-in activity metrics."
author: "akhil-potturi"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# b2BSignInActivityMetricsRecent resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents the most recent snapshot of B2B sign-in activity metrics, showing current monthly active guests and application counts.

## Properties
|Property|Type|Description|
|:---|:---|:---|
|updateDateTime|DateTimeOffset|Timestamp that represents the most recent time B2B registration data was aggregated and have sufficiently changed for the related tenant.|
|watermarkDateTime|DateTimeOffset|Timestamp that represents the earliest segment of data missing within the aggregation window. When no data is missing, this value is within one day of the associated updateDateTime property.|
|inboundMonthlyTotalUsers|Int64|Count of distinct users from the related tenant who signed-in to an application in the calling tenant in the past 30 days.|
|inboundMonthlyTotalApplications|Int64|Count of distinct applications in the calling tenant with sign-ins from users in the related tenant in the past 30 days.|
|outboundMonthlyTotalUsers|Int64|Count of distinct users from the calling tenant who signed-in to an application in the related tenant in the past 30 days.|
|outboundMonthlyTotalApplications|Int64|Count of distinct applications in the related tenant with sign-ins from users in the calling tenant in the past 30 days.|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.b2BSignInActivityMetricsRecent"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.b2BSignInActivityMetricsRecent",
  "updateDateTime": "String (timestamp)",
  "watermarkDateTime": "String (timestamp)",
  "inboundMonthlyTotalUsers": "Int64",
  "inboundMonthlyTotalApplications": "Int64",
  "outboundMonthlyTotalUsers": "Int64",
  "outboundMonthlyTotalApplications": "Int64"
}
```

