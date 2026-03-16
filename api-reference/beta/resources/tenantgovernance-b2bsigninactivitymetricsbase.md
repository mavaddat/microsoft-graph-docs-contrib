---
title: "b2BSignInActivityMetricsBase resource type"
description: "Abstract base type for B2B sign-in activity metrics."
author: "akhil-potturi"
ms.date: 03/16/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# b2BSignInActivityMetricsBase resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

> [!IMPORTANT]
> This is an abstract base type and does not appear directly in API responses. Use the concrete types [b2BSignInActivityMetricsInitial](tenantgovernance-b2bsigninactivitymetricsinitial.md) or [b2BSignInActivityMetricsRecent](tenantgovernance-b2bsigninactivitymetricsrecent.md).

Abstract base type that defines common properties for B2B sign-in activity metrics.

## Properties

| Property | Type | Description |
|:---------|:-----|:------------|
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. |
| inboundMonthlyTotalUsers | Decimal | The total number of unique inbound users with sign-in activity in the last month. |
| inboundMonthlyTotalApplications | Decimal | The total number of applications accessed by inbound users in the last month. |
| outboundMonthlyTotalUsers | Decimal | The total number of unique outbound users with sign-in activity in the last month. |
| outboundMonthlyTotalApplications | Decimal | The total number of applications accessed by outbound users in the last month. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

> [!NOTE]
> This abstract type is not returned in API responses. See concrete implementations.

<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.b2BSignInActivityMetricsBase"
}
-->
```json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.b2BSignInActivityMetricsBase",
  "watermarkDateTime": "String (timestamp)",
  "inboundMonthlyTotalUsers": "Decimal",
  "inboundMonthlyTotalApplications": "Decimal",
  "outboundMonthlyTotalUsers": "Decimal",
  "outboundMonthlyTotalApplications": "Decimal"
}
```
