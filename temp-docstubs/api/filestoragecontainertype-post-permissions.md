---
title: "Create permission for a fileStorageContainerType"
description: "Add a permission to a fileStorageContainerType object."
author: "grjoseph"
ms.date: 02/27/2026
ms.localizationpriority: medium
ms.subservice: "sharepoint-embedded"
doc_type: apiPageType
---

# Create permission for a fileStorageContainerType

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Add a user [permission](../resources/permission.md) to a [fileStorageContainerType](../resources/filestoragecontainertype.md). Only existing owners (users with the `owner` role in the container type's **permissions** collection) or SharePoint Embedded Administrators or Global Administrators can add permissions.

The following constraints apply:
- A maximum of **3** permissions per container type is allowed. Adding a fourth permission returns a `400 Bad Request` error.
- Duplicate permissions are silently ignored (idempotent). If the specified user already has a permission, the existing permission is returned with a `201 Created` status.
- Currently only the `owner` role is supported.

Guest users can't perform this operation.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "filestoragecontainertype-post-permissions-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/filestoragecontainertype-post-permissions-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /storage/fileStorage/containerTypes/{fileStorageContainerTypeId}/permissions
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

In the request body, supply a JSON representation of the [permission](../resources/permission.md) object.

You can specify the following properties when creating a **permission**.

|Property|Type|Description|
|:---|:---|:---|
|roles|String collection|The roles granted to the user. Currently only `owner` is supported. Required.|
|grantedToV2|[sharePointIdentitySet](../resources/sharepointidentityset.md)|The identity of the user to grant the permission to. You must specify the **user** property with the user's **id**. Required.|



## Response

If successful, this method returns a `201 Created` response code and a [permission](../resources/permission.md) object in the response body.

## Examples

### Request

The following example shows a request to add an owner permission to a container type.
<!-- {
  "blockType": "request",
  "name": "create_permission_from_filestoragecontainertype"
}
-->
``` http
POST https://graph.microsoft.com/beta/storage/fileStorage/containerTypes/de988700-d700-020e-0a00-0831f3042f00/permissions
Content-Type: application/json

{
  "roles": ["owner"],
  "grantedToV2": {
    "user": {
      "id": "11111111-1111-1111-1111-111111111111"
    }
  }
}
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.permission"
}
-->
``` http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.permission",
  "id": "b3duZXJfMTExMTExMTEtMTExMS0xMTExLTExMTEtMTExMTExMTExMTEx",
  "roles": ["owner"],
  "grantedToV2": {
    "user": {
      "id": "11111111-1111-1111-1111-111111111111"
    }
  }
}
```

