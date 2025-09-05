---
title: "Get assignment"
description: "Read the properties and relationships of microsoft.graph.cloudLicensing.assignment object."
author: "patrick-starrin"
ms.date: 07/18/2025
ms.localizationpriority: medium
ms.subservice: "cloud-licensing"
doc_type: apiPageType
---

# Get assignment

Namespace: microsoft.graph.cloudLicensing

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Read the properties and relationships of a [microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).


Permissions to get an **assignment** for an admin:

<!-- { "blockType": "ignored"} -->
``` http
GET /admin/cloudLicensing/assignments/{assignmentId}
GET /admin/cloudLicensing/allotments/{allotmentId}/assignments/{assignmentId}
```

<!-- { "blockType": "permissions", "name": "cloudlicensing_assignment_get" } -->
[!INCLUDE [permissions-table](../includes/permissions/cloudlicensing-assignment-get-permissions.md)]


Permissions to get an **assignment** for a user:

<!-- { "blockType": "ignored"} -->
``` http
GET /me/cloudLicensing/assignments/{assignmentId}
GET /users/{userId}/cloudLicensing/assignments/{assignmentId}
```

<!-- { "blockType": "permissions", "name": "cloudlicensing_assignment_get_user" } -->
[!INCLUDE [permissions-table](../includes/permissions/cloudlicensing-assignment-get-user-permissions.md)]


Permissions to get an **assignment** for a group:

<!-- { "blockType": "ignored"} -->
``` http
GET /groups/{groupId}/cloudLicensing/assignments/{assignmentId}
```

<!-- { "blockType": "permissions", "name": "cloudlicensing_assignment_get_group" } -->
[!INCLUDE [permissions-table](../includes/permissions/cloudlicensing-assignment-get-group-permissions.md)]


## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /admin/cloudLicensing/assignments/{assignmentId}
GET /admin/cloudLicensing/allotments/{allotmentId}/assignments/{assignmentId}
GET /groups/{groupId}/cloudLicensing/assignments/{assignmentId}
GET /me/cloudLicensing/assignments/{assignmentId}
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

### Example 1: Get assignment for a given assignmentId

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

### Example 2: Get assignment with expanded relationships

The following example shows how to get an assignment and include details about the allotment and assignee.

#### Request
<!-- {
  "blockType": "request",
  "name": "get_assignment_expanded"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/assignments/405ee855-dd74-f695-8d7e-be35a6788fe8?$expand=allotment($select=id,skuPartNumber,allottedUnits,consumedUnits),assignedTo($select=id,displayName)
```

#### Response
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
  "id": "405ee855-dd74-f695-8d7e-be35a6788fe8",
  "disabledServicePlanIds": [
    "9aaf7827-d63c-4b61-89c3-182f06f82e5c"
  ],
  "allotment": {
    "@odata.type": "#microsoft.graph.cloudLicensing.allotment",
    "id": "551f1755-0184-9e51-0bc7-f32bae5a1afb",
    "skuPartNumber": "EXCHANGESTANDARD",
    "allottedUnits": 250,
    "consumedUnits": 224
  },
  "assignedTo": {
    "@odata.type": "#microsoft.graph.user",
    "id": "d6125d65-8a97-4b1d-b5c9-14d799013255",
    "displayName": "John Smith"
  }
}
```

### Example 3: Get assignment from user perspective

The following example shows how a user can get details about their own assignment.

#### Request
<!-- {
  "blockType": "request",
  "name": "get_user_assignment"
}
-->
``` http
GET https://graph.microsoft.com/beta/me/cloudLicensing/assignments/405ee855-dd74-f695-8d7e-be35a6788fe8?$expand=allotment($select=id,skuPartNumber,services)
```

#### Response
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
  "id": "405ee855-dd74-f695-8d7e-be35a6788fe8",
  "disabledServicePlanIds": [
    "9aaf7827-d63c-4b61-89c3-182f06f82e5c"
  ],
  "allotment": {
    "@odata.type": "#microsoft.graph.cloudLicensing.allotment",
    "id": "551f1755-0184-9e51-0bc7-f32bae5a1afb",
    "skuPartNumber": "EXCHANGESTANDARD",
    "services": [
      {
        "@odata.type": "microsoft.graph.cloudLicensing.service",
        "assignableTo": "user,group",
        "planId": "9aaf7827-d63c-4b61-89c3-182f06f82e5c",
        "planName": "EXCHANGE_S_STANDARD"
      },
      {
        "@odata.type": "microsoft.graph.cloudLicensing.service",
        "assignableTo": "user,group",
        "planId": "5e62787c-c316-451f-b873-1d05acd4d12c",
        "planName": "BPOS_S_TODO_1"
      }
    ]
  }
}
```

### Example 4: Get assignment from allotment context

The following example shows how to get a specific assignment within an allotment's context.

#### Request
<!-- {
  "blockType": "request",
  "name": "get_assignment_from_allotment"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/551f1755-0184-9e51-0bc7-f32bae5a1afb/assignments/405ee855-dd74-f695-8d7e-be35a6788fe8?$expand=assignedTo($select=id,displayName)
```

#### Response
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
  "id": "405ee855-dd74-f695-8d7e-be35a6788fe8",
  "disabledServicePlanIds": [
    "9aaf7827-d63c-4b61-89c3-182f06f82e5c"
  ],
  "assignedTo": {
    "@odata.type": "#microsoft.graph.user",
    "id": "d6125d65-8a97-4b1d-b5c9-14d799013255",
    "displayName": "John Smith"
  }
}
```