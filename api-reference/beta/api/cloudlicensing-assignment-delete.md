---
title: "Delete assignment"
description: "Delete a microsoft.graph.cloudLicensing.assignment object."
author: "kunal-chilka"
ms.date: 07/18/2025
ms.localizationpriority: medium
ms.subservice: "cloud-licensing"
doc_type: apiPageType
---

# Delete assignment

Namespace: microsoft.graph.cloudLicensing

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Delete a [microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "cloudlicensing-assignment-delete-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/cloudlicensing-assignment-delete-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
DELETE /admin/cloudLicensing/assignments/{assignmentId}
DELETE /admin/cloudLicensing/allotments/{allotmentId}/assignments/{assignmentId}
DELETE /groups/{groupId}/cloudLicensing/allotments/{allotmentId}/assignments/{assignmentId}
DELETE /me/cloudLicensing/allotments/{allotmentId}/assignments/{assignmentId}
DELETE /users/{userId}/cloudLicensing/allotments/{allotmentId}/assignments/{assignmentId}
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "update_assignment"
}
-->
``` http
DELETE https://graph.microsoft.com/beta/admin/cloudLicensing/assignments/0b1a424d-3b9b-4446-80b9-6917dd521e03
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
HTTP/1.1 204 No Content
```
