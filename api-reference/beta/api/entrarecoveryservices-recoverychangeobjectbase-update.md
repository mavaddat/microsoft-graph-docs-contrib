---
title: "Update recoveryChangeObjectBase"
description: "Update the properties of a recoveryChangeObjectBase object."
author: "mapamu"
ms.date: 03/04/2026
ms.localizationpriority: medium
ms.subservice: "RecoveryServices"
doc_type: apiPageType
---

# Update recoveryChangeObjectBase

Namespace: microsoft.graph.entraRecoveryServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Update the properties of a recoveryChangeObjectBase object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "entrarecoveryservices-recoverychangeobjectbase-update-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/entrarecoveryservices-recoverychangeobjectbase-update-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
PATCH /recoveryChangeObjectBase
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

[!INCLUDE [table-intro](../../includes/update-property-table-intro.md)]


|Property|Type|Description|
|:---|:---|:---|
|entityTypeName|microsoft.graph.entraRecoveryServices.resourceTypeName|The possible values are: `user`, `group`, `conditionalAccessPolicy`, `namedLocationPolicy`, `authenticationMethodPolicy`, `authorizationPolicy`, `authenticationStrengthPolicy`, `application`, `servicePrincipal`, `unknownFutureValue`, `oAuth2PermissionGrant`, `appRoleAssignment`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `oAuth2PermissionGrant` , `appRoleAssignment`. Required.|
|displayName|String|Optional.|
|recoveryAction|microsoft.graph.entraRecoveryServices.recoveryAction|The possible values are: `softDelete`, `update`, `restore`, `unknownFutureValue`. Required.|
|failureMessage|String|Optional.|



## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase](../resources/entrarecoveryservices-recoverychangeobjectbase.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "update_recoverychangeobjectbase"
}
-->
``` http
PATCH https://graph.microsoft.com/beta/recoveryChangeObjectBase
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase",
  "entityTypeName": "String",
  "displayName": "String",
  "recoveryAction": "String",
  "failureMessage": "String"
}
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase",
  "id": "59c78403-4467-25a1-1d84-3a921cdd4523",
  "entityTypeName": "String",
  "displayName": "String",
  "recoveryAction": "String",
  "failureMessage": "String"
}
```

