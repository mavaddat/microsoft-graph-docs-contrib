---
title: "billingMetrics resource type"
description: "Represents billing account connection metrics showing commerce relationships between two related tenants."
author: "akhil-potturi"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# billingMetrics resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents billing metrics that show commerce and billing account connections between the calling tenant and a related tenant. Tracks associated tenant relationships where one tenant manages billing or provisioning for another tenant's subscriptions. Includes both initial and recent snapshots with local (calling tenant as primary billing tenant) and foreign (related tenant as primary billing tenant) connection counts.

## Properties
|Property|Type|Description|
|:---|:---|:---|
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. |
| localAssociatedTenantCount | Decimal | The total number of local associated tenants. |
| localAssociatedTenantBillingManagementActiveCount | Decimal | The number of local associated tenants with active billing management. |
| localAssociatedTenantProvisioningActiveCount | Decimal | The number of local associated tenants with active provisioning. |
| localAssociatedTenantIds | Collection(String) | The list of local associated tenant IDs. |
| foreignAssociatedTenantCount | Decimal | The total number of foreign associated tenants. |
| foreignAssociatedTenantBillingManagementActiveCount | Decimal | The number of foreign associated tenants with active billing management. |
| foreignAssociatedTenantProvisioningActiveCount | Decimal | The number of foreign associated tenants with active provisioning. |

## Relationships
|Property|Type|Description|
|:---|:---|:---|
|initial|[microsoft.graph.tenantGovernanceServices.billingMetricsInitial](../resources/tenantgovernanceservices-billingmetricsinitial.md)|Billing metrics correpsionding to initial snapshots where metrics were aggregated for the first time.|
|recent|[microsoft.graph.tenantGovernanceServices.billingMetricsRecent](../resources/tenantgovernanceservices-billingmetricsrecent.md)|Billing metrics correpsionding to recent snapshots where metrics were found to have sufficiently changed.|

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.billingMetrics"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.billingMetrics",
  "initial": {"@odata.type": "microsoft.graph.tenantGovernanceServices.billingMetricsInitial"},
  "recent": {"@odata.type": "microsoft.graph.tenantGovernanceServices.billingMetricsRecent"}
}
```

