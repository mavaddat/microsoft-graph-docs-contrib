---
title: "b2bRegistrationMetrics resource type"
description: "Represents B2B collaboration guest registration metrics between two related tenants."
author: "akhil-potturi"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# b2bRegistrationMetrics resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents B2B collaboration metrics that track guest registrations between the calling tenant and a related tenant. Includes both initial and recent snapshots showing inbound and outbound guest counts.

## Properties
|Property|Type|Description|
|:---|:---|:---|
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. |
| inboundTotalUsers | Int64 | The total number of inbound B2B guest users registered. |
| outboundTotalUsers | Int64 | The total number of outbound B2B users from this tenant registered in other tenants. |

## Relationships
|Property|Type|Description|
|:---|:---|:---|
|initial|[microsoft.graph.tenantGovernanceServices.b2BRegistrationMetricsInitial](../resources/tenantgovernanceservices-b2bregistrationmetricsinitial.md)|B2B registration metrics correpsionding to initial snapshots where metrics were aggregated for the first time.|
|recent|[microsoft.graph.tenantGovernanceServices.b2BRegistrationMetricsRecent](../resources/tenantgovernanceservices-b2bregistrationmetricsrecent.md)|B2B registration metrics correpsionding to recent snapshots where metrics were found to have sufficiently changed.|

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.b2bRegistrationMetrics"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.b2bRegistrationMetrics",
  "initial": {"@odata.type": "microsoft.graph.tenantGovernanceServices.b2BRegistrationMetricsInitial"},
  "recent": {"@odata.type": "microsoft.graph.tenantGovernanceServices.b2BRegistrationMetricsRecent"}
}
```

