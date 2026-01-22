---
title: "driveItem: unarchive"
description: "Unarchive a drive item"
author: "dcun55"
ms.date: 01/20/2026
ms.localizationpriority: medium
ms.subservice: "sharepoint"
doc_type: apiPageType
---

# driveItem: unarchive

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Unarchives a [DriveItem](../resources/driveitem.md).

**File Unarchive**: Unarchives a single archived file using a synchronous request. If the archived file was recently archived, the file is unarchived immediately. Otherwise, the archived file starts the reactivation process.

_Note_: File DriveItem Unarchive is not supported when the request includes the Prefer: respond-async header.

**Folder Unarchive**: Unarchives all archived files within a folder using an asynchronous request. The operation is initiated asynchronously, and a [monitor URL](/graph/long-running-actions-overview) is returned in the response to allow clients to track the progress of the unarchive operation.

Use the [monitor URL](/graph/long-running-actions-overview) to track progress until the operation completes.

_Note_: Folder DriveItem Unarchive is supported only when the request includes the Prefer: respond-async header
## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "driveitem-unarchive-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/driveitem-unarchive-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /drive/root/unarchive
POST /drives/{drivesId}/root/unarchive
POST /shares/{sharesId}/root/unarchive
POST /drive/items/{driveItemId}/unarchive
POST /shares/{sharesId}/driveItem/unarchive
POST /drive/bundles/{driveItemId}/unarchive
POST /drive/special/{driveItemId}/unarchive
POST /drive/following/{driveItemId}/unarchive
```

## Request headers

| Name          | Description                                                                                               |
|:--------------|:----------------------------------------------------------------------------------------------------------|
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts). |
| Prefer        | respond-async. Indicates that the request is an async request. Optional.                                  |

## Request body

Don't supply a request body for this method.

## Response

If successful, this action returns a `200 OK` response code for file [DriveItem](../resources/driveitem.md). The response body will include the driveItem’s metadata, with the archiveStatus property included under the [FileFacet](../resources/file.md).

Otherwise, if successful, this action returns a `202 Accepted` response code, with a monitor URI, is returned for folder [DriveItem](../resources/driveitem.md).

## Examples

### File Unarchive Example

For a file unarchive operation on the [DriveItem](../resources/driveitem.md), the request completes synchronously and returns `200 OK` with the archiveStatus, unarchived or reactivating, property included under the [FileFacet](../resources/file.md).

#### File Unarchive Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "driveitemthis.unarchive"
}
-->
``` http
POST https://graph.microsoft.com/beta/drive/root/unarchive
```

#### File Unarchive Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true
}
-->
``` json
HTTP/1.1 200 OK
Content-type: application/json
    "createdDateTime": "2016-03-21T20:01:37Z",
    "cTag": "\"c:{86EB4C8E-D20D-46B9-AD41-23B8868DDA8A},0\"",
    "eTag": "\"{86EB4C8E-D20D-46B9-AD41-23B8868DDA8A},1\"",
    "id": "01NKDM7HMOJTVYMDOSXFDK2QJDXCDI3WUK",
    "lastModifiedDateTime": "2025-07-21T20:01:37Z",
    "name": "Feature.txt",
    "file": {
        "archiveStatus": "reactivating",
        "hashes": {
            "quickXorHash": "Sy2meSLBupGTGjRSLAv3LPpWqwo="
        },
        "mimeType": "text/plain"
    },
    "fileSystemInfo": {
        "createdDateTime": "2025-07-21T20:01:37Z",
        "lastModifiedDateTime": "2025-07-21T20:01:37Z"
    },
    "size": 157286400
```

### Folder Unarchive Example

For a folder unarchive operation on the [DriveItem](../resources/driveitem.md), the request completes asynchronously and returns `202 Accepted` with a [monitor URL](/graph/long-running-actions-overview).

#### Folder Unarchive Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "driveitemthis.unarchive"
}
-->
``` http
POST https://graph.microsoft.com/beta/drive/root/unarchive
Content-type: application/json
Prefer: respond-async
```

#### Folder Unarchive Response

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