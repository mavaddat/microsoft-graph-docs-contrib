---
title: "Update recovery"
description: "Update the properties of a recovery object."
author: "mapamu"
ms.date: 03/04/2026
ms.localizationpriority: medium
ms.subservice: "RecoveryServices"
doc_type: apiPageType
---

# Update recovery

Namespace: microsoft.graph.entraRecoveryServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Update the properties of a recovery object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "entrarecoveryservices-recovery-update-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/entrarecoveryservices-recovery-update-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
PATCH /directory/recovery
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



## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.entraRecoveryServices.recovery](../resources/entrarecoveryservices-recovery.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "update_recovery"
}
-->
``` http
PATCH https://graph.microsoft.com/beta/directory/recovery
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.recovery"
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
  "@odata.type": "#microsoft.graph.entraRecoveryServices.recovery",
  "id": "f1a6d5cd-dfa1-a1a3-fbcb-fdcc6f3e1677"
}
```

