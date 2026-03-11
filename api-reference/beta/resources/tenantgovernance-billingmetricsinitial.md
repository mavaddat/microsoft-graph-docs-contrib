---
title: "billingMetricsInitial resource type"
description: "Represents the initial snapshot of billing metrics when the relationship was first discovered."
author: "akhil-potturi"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# billingMetricsInitial resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents the initial snapshot of billing metrics captured when the relationship was first discovered, establishing a baseline for billing account associations and associated tenant connection counts.

## Properties
|Property|Type|Description|
|:---|:---|:---|
|createdDateTime|DateTimeOffset|Timestamp which represents when billing metrics are initially aggregated for the related tenant.|
|watermarkDateTime|DateTimeOffset|Timestamp which represents the earliest segment of data missing within the aggregation window. When no data is missing, this value will be within one day of the associated createdDateTime property.|
|localAssociatedTenantCount|Decimal|Count of shared billing accounts where the calling tenant is the primary billing tenant and the related tenant is the associated billing tenant.|
|localAssociatedTenantBillingManagementActiveCount|Decimal|Count of shared billing accounts where the calling tenant is the primary billing tenant and the related tenant is the associated billing tenant with Billing Management is active.|
|localAssociatedTenantProvisioningActiveCount|Decimal|Count of shared billing accounts where the calling tenant is the primary billing tenant and the related tenant is the associated billing tenant with Provisioning is active.|
|localAssociatedTenantIds|String collection|Collection of associated billing tenant IDs corresponding to localAssociatedTenants.|
|foreignAssociatedTenantCount|Decimal|Count of shared billing accounts where the calling tenant is the associated billing tenant and the related tenant is the primary billing tenant.|
|foreignAssociatedTenantBillingManagementActiveCount|Decimal|Count of shared billing accounts where the calling tenant is the associated billing tenant and the related tenant is the primary billing tenant with Billing Management is active.|
|foreignAssociatedTenantProvisioningActiveCount|Decimal|Count of shared billing accounts where the calling tenant is the associated billing tenant and the related tenant is the primary billing tenant with Provisioning is active.|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.billingMetricsInitial"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.billingMetricsInitial",
  "createdDateTime": "String (timestamp)",
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
```

