---
title: "List assignments"
description: "Get a list of assignments which combine to form this usageRight."
author: "kchilka07"
ms.date: 07/18/2025
ms.localizationpriority: medium
ms.subservice: "cloud-licensing"
doc_type: apiPageType
---

# List assignments

Namespace: microsoft.graph.cloudLicensing

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get a list of assignments which combine to form this usageRight. This includes both direct assignments and assignments inherited through group membership.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

Permissions to list usageRight assignments for a user:

<!-- { "blockType": "ignored"} -->
``` http
GET /me/cloudLicensing/usageRights/{usageRightId}/assignments
GET /users/{userId}/cloudLicensing/usageRights/{usageRightId}/assignments
```

<!-- { "blockType": "permissions", "name": "cloudlicensing_usageright_get", "requestUrls": "GET /users/{userId}/cloudLicensing/usageRights/{usageRightId}" } -->
|Permission type|Least privileged permissions|Higher privileged permissions|
|:---|:---|:---|
|Delegated (work or school account)|User-UsageRight.Read|Directory.Read.All, Directory.ReadWrite.All, User-CloudLicensing.Read, User-CloudLicensing.Read.All, User-UsageRight.Read.All, User.Read, User.Read.All, User.ReadWrite, User.ReadWrite.All|
|Delegated (personal Microsoft account)|Not supported.|Not supported.|
|Application|User-UsageRight.Read.All|Directory.Read.All, Directory.ReadWrite.All, User-CloudLicensing.Read.All, User.Read.All, User.ReadWrite.All|

Permissions to list usageRight assignments for a group:

<!-- { "blockType": "ignored"} -->
``` http
GET /groups/{groupId}/cloudLicensing/usageRights/{usageRightId}/assignments
```

<!-- { "blockType": "permissions", "name": "cloudlicensing_usageright_get", "requestUrls": "GET /groups/{groupId}/cloudLicensing/usageRights/{usageRightId}" } -->
|Permission type|Least privileged permissions|Higher privileged permissions|
|:---|:---|:---|
|Delegated (work or school account)|Group-UsageRight.Read.All|Directory.Read.All, Directory.ReadWrite.All, Group-CloudLicensing.Read, Group-CloudLicensing.Read.All, Group.Read.All, Group.ReadWrite.All, User.Read.All, User.ReadWrite.All|
|Delegated (personal Microsoft account)|Not supported.|Not supported.|
|Application|Group-UsageRight.Read.All|Directory.Read.All, Directory.ReadWrite.All, Group-CloudLicensing.Read.All, Group.Read.All, Group.ReadWrite.All, User.Read.All, User.ReadWrite.All|


<!-- {
  "blockType": "permissions",
  "name": "cloudlicensing-usageright-list-assignments-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/cloudlicensing-usageright-list-assignments-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /groups/{groupId}/cloudLicensing/usageRights/{usageRightId}/assignments
GET /me/cloudLicensing/usageRights/{usageRightId}/assignments
GET /users/{userId}/cloudLicensing/usageRights/{usageRightId}/assignments
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

If successful, this method returns a `200 OK` response code and a collection of [assignment](../resources/assignment.md) objects in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "list_assignment"
}
-->
``` http
GET https://graph.microsoft.com/beta/me/cloudLicensing/usageRights/{usageRightId}/assignments
```

### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.cloudLicensing.assignment"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
      "id": "405ee855-dd74-f695-8d7e-be35a6788fe8",
      "disabledServicePlanIds": [
        "5e62787c-c316-451f-b873-1d05acd4d12c"
      ]
    }
  ]
}
```
