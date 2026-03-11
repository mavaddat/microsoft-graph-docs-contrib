---
title: "Update snapshot"
description: "Update the properties of a snapshot object."
author: "mapamu"
ms.date: 03/04/2026
ms.localizationpriority: medium
ms.subservice: "entra-id"
doc_type: apiPageType
---

# Update snapshot

Namespace: microsoft.graph.entraRecoveryServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Update the properties of a snapshot object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "entrarecoveryservices-snapshot-update-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/entrarecoveryservices-snapshot-update-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
PATCH /directory/recovery/snapshots/{snapshotId}
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
|createdDateTime|DateTimeOffset|Required.|
|totalChangedObjects|Int32|Optional.|



## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.entraRecoveryServices.snapshot](../resources/entrarecoveryservices-snapshot.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "update_snapshot"
}
-->
``` http
PATCH https://graph.microsoft.com/beta/directory/recovery/snapshots/{snapshotId}
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.snapshot",
  "totalChangedObjects": "Integer"
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
  "@odata.type": "#microsoft.graph.entraRecoveryServices.snapshot",
  "id": "c5e10147-16d9-fb65-ef1d-034c0b696f9e",
  "createdDateTime": "String (timestamp)",
  "totalChangedObjects": "Integer"
}
```

