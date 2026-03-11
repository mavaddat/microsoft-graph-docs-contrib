---
title: "b2bRegistrationMetrics resource type"
description: "Represents B2B collaboration guest user registration metrics between two related tenants."
author: "akhil-potturi"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# b2bRegistrationMetrics resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents B2B collaboration metrics that track guest user registrations between the calling tenant and a related tenant. Includes both initial and recent snapshots showing inbound and outbound guest user counts.

## Properties
|Property|Type|Description|
|:---|:---|:---|
|initial|[microsoft.graph.tenantGovernanceServices.b2BRegistrationMetricsInitial](../resources/tenantgovernance-b2bregistrationmetricsinitial.md)|B2B registration metrics correpsionding to initial snapshots where metrics were aggregated for the first time.|
|recent|[microsoft.graph.tenantGovernanceServices.b2BRegistrationMetricsRecent](../resources/tenantgovernance-b2bregistrationmetricsrecent.md)|B2B registration metrics correpsionding to recent snapshots where metrics were found to have sufficiently changed.|

## Relationships
None.

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

