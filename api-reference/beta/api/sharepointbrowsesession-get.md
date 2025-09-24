---
title: "Get sharePointBrowseSession"
description: "Read the properties and relationships of sharePointBrowseSession object."
author: "manikantsinghms"
ms.date: 09/23/2025
ms.localizationpriority: medium
ms.subservice: "m365-backup-storage"
doc_type: apiPageType
---

# Get sharePointBrowseSession

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Read the properties and relationships of [sharePointBrowseSession](../resources/sharepointbrowsesession.md) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "sharepointbrowsesession-get-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/sharepointbrowsesession-get-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /solutions/backupRestore/sharePointBrowseSessions/{sharePointBrowseSessionId}
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

If successful, this method returns a `200 OK` response code and a [sharePointBrowseSession](../resources/sharepointbrowsesession.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "get_sharepointbrowsesession"
}
-->
``` http
GET https://graph.microsoft.com/beta/solutions/backupRestore/sharePointBrowseSessions/{sharePointBrowseSessionId}
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.sharePointBrowseSession"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.sharePointBrowseSession",
    "id": "eff933bc-09df-2bd0-d91f-4f58482a9da0",
    "status": "String",
    "createdDateTime": "String (timestamp)",
    "expirationDateTime": "String (timestamp)",
    "restorePointDateTime": "String (timestamp)",
    "backupSizeInBytes": "String",
    "error": {
      "@odata.type": "microsoft.graph.publicError"
    },
    "siteId": "String"
  }
}
```

