---
title: "Delete engagementRoleMember"
description: "Delete a Viva Engage role from a user."
author: "richafnu"
ms.date: 09/22/2025
ms.localizationpriority: medium
ms.subservice: "viva-engage"
doc_type: apiPageType
---

# Delete engagementRoleMember

Namespace: microsoft.graph

Delete a Viva Engage [role](../resources/engagementrolemember.md) from a user.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "engagementrole_delete_members" } -->
[!INCLUDE [permissions-table](../includes/permissions/engagementrole-delete-members-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
DELETE /employeeExperience/roles/{engagementRoleId}/members/{engagementRoleMemberId}
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

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "delete_engagementrolemember"
}
-->
``` http
DELETE https://graph.microsoft.com/v1.0/employeeExperience/roles/5f3c2d11-8a9b-4d6e-b214-7c1f2b9a6d55/members/a40473a5-0fb4-a250-e029-f6fe33d07733
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
