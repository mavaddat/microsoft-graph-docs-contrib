---
title: "Delete permission from a fileStorageContainerType"
description: "Remove a permission from a fileStorageContainerType object."
author: "grjoseph"
ms.date: 02/27/2026
ms.localizationpriority: medium
ms.subservice: "sharepoint-embedded"
doc_type: apiPageType
---

# Delete permission from a fileStorageContainerType

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Remove a user [permission](../resources/permission.md) from a [fileStorageContainerType](../resources/filestoragecontainertype.md) by deleting the specified permission resource. Only existing owners (users with the `owner` role in the container type's **permissions** collection) or SharePoint Embedded Administrators or Global Administrators can remove permissions.

Owners can remove their own permission. If an owner removes their own permission and is not a SharePoint Embedded Administrator or Global Administrator, they lose access to manage the container type.

Guest users can't perform this operation.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "filestoragecontainertype-delete-permissions-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/filestoragecontainertype-delete-permissions-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
DELETE /storage/fileStorage/containerTypes/{fileStorageContainerTypeId}/permissions/{permissionId}
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request to remove a permission from a container type.
<!-- {
  "blockType": "request",
  "name": "delete_permission_filestoragecontainertype"
}
-->
``` http
DELETE https://graph.microsoft.com/beta/storage/fileStorage/containerTypes/de988700-d700-020e-0a00-0831f3042f00/permissions/b3duZXJfMTExMTExMTEtMTExMS0xMTExLTExMTEtMTExMTExMTExMTEx
```


### Response

The following example shows the response.
<!-- {
  "blockType": "response",
  "truncated": true
}
-->
``` http
HTTP/1.1 204 No Content
```

