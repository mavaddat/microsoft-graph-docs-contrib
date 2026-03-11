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
|initial|[microsoft.graph.tenantGovernanceServices.b2BSignInActivityMetricsInitial](../resources/tenantgovernance-b2bsigninactivitymetricsinitial.md)|B2B sign-in activity metrics correpsionding to initial snapshots where metrics were aggregated for the first time.|
|recent|[microsoft.graph.tenantGovernanceServices.b2BSignInActivityMetricsRecent](../resources/tenantgovernance-b2bsigninactivitymetricsrecent.md)|B2B sign-in activity metrics correpsionding to recent snapshots where metrics were found to have sufficiently changed.|

## Relationships
None.

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

