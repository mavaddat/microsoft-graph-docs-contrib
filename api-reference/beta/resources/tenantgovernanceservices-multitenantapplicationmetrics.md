---
title: "multiTenantApplicationMetrics resource type"
description: "Represents multi-tenant application usage metrics between two related tenants."
author: "akhil-potturi"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# multiTenantApplicationMetrics resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents multi-tenant application usage metrics that track the number of applications used across tenant boundaries. Includes both initial and recent snapshots showing monthly counts of inbound and outbound multi-tenant application usage.

## Properties
|Property|Type|Description|
|:---|:---|:---|
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. |
| inboundMonthlyTotalApplications | Decimal | The total number of inbound multi-tenant applications in the last month. |
| outboundMonthlyTotalApplications | Decimal | The total number of outbound multi-tenant applications in the last month. |

## Relationships
|Property|Type|Description|
|:---|:---|:---|
|initial|[microsoft.graph.tenantGovernanceServices.multiTenantApplicationMetricsInitial](../resources/tenantgovernanceservices-multitenantapplicationmetricsinitial.md)|Multitenant application metrics correpsionding to initial snapshots where metrics were aggregated for the first time.|
|recent|[microsoft.graph.tenantGovernanceServices.multiTenantApplicationMetricsRecent](../resources/tenantgovernanceservices-multitenantapplicationmetricsrecent.md)|Multitenant application metrics correpsionding to recent snapshots where metrics were found to have sufficiently changed.|

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.multiTenantApplicationMetrics"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.multiTenantApplicationMetrics",
  "initial": {"@odata.type": "microsoft.graph.tenantGovernanceServices.multiTenantApplicationMetricsInitial"},
  "recent": {"@odata.type": "microsoft.graph.tenantGovernanceServices.multiTenantApplicationMetricsRecent"}
}
```

