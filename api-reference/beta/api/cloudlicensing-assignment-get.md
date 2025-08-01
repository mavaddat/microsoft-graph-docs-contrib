---
title: "Get assignment"
description: "Read the properties and relationships of microsoft.graph.cloudLicensing.assignment object."
author: "kchilka07"
ms.date: 07/18/2025
ms.localizationpriority: medium
ms.subservice: "cloud-licensing"
doc_type: apiPageType
---

# Get assignment

Namespace: microsoft.graph.cloudLicensing

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Read the properties and relationships of [microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "cloudlicensing-assignment-get-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/cloudlicensing-assignment-get-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /admin/cloudLicensing/assignments/{assignmentId}
GET /admin/cloudLicensing/allotments/{allotmentId}/assignments/{assignmentId}
GET /groups/{groupId}/cloudLicensing/assignments/{assignmentId}
GET /groups/{groupId}/cloudLicensing/usageRights/{usageRightId}/assignments/{assignmentId}
GET /me/cloudLicensing/assignments/{assignmentId}
GET /me/cloudLicensing/usageRights/{usageRightId}/assignments/{assignmentId}
GET /users/{userId}/cloudLicensing/assignments/{assignmentId}
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

If successful, this method returns a `200 OK` response code and a [microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "get_assignment"
}
-->
``` http
GET https://graph.microsoft.com/beta/me/cloudLicensing/assignments/405ee855-dd74-f695-8d7e-be35a6788fe8
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
  "value": {
    "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
    "disabledServicePlanIds": [
      "9aaf7827-d63c-4b61-89c3-182f06f82e5c"
    ],
    "id": "405ee855-dd74-f695-8d7e-be35a6788fe8"
  }
}
```

