---
title: "billingMetricsRecent resource type"
description: "Represents the most recent snapshot of billing metrics."
author: "akhil-potturi"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# billingMetricsRecent resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents the most recent snapshot of billing metrics, showing current billing account associations and associated tenant connection counts with corrected property names (management instead of managment).

## Properties
|Property|Type|Description|
|:---|:---|:---|
|foreignAssociatedTenantBillingManagementActiveCount|Decimal|**TODO: Add Description**|
|foreignAssociatedTenantCount|Decimal|**TODO: Add Description**|
|foreignAssociatedTenantProvisioningActiveCount|Decimal|**TODO: Add Description**|
|localAssociatedTenantBillingManagementActiveCount|Decimal|**TODO: Add Description**|
|localAssociatedTenantCount|Decimal|**TODO: Add Description**|
|localAssociatedTenantIds|String collection|**TODO: Add Description**|
|localAssociatedTenantProvisioningActiveCount|Decimal|**TODO: Add Description**|
|updateDateTime|DateTimeOffset|**TODO: Add Description**|
|watermarkDateTime|DateTimeOffset|**TODO: Add Description**|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.billingMetricsRecent"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.billingMetricsRecent",
  "updateDateTime": "String (timestamp)",
  "watermarkDateTime": "String (timestamp)",
  "localAssociatedTenantCount": "Decimal",
  "localAssociatedTenantBillingManagementActiveCount": "Decimal",
  "localAssociatedTenantProvisioningActiveCount": "Decimal",
  "localAssociatedTenantIds": [
    "String"
  ],
  "foreignAssociatedTenantCount": "Decimal",
  "foreignAssociatedTenantBillingManagementActiveCount": "Decimal",
  "foreignAssociatedTenantProvisioningActiveCount": "Decimal"
}
  "localAssociatedTenantIds": [
    "String"
  ],
  "foreignAssociatedTenantCount": "Decimal",
  "foreignAssociatedTenantBillingManagementActiveCount": "Decimal",
  "foreignAssociatedTenantProvisioningActiveCount": "Decimal",
  "updateDateTime": "String (timestamp)"
}
```

