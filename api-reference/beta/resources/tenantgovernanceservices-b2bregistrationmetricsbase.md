---
title: "b2BRegistrationMetricsBase resource type"
description: "Abstract base type for B2B registration metrics."
author: "akhil-potturi"
ms.date: 03/16/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# b2BRegistrationMetricsBase resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

> [!IMPORTANT]
> This is an abstract base type and does not appear directly in API responses. Use the concrete types [b2BRegistrationMetricsInitial](tenantenantgovernanceservicestgovernance-b2bregistrationmetricsinitial.md) or [b2BRegistrationMetricsRecent](tenantgovernanceservices-b2bregistrationmetricsrecent.md).

Abstract base type that defines common properties for B2B registration metrics snapshots.

## Properties

| Property | Type | Description |
|:---------|:-----|:------------|
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. |
| inboundTotalUsers | Decimal | The total number of inbound B2B guest users registered. |
| outboundTotalUsers | Decimal | The total number of outbound B2B users from this tenant registered in other tenants. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

> [!NOTE]
> This abstract type is not returned in API responses. See concrete implementations.

<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.b2BRegistrationMetricsBase"
}
-->
```json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.b2BRegistrationMetricsBase",
  "watermarkDateTime": "String (timestamp)",
  "inboundTotalUsers": "Decimal",
  "outboundTotalUsers": "Decimal"
}
```
