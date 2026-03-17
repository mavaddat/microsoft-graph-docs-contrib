---
title: "governanceRequest resource type"
description: "Represents a request from a governing tenant to establish a governance relationship with a governed tenant."
author: "hafowler"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# governanceRequest resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents a request from a governing tenant to establish a governance relationship with a governed tenant. The governed tenant can accept or reject the request. When accepted, a [governanceRelationship](tenantgovernanceservices-governancerelationship.md) is created.


Inherits from [microsoft.graph.entity](../resources/entity.md).


## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[List](../api/tenantgovernanceservices-list-governancerequests.md)|[microsoft.graph.tenantGovernanceServices.governanceRequest](../resources/tenantgovernanceservices-governancerequest.md) collection|Get a list of the [governanceRequest](../resources/tenantgovernanceservices-governancerequest.md) objects and their properties.|
|[Create](../api/tenantgovernanceservices-post-governancerequests.md)|[microsoft.graph.tenantGovernanceServices.governanceRequest](../resources/tenantgovernanceservices-governancerequest.md)|Create a new governance request to establish a relationship with a governed tenant.|
|[Get](../api/tenantgovernanceservices-governancerequest-get.md)|[microsoft.graph.tenantGovernanceServices.governanceRequest](../resources/tenantgovernanceservices-governancerequest.md)|Read the properties of a [governanceRequest](../resources/tenantgovernanceservices-governancerequest.md) object.|
|[Update](../api/tenantgovernanceservices-governancerequest-update.md)|[microsoft.graph.tenantGovernanceServices.governanceRequest](../resources/tenantgovernanceservices-governancerequest.md)|Update the **status** property to accept or reject the governance request.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|expirationDateTime|DateTimeOffset|The date and time when the request expires if not accepted or rejected. The timestamp type represents date and time information using ISO 8601 format and is always in UTC.|
|governedTenantId|String|The Microsoft Entra tenant ID of the governed tenant.|
|governedTenantName|String|The display name of the governed tenant.|
|governingTenantId|String|The Microsoft Entra tenant ID of the governing tenant.|
|governingTenantName|String|The display name of the governing tenant.|
|id|String|The unique identifier for the governance request. Inherited from [entity](../resources/entity.md).|
|policySnapshot|[microsoft.graph.tenantGovernanceServices.relationshipPolicy](../resources/tenantgovernanceservices-relationshippolicy.md)|A snapshot of the governance policy to be applied if the request is accepted, including delegated administration role assignments and multi-tenant applications to provision.|
|requestDateTime|DateTimeOffset|The date and time when the request was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC.|
|status|microsoft.graph.tenantGovernanceServices.requestStatus|The current status of the governance request. The possible values are: `pending`, `accepted`, `rejected`, `unknownFutureValue`.|

## Relationships
|Relationship|Type|Description|
|:---|:---|:---|
|governancePolicyTemplate|[microsoft.graph.tenantGovernanceServices.governancePolicyTemplate](../resources/tenantgovernanceservices-governancepolicytemplate.md)|The governance policy template associated with this request.|

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.governanceRequest",
  "baseType": "microsoft.graph.entity",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.governanceRequest",
  "id": "String (identifier)",
  "governingTenantId": "String",
  "governingTenantName": "String",
  "governedTenantId": "String",
  "governedTenantName": "String",
  "expirationDateTime": "String (timestamp)",
  "requestDateTime": "String (timestamp)",
  "status": "String",
  "policySnapshot": {
    "@odata.type": "microsoft.graph.tenantGovernanceServices.relationshipPolicy"
  }
}
```

