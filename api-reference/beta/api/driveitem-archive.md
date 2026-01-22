---
title: "driveItem: archive"
description: "Archive a drive item."
author: "dcun55"
ms.date: 01/20/2026
ms.localizationpriority: medium
ms.subservice: "sharepoint"
doc_type: apiPageType
---

# driveItem: archive

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Archives a [DriveItem](../resources/driveitem.md).

**File Archive**: Archives a single active file using a synchronous request. The file is archived immediately.

_Note_: File DriveItem Archive is not supported when the request includes the Prefer: respond-async header.

**Folder Archive**: Archives all active files within a folder using an asynchronous request. The operation is initiated asynchronously, and a [monitor URL](/graph/long-running-actions-overview) is returned in the response to allow clients to track the progress of the archive operation.

Use the [monitor URL](/graph/long-running-actions-overview) to track progress until the operation completes.

_Note_: Folder DriveItem Archive is supported only when the request includes the Prefer: respond-async header

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "driveitem-archive-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/driveitem-archive-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /drive/root/archive
POST /drives/{drivesId}/root/archive
POST /shares/{sharesId}/root/archive
POST /drive/items/{driveItemId}/archive
POST /shares/{sharesId}/driveItem/archive
POST /drive/bundles/{driveItemId}/archive
POST /drive/special/{driveItemId}/archive
POST /drive/following/{driveItemId}/archive
```

## Request headers

| Name          | Description                                                                                               |
|:--------------|:----------------------------------------------------------------------------------------------------------|
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts). |
| Prefer        | respond-async. Indicates that the request is an async request. Optional.                                  |

## Request body

Don't supply a request body for this method.

## Response

If successful, this action returns a `204 No Content` response code for file [DriveItem](../resources/driveitem.md).

Otherwise, if successful, this action returns a `202 Accepted` response code, with a monitor URI, is returned for folder [DriveItem](../resources/driveitem.md).

## Examples

### File Archive Example

For file archive operation on the [DriveItem](../resources/driveitem.md), the request completes synchronously and returns `204 No Content`

#### File Archive Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "driveitemthis.archive"
}
-->
``` http
POST https://graph.microsoft.com/beta/drive/root/archive
```

#### File Archive Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true
}
-->
``` http
HTTP/1.1 204 No Content
```

### Folder Archive Example

For folder archive operation on the [DriveItem](../resources/driveitem.md), the request completes asynchronously and returns `202 Accepted` with a [monitor URL](/graph/long-running-actions-overview).

#### Folder Archive Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "driveitemthis.archive"
}
-->
``` http
POST https://graph.microsoft.com/beta/drive/root/archive
Content-type: application/json
Prefer: respond-async
```

#### Folder Archive Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true
}
-->
``` http
HTTP/1.1 202 Accepted
Location: https://graph.microsoft.com/monitor/4A3407B5-88FC-4504-8B21-0AABD3412717
```
