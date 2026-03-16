---
title: "multiTenantApplicationMetricsBase resource type"
description: "Abstract base type for multi-tenant application metrics."
author: "akhil-potturi"
ms.date: 03/16/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# multiTenantApplicationMetricsBase resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

> [!IMPORTANT]
> This is an abstract base type and does not appear directly in API responses. Use the concrete types [multiTenantApplicationMetricsInitial](tenantgovernance-multitenantapplicationmetricsinitial.md) or [multiTenantApplicationMetricsRecent](tenantgovernance-multitenantapplicationmetricsrecent.md).

Abstract base type that defines common properties for multi-tenant application metrics.

## Properties

| Property | Type | Description |
|:---------|:-----|:------------|
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. |
| inboundMonthlyTotalApplications | Decimal | The total number of inbound multi-tenant applications in the last month. |
| outboundMonthlyTotalApplications | Decimal | The total number of outbound multi-tenant applications in the last month. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

> [!NOTE]
> This abstract type is not returned in API responses. See concrete implementations.

<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.multiTenantApplicationMetricsBase"
}
-->
```json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.multiTenantApplicationMetricsBase",
  "watermarkDateTime": "String (timestamp)",
  "inboundMonthlyTotalApplications": "Decimal",
  "outboundMonthlyTotalApplications": "Decimal"
}
```
