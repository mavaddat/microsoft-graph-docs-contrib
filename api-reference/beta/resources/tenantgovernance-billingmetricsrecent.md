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
|updateDateTime|DateTimeOffset|Timestamp which represents when billing metrics are aggregated and found to have sufficiently changed for the related tenant.|
|watermarkDateTime|DateTimeOffset|Timestamp which represents the earliest segment of data missing within the aggregation window. When no data is missing, this value will be within one day of the associated updateDateTime property.|
|localAssociatedTenantCount|Int64|Count of shared billing accounts where the calling tenant is the primary billing tenant and the related tenant is the associated billing tenant.|
|localAssociatedTenantBillingManagementActiveCount|Int64|Count of shared billing accounts where the calling tenant is the primary billing tenant and the related tenant is the associated billing tenant with Billing Management is active.|
|localAssociatedTenantProvisioningActiveCount|Int64|Count of shared billing accounts where the calling tenant is the primary billing tenant and the related tenant is the associated billing tenant with Provisioning is active.|
|localAssociatedTenantIds|String collection|Collection of associated billing tenant IDs corresponding to localAssociatedTenants.|
|foreignAssociatedTenantCount|Int64|Count of shared billing accounts where the calling tenant is the associated billing tenant and the related tenant is the primary billing tenant.|
|foreignAssociatedTenantBillingManagementActiveCount|Int64|Count of shared billing accounts where the calling tenant is the associated billing tenant and the related tenant is the primary billing tenant with Billing Management is active.|
|foreignAssociatedTenantProvisioningActiveCount|Int64|Count of shared billing accounts where the calling tenant is the associated billing tenant and the related tenant is the primary billing tenant with Provisioning is active.|

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
  "localAssociatedTenantCount": "Int64",
  "localAssociatedTenantBillingManagementActiveCount": "Int64",
  "localAssociatedTenantProvisioningActiveCount": "Int64",
  "localAssociatedTenantIds": [
    "String"
  ],
  "foreignAssociatedTenantCount": "Int64",
  "foreignAssociatedTenantBillingManagementActiveCount": "Int64",
  "foreignAssociatedTenantProvisioningActiveCount": "Int64"
}
{
  "localAssociatedTenantIds": [
    "String"
  ],
  "foreignAssociatedTenantCount": "Int64",
  "foreignAssociatedTenantBillingManagementActiveCount": "Int64",
  "foreignAssociatedTenantProvisioningActiveCount": "Int64",
  "updateDateTime": "String (timestamp)"
}
```

