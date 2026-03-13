---
title: "recoveryChangeObjectBase resource type"
description: "Represents a single object change in the context of tenant recovery."
author: "mapamu"
ms.date: 03/04/2026
ms.localizationpriority: medium
ms.subservice: "entra-id"
doc_type: resourcePageType
---

# recoveryChangeObjectBase resource type

Namespace: microsoft.graph.entraRecoveryServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents a single object change in the context of tenant recovery. Returned by the `getChanges` function on preview jobs and `getFailedChanges` function on recovery jobs. Each instance describes the entity being modified, the type of recovery action to be performed, and the delta between the current and target states.

Inherits from [microsoft.graph.entity](../resources/entity.md).

This resource is an open type that supports additional dynamic properties `deltaFromCurrent` and `currentState` in responses.

## Methods
None.

## Properties
|Property|Type|Description|
|:---|:---|:---|
|displayName|String|The display name of the changed object in its current state, used to uniquely identify the object.|
|entityTypeName|[microsoft.graph.entraRecoveryServices.resourceTypeName](../resources/enums-entrarecoveryservices.md)|The type of directory entity being modified. The possible values are: `user`, `group`, `conditionalAccessPolicy`, `namedLocationPolicy`, `authenticationMethodPolicy`, `authorizationPolicy`, `authenticationStrengthPolicy`, `application`, `servicePrincipal`, `unknownFutureValue`, `oAuth2PermissionGrant`, `appRoleAssignment`. You must use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `oAuth2PermissionGrant`, `appRoleAssignment`.|
|failureMessage|String|The error message if the change failed to apply. Only populated in `getFailedChanges` responses. Null otherwise.|
|id|String|The unique identifier of the changed object. Inherited from [entity](../resources/entity.md).|
|recoveryAction|[microsoft.graph.entraRecoveryServices.recoveryAction](../resources/enums-entrarecoveryservices.md)|The type of recovery action to be performed on this object. The possible values are: `softDelete`, `update`, `restore`, `unknownFutureValue`.|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase",
  "baseType": "microsoft.graph.entity",
  "openType": true
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase",
  "id": "String (identifier)",
  "entityTypeName": "String",
  "displayName": "String",
  "recoveryAction": "String",
  "failureMessage": "String"
}
```
