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
| localAssociatedTenantCount | Decimal | The total number of local associated tenants. |
| localAssociatedTenantBillingManagementActiveCount | Decimal | The number of local associated tenants with active billing management. |
| localAssociatedTenantProvisioningActiveCount | Decimal | The number of local associated tenants with active provisioning. |
| localAssociatedTenantIds | Collection(String) | The list of local associated tenant IDs. |
| foreignAssociatedTenantCount | Decimal | The total number of foreign associated tenants. |
| foreignAssociatedTenantBillingManagementActiveCount | Decimal | The number of foreign associated tenants with active billing management. |
| foreignAssociatedTenantProvisioningActiveCount | Decimal | The number of foreign associated tenants with active provisioning. |

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
  "localAssociatedTenantCount": "Decimal",
  "localAssociatedTenantBillingManagementActiveCount": "Decimal",
  "localAssociatedTenantProvisioningActiveCount": "Decimal",
  "localAssociatedTenantIds": ["String"],
  "foreignAssociatedTenantCount": "Decimal",
  "foreignAssociatedTenantBillingManagementActiveCount": "Decimal",
  "foreignAssociatedTenantProvisioningActiveCount": "Decimal"
}
```
