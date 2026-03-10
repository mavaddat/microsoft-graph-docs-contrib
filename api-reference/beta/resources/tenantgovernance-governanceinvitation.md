---
title: "governanceInvitation resource type"
description: "Represents an invitation sent by a governing tenant to establish a governance relationship with a governed tenant."
author: "hafowler"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# governanceInvitation resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents an invitation sent by a future governed tenant to establish a governance relationship with a future governing tenant. 


Inherits from [microsoft.graph.entity](../resources/entity.md).


## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[List](../api/tenantgovernance-list-governanceinvitations.md)|[microsoft.graph.tenantGovernanceServices.governanceInvitation](../resources/tenantgovernance-governanceinvitation.md) collection|Get a list of the [governanceInvitation](../resources/tenantgovernance-governanceinvitation.md) objects and their properties.|
|[Create](../api/tenantgovernance-post-governanceinvitations.md)|[microsoft.graph.tenantGovernanceServices.governanceInvitation](../resources/tenantgovernance-governanceinvitation.md)|Create a new governance invitation.|
|[Get](../api/tenantgovernance-governanceinvitation-get.md)|[microsoft.graph.tenantGovernanceServices.governanceInvitation](../resources/tenantgovernance-governanceinvitation.md)|Read the properties of a [governanceInvitation](../resources/tenantgovernance-governanceinvitation.md) object.|
|[Delete](../api/tenantgovernance-governanceinvitation-delete.md)|None|Delete a governance invitation.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|createdDateTime|DateTimeOffset|The date and time when the invitation was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC.|
|expirationDateTime|DateTimeOffset|The date and time when the invitation expires. The timestamp type represents date and time information using ISO 8601 format and is always in UTC.|
|governedTenantId|String|The Microsoft Entra tenant ID of the governed tenant.|
|governedTenantName|String|The display name of the governed tenant.|
|governingTenantId|String|The Microsoft Entra tenant ID of the governing tenant.|
|governingTenantName|String|The display name of the governing tenant.|
|id|String|The unique identifier for the governance invitation. Inherited from [entity](../resources/entity.md)|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.governanceInvitation",
  "baseType": "microsoft.graph.entity",
  "openType": "id"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.governanceInvitation",
  "id": "String (identifier)",
  "governingTenantId": "String",
  "governedTenantId": "String",
  "governingTenantName": "String",
  "governedTenantName": "String",
  "createdDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)"
}
```

