---
title: "Create snapshot"
description: "Create a new snapshot object."
author: "mapamu"
ms.date: 03/04/2026
ms.localizationpriority: medium
ms.subservice: "RecoveryServices"
doc_type: apiPageType
---

# Create snapshot

Namespace: microsoft.graph.entraRecoveryServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Create a new snapshot object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "entrarecoveryservices-recovery-post-snapshots-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/entrarecoveryservices-recovery-post-snapshots-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /directory/recovery/snapshots
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.entraRecoveryServices.snapshot](../resources/entrarecoveryservices-snapshot.md) object.

You can specify the following properties when creating a **snapshot**.

|Property|Type|Description|
|:---|:---|:---|
|createdDateTime|DateTimeOffset|Required.|
|totalChangedObjects|Int32|Optional.|



## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.entraRecoveryServices.snapshot](../resources/entrarecoveryservices-snapshot.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "create_snapshot_from_"
}
-->
``` http
POST https://graph.microsoft.com/beta/directory/recovery/snapshots
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
  "truncated": true,
  "@odata.type": "microsoft.graph.entraRecoveryServices.snapshot"
}
-->
``` http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.snapshot",
  "id": "c5e10147-16d9-fb65-ef1d-034c0b696f9e",
  "createdDateTime": "String (timestamp)",
  "totalChangedObjects": "Integer"
}
```

