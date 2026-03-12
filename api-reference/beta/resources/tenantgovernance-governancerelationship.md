---
title: "governanceRelationship resource type"
description: "Represents an established governance relationship between a governing tenant and a governed tenant."
author: "hafowler"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# governanceRelationship resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents an established governance relationship between a governing tenant and a governed tenant. A governance relationship is created when a [governanceRequest](tenantgovernance-governancerequest.md) is accepted by the governed tenant.


Inherits from [microsoft.graph.entity](../resources/entity.md).


## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[List](../api/tenantgovernance-list-governancerelationships.md)|[microsoft.graph.tenantGovernanceServices.governanceRelationship](../resources/tenantgovernance-governancerelationship.md) collection|Get a list of the [governanceRelationship](../resources/tenantgovernance-governancerelationship.md) objects and their properties.|
|[Get](../api/tenantgovernance-governancerelationship-get.md)|[microsoft.graph.tenantGovernanceServices.governanceRelationship](../resources/tenantgovernance-governancerelationship.md)|Read the properties of a [governanceRelationship](../resources/tenantgovernance-governancerelationship.md) object.|
|[Update](../api/tenantgovernance-governancerelationship-update.md)|[microsoft.graph.tenantGovernanceServices.governanceRelationship](../resources/tenantgovernance-governancerelationship.md)|Update the **status** property to initiate termination of the governance relationship.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|createdType|microsoft.graph.tenantGovernanceServices.relationshipCreationType|Indicates how the relationship was created. The possible values are: `approvedByAdmin`, `addOnTenant`, `unknownFutureValue`.|
|creationDateTime|DateTimeOffset|The date and time when the relationship was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2026 is `2026-01-01T00:00:00Z`.|
|governedTenantId|String|The Microsoft Entra tenant ID of the governed tenant.|
|governedTenantName|String|The display name of the governed tenant.|
|governingTenantId|String|The Microsoft Entra tenant ID of the governing tenant.|
|governingTenantName|String|The display name of the governing tenant.|
|id|String|The unique identifier for the governance relationship. Inherited from [entity](../resources/entity.md).|
|policySnapshot|[microsoft.graph.tenantGovernanceServices.relationshipPolicy](../resources/tenantgovernance-relationshippolicy.md)|A snapshot of the governance policy applied to this relationship, including delegated administration role assignments and multi-tenant applications to provision.|
|status|microsoft.graph.tenantGovernanceServices.relationshipStatus|The current status of the governance relationship. The possible values are: `active`, `terminated`, `terminationRequestedByGoverningTenant`, `unknownFutureValue`.|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.governanceRelationship",
  "baseType": "microsoft.graph.entity",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.governanceRelationship",
  "id": "String (identifier)",
  "governingTenantId": "String",
  "governingTenantName": "String",
  "governedTenantId": "String",
  "governedTenantName": "String",
  "status": "String",
  "policySnapshot": {
    "@odata.type": "microsoft.graph.tenantGovernanceServices.relationshipPolicy"
  },
  "createdType": "String",
  "creationDateTime": "String (timestamp)"
}
```

