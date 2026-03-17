---
title: "billingMetricsBase resource type"
description: "Abstract base type for billing metrics."
author: "akhil-potturi"
ms.date: 03/16/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# billingMetricsBase resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

> [!IMPORTANT]
> This is an abstract base type and does not appear directly in API responses. Use the concrete types [billingMetricsInitial](tenantgovernanceservices-billingmetricsinitial.md) or [billingMetricsRecent](tenantgovernanceservices-billingmetricsrecent.md).

Abstract base type that defines common properties for billing metrics.

## Properties

| Property | Type | Description |
|:---------|:-----|:------------|
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. |
| localAssociatedTenantCount | Int64 | The total number of local associated tenants. |
| localAssociatedTenantBillingManagementActiveCount | Int64 | The number of local associated tenants with active billing management. |
| localAssociatedTenantProvisioningActiveCount | Int64 | The number of local associated tenants with active provisioning. |
| localAssociatedTenantIds | Collection(String) | The list of local associated tenant IDs. |
| foreignAssociatedTenantCount | Int64 | The total number of foreign associated tenants. |
| foreignAssociatedTenantBillingManagementActiveCount | Int64 | The number of foreign associated tenants with active billing management. |
| foreignAssociatedTenantProvisioningActiveCount | Int64 | The number of foreign associated tenants with active provisioning. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

> [!NOTE]
> This abstract type is not returned in API responses. See concrete implementations.

<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.billingMetricsBase"
}
-->
```json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.billingMetricsBase",
  "watermarkDateTime": "String (timestamp)",
  "localAssociatedTenantCount": "Int64",
  "localAssociatedTenantBillingManagementActiveCount": "Int64",
  "localAssociatedTenantProvisioningActiveCount": "Int64",
  "localAssociatedTenantIds": ["String"],
  "foreignAssociatedTenantCount": "Int64",
  "foreignAssociatedTenantBillingManagementActiveCount": "Int64",
  "foreignAssociatedTenantProvisioningActiveCount": "Int64"
}
```
