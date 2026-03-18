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

Inherits from [microsoft.graph.entity](../resources/entity.md).

## Properties

| Property | Type | Description |
|:---------|:-----|:------------|
| foreignAssociatedTenantBillingManagementActiveCount | Decimal | The number of foreign associated tenants with active billing management. |
| foreignAssociatedTenantCount | Decimal | The total number of foreign associated tenants. |
| foreignAssociatedTenantProvisioningActiveCount | Decimal | The number of foreign associated tenants with active provisioning. |
| id | String | Unique identifier for the metrics snapshot. Inherited from [microsoft.graph.entity](../resources/entity.md). |
| localAssociatedTenantBillingManagementActiveCount | Decimal | The number of local associated tenants with active billing management. |
| localAssociatedTenantCount | Decimal | The total number of local associated tenants. |
| localAssociatedTenantIds | Collection(String) | The list of local associated tenant IDs. |
| localAssociatedTenantProvisioningActiveCount | Decimal | The number of local associated tenants with active provisioning. |
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

> [!NOTE]
> This abstract type is not returned in API responses. See concrete implementations.

<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.billingMetricsBase",
  "baseType": "microsoft.graph.entity",
  "openType": false
}
-->
```json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.billingMetricsBase",
  "id": "String (identifier)",
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
