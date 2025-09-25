---
title: "List granularDriveRestoreArtifact objects"
description: "Get a list of the granularDriveRestoreArtifact objects and their properties."
author: "manikantsinghms"
ms.date: 09/23/2025
ms.localizationpriority: medium
ms.subservice: "m365-backup-storage"
doc_type: apiPageType
---

# List granularDriveRestoreArtifact objects

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get a list of the granularDriveRestoreArtifact objects and their properties.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "onedriveforbusinessrestoresession-list-granulardriverestoreartifacts-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/onedriveforbusinessrestoresession-list-granulardriverestoreartifacts-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /solutions/backupRestore/oneDriveForBusinessRestoreSessions/{oneDriveForBusinessRestoreSessionId}/granularDriveRestoreArtifacts
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](/graph/query-parameters).

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [granularDriveRestoreArtifact](../resources/granulardriverestoreartifact.md) objects in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "list_granulardriverestoreartifact"
}
-->
``` http
GET https://graph.microsoft.com/beta/solutions/backupRestore/oneDriveForBusinessRestoreSessions/{oneDriveForBusinessRestoreSessionId}/granularDriveRestoreArtifacts
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.granularDriveRestoreArtifact"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.granularDriveRestoreArtifact",
      "id": "c08c8109-bc9e-ec60-c1a9-0798c2e5706e",
      "browseSessionId": "String",
      "status": "String",
      "webUrl": "String",
      "restoredItemKey": "String",
      "restoredItemPath": "String",
      "restoredItemWebUrl": "String",
      "restorePointDateTime": "String (timestamp)",
      "startDateTime": "String (timestamp)",
      "completionDateTime": "String (timestamp)",
      "directoryObjectId": "String"
    }
  ]
}
```

