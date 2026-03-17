---
title: "b2BSignInActivityMetrics resource type"
description: "Represents B2B sign-in activity metrics showing guest user authentication between two related tenants."
author: "akhil-potturi"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# b2BSignInActivityMetrics resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents B2B sign-in activity metrics that track monthly active guest users and applications accessed between the calling tenant and a related tenant. Includes both initial and recent snapshots with inbound and outbound activity counts.

## Properties
|Property|Type|Description|
|:---|:---|:---|
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. |
| inboundMonthlyTotalUsers | Int64 | The total number of unique inbound users with sign-in activity in the last month. |
| inboundMonthlyTotalApplications | Int64 | The total number of applications accessed by inbound users in the last month. |
| outboundMonthlyTotalUsers | Int64 | The total number of unique outbound users with sign-in activity in the last month. |
| outboundMonthlyTotalApplications | Int64 | The total number of applications accessed by outbound users in the last month. |

## Relationships
|Property|Type|Description|
|:---|:---|:---|
|initial|[microsoft.graph.tenantGovernanceServices.b2BSignInActivityMetricsInitial](../resources/tenantgovernanceservices-b2bsigninactivitymetricsinitial.md)|B2B sign-in activity metrics correpsionding to initial snapshots where metrics were aggregated for the first time.|
|recent|[microsoft.graph.tenantGovernanceServices.b2BSignInActivityMetricsRecent](../resources/tenantgovernanceservices-b2bsigninactivitymetricsrecent.md)|B2B sign-in activity metrics correpsionding to recent snapshots where metrics were found to have sufficiently changed.|

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.b2BSignInActivityMetrics"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.b2BSignInActivityMetrics",
  "initial": {"@odata.type": "microsoft.graph.tenantGovernanceServices.b2BSignInActivityMetricsInitial"},
  "recent": {"@odata.type": "microsoft.graph.tenantGovernanceServices.b2BSignInActivityMetricsRecent"}
}
```

