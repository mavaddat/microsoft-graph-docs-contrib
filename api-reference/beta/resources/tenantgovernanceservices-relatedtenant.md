---
title: "relatedTenant resource type"
description: "Represents a tenant that has a relationship with the calling tenant, including B2B collaboration, application usage, and billing connections."
author: "akhil-potturi"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# relatedTenant resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents a tenant that has a relationship with the calling tenant. Related tenants are discovered based on various connection types including B2B collaboration (guest users), B2B sign-in activity, multi-tenant application usage, and billing account associations. This resource provides metrics about the nature and strength of the relationship between the two tenants.


Inherits from [microsoft.graph.entity](../resources/entity.md).


## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[List](../api/tenantgovernanceservices-list-relatedtenants.md)|[microsoft.graph.tenantGovernanceServices.relatedTenant](../resources/tenantgovernanceservices-relatedtenant.md) collection|Get a list of related tenants with their relationship metrics.|
|[Get](../api/tenantgovernanceservices-relatedtenant-get.md)|[microsoft.graph.tenantGovernanceServices.relatedTenant](../resources/tenantgovernanceservices-relatedtenant.md)|Read the properties and metrics of a specific related tenant.|
|[refresh](../api/tenantgovernanceservices-relatedtenant-refresh.md)|None|Trigger an ad-hoc refresh of related tenants data outside the regular refresh schedule.|
|[refreshStatus](../api/tenantgovernanceservices-relatedtenant-refreshstatus.md)|[microsoft.graph.tenantGovernanceServices.relatedTenantsRefreshStatus](../resources/tenantgovernanceservices-relatedtenantsrefreshstatus.md)|Get the status of a related tenants refresh operation.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|createdDateTime|DateTimeOffset|Timestamp of when the RelatedTenant was created. The value can't be modified and is automatically populated when the RelatedTenant is created.|
|id|String|Unique identifier for the related tenant. Inherited from [microsoft.graph.entity](../resources/entity.md).|

## Relationships
|Relationship|Type|Description|
|:---|:---|:---|
|appB2BSignInActivityMetrics|[microsoft.graph.tenantGovernanceServices.b2BSignInActivityMetrics](../resources/tenantgovernanceservices-b2bsigninactivitymetrics.md)|Represents aggregated data related to B2B sign-ins to specific administrative applications in the Entra ecosystem. Admin apps included: Azure Portal, Exchange Admin Center, Windows Admin Center, SharePoint Tenant Admin Center, Microsoft Teams Admin Portal Service, Microsoft 365 Admin Portal, Microsoft Office 365 Portal.|
|b2BRegistrationMetrics|[microsoft.graph.tenantGovernanceServices.b2bRegistrationMetrics](../resources/tenantgovernanceservices-b2bregistrationmetrics.md)|Represents aggregated data related to B2B collaboration guest/external users between tenants. Scope of data includes invited and accepted guest users via B2B registration; does not include data from B2B direct connect.|
|b2BSignInActivityMetrics|[microsoft.graph.tenantGovernanceServices.b2BSignInActivityMetrics](../resources/tenantgovernanceservices-b2bsigninactivitymetrics.md)|Represents aggregated data related to B2B sign-ins between tenants across all applications in the Entra ecosystem. Scope of data considers sign-ins from last 30 days since tenant discovery is initiated.|
|billingMetrics|[microsoft.graph.tenantGovernanceServices.billingMetrics](../resources/tenantgovernanceservices-billingmetrics.md)|Represents aggregated data related to shared billing accounts between the calling and related tenant based on the associated billing tenant construct.|
|multiTenantApplicationMetrics|[microsoft.graph.tenantGovernanceServices.multiTenantApplicationMetrics](../resources/tenantgovernanceservices-multitenantapplicationmetrics.md)|Represents aggregated data related to multi-tenant application relations between the calling and related tenant.|

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.relatedTenant",
  "baseType": "microsoft.graph.entity",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.relatedTenant",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)"
}
```

