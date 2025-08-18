---
title: "Update assignment"
description: "Update the properties of a assignment object."
author: "patrick-starrin"
ms.date: 07/18/2025
ms.localizationpriority: medium
ms.subservice: "cloud-licensing"
doc_type: apiPageType
---

# Update assignment

Namespace: microsoft.graph.cloudLicensing

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Update a [microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md) object to enable or disable services. Any service contained in its allotment which is not listed in the disabledServicePlanIds array is enabled.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "cloudlicensing-assignment-update-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/cloudlicensing-assignment-update-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
PATCH /admin/cloudLicensing/assignments/{assignmentId}
PATCH /admin/cloudLicensing/allotments/{allotmentId}/assignments/{assignmentId}
PATCH /groups/{groupId}/cloudLicensing/assignments/{assignmentId}
PATCH /me/cloudLicensing/allotments/{allotmentId}/assignments/{assignmentId}
PATCH /users/{userId}/cloudLicensing/assignments/{assignmentId}
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

[!INCLUDE [table-intro](../../includes/update-property-table-intro.md)]

|Property|Type|Description|
|:---|:---|:---|
|disabledServicePlanIds|Guid collection|The list of disabled service plans for this assignment. An empty list indicates that all services are enabled. Required. Not nullable.|




## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "update_assignment"
}
-->
``` http
PATCH https://graph.microsoft.com/beta/userCloudLicensing/assignments/0b1a424d-3b9b-4446-80b9-6917dd521e03
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
  "disabledServicePlanIds": [
    "Guid"
  ]
}
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
  "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
  "disabledServicePlanIds": [
    "Guid"
  ],
  "id": "405ee855-dd74-f695-8d7e-be35a6788fe8"
}
```

