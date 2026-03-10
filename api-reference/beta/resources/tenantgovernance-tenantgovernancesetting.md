---
title: "tenantGovernanceSetting resource type"
description: "Represents the tenant governance settings that control related tenant discovery and invitation capabilities."
author: "hafowler"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# tenantGovernanceSetting resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents the tenant governance settings that control related tenant discovery and invitation capabilities. This is a singleton resource.


Inherits from [microsoft.graph.entity](../resources/entity.md).


## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[Get](../api/tenantgovernance-tenantgovernancesetting-get.md)|[microsoft.graph.tenantGovernanceServices.tenantGovernanceSetting](../resources/tenantgovernance-tenantgovernancesetting.md)|Read the properties of the [tenantGovernanceSetting](../resources/tenantgovernance-tenantgovernancesetting.md) singleton.|
|[Update](../api/tenantgovernance-tenantgovernancesetting-update.md)|[microsoft.graph.tenantGovernanceServices.tenantGovernanceSetting](../resources/tenantgovernance-tenantgovernancesetting.md)|Update the **canReceiveInvitations** property of the tenant governance settings.|
|[enableRelatedTenants](../api/tenantgovernance-tenantgovernancesetting-enablerelatedtenants.md)|None|Enable the related tenants feature for tenant discovery.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|canReceiveInvitations|Boolean|Indicates whether the tenant can receive governance invitations. When set to `false`, the tenant cannot receive new governance invitations. When set to `true`, other tenants can send your tenant invitations by providing your tenant id or domain name. This setting is disabled by default.|
|id|String|The unique identifier for the tenant governance setting. Inherited from [entity](../resources/entity.md).|
|isRelatedTenantsEnabled|Boolean|Indicates whether the related tenants feature is enabled for tenant discovery. When set to `false`, related tenant APIs don't work. This property can be enabled by calling the [enableRelatedTenants](../api/tenantgovernance-tenantgovernancesetting-enablerelatedtenants.md) action.|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.tenantGovernanceSetting",
  "baseType": "microsoft.graph.entity",
  "openType": "id"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.tenantGovernanceSetting",
  "id": "String (identifier)",
  "isRelatedTenantsEnabled": "Boolean",
  "canReceiveInvitations": "Boolean"
}
```

