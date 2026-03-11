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

Represents the most recent snapshot of B2B sign-in activity metrics, showing current monthly active guest user and application counts.

## Properties
|Property|Type|Description|
|:---|:---|:---|
|updateDateTime|DateTimeOffset|Timestamp which represents the most recent time B2B registration data was aggregated and found to have sufficiently changed for the related tenant.|
|watermarkDateTime|DateTimeOffset|Timestamp which represents the earliest segment of data missing within the aggregation window. When no data is missing, this value will be within one day of the associated updateDateTime property.|
|inboundMonthlyTotalUsers|Decimal|Count of distinct users from the related tenant who signed-in to an application in the calling tenant in the past 30 days.|
|inboundMonthlyTotalApplications|Decimal|Count of distinct applications in the calling tenant with sign-ins from users in the related tenant in the past 30 days.|
|outboundMonthlyTotalUsers|Decimal|Count of distinct users from the calling tenant who signed-in to an application in the related tenant in the past 30 days.|
|outboundMonthlyTotalApplications|Decimal|Count of distinct applications in the related tenant with sign-ins from users in the calling tenant in the past 30 days.|

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
  "inboundMonthlyTotalUsers": "Decimal",
  "inboundMonthlyTotalApplications": "Decimal",
  "outboundMonthlyTotalUsers": "Decimal",
  "outboundMonthlyTotalApplications": "Decimal"
}
```

