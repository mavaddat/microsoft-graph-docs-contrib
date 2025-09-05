---
title: "List assignments"
description: "Get a list of assignments which combine to form this usageRight."
author: "patrick-starrin"
ms.date: 07/18/2025
ms.localizationpriority: medium
ms.subservice: "cloud-licensing"
doc_type: apiPageType
---

# List assignments

Namespace: microsoft.graph.cloudLicensing

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get a list of [microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md) which combine to form this [usageRight](../resources/cloudlicensing-usageright.md). This includes both direct assignments and assignments inherited through group membership.

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

If successful, this method returns a `200 OK` response code and a collection of [assignment](../resources/cloudlicensing-assignment.md) objects in the response body.

## Examples

### Example 1: Get assignments that form a usageRight

#### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "list_usageright_assignments"
}
-->
``` http
GET https://graph.microsoft.com/beta/me/cloudLicensing/usageRights/7e452304-0a58-40d6-8fd2-2afe92d26a3a/assignments
```

#### Response

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

### Example 2: Get assignments with allotment and assignee details

The following example shows how to investigate the origin of a usage right by getting detailed information about the assignments that contribute to it.

#### Request
<!-- {
  "blockType": "request",
  "name": "list_usageright_assignments_detailed"
}
-->
``` http
GET https://graph.microsoft.com/beta/me/cloudLicensing/usageRights/7e452304-0a58-40d6-8fd2-2afe92d26a3a/assignments?$expand=allotment($select=id,skuPartNumber),assignedTo($select=id,displayName)
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
  "value": [
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
      "id": "405ee855-dd74-f695-8d7e-be35a6788fe8",
      "disabledServicePlanIds": [
        "f446866a-4b4c-492e-907a-998b3fde5a81"
      ],
      "allotment": {
        "@odata.type": "#microsoft.graph.cloudLicensing.allotment",
        "id": "2afb23bc-12bb-4e01-ac77-a909d1723756",
        "skuPartNumber": "FABRIKAM_USER"
      },
      "assignedTo": {
        "@odata.type": "#microsoft.graph.user",
        "id": "d6125d65-8a97-4b1d-b5c9-14d799013255",
        "displayName": "Nasim Ahmed"
      }
    },
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
      "id": "7bc123ef-44a2-5c91-9d8e-fa67b8901234",
      "disabledServicePlanIds": [
        "3e315338-9379-453d-ac8f-c75f57ac78a1"
      ],
      "allotment": {
        "@odata.type": "#microsoft.graph.cloudLicensing.allotment",
        "id": "8def45cd-23cc-5b12-bd88-b910e2834867",
        "skuPartNumber": "FABRIKAM_USER"
      },
      "assignedTo": {
        "@odata.type": "#microsoft.graph.group",
        "id": "d8ee6ba1-2b90-4e77-90e8-3e52a09bc35a",
        "displayName": "Engineering Team"
      }
    }
  ]
}
```

### Example 3: Filter assignments by assignment type

The following example shows how to get only direct user assignments (not group assignments) that contribute to a usage right.

#### Request
<!-- {
  "blockType": "request",
  "name": "list_usageright_assignments_filtered"
}
-->
``` http
GET https://graph.microsoft.com/beta/me/cloudLicensing/usageRights/7e452304-0a58-40d6-8fd2-2afe92d26a3a/assignments?$filter=assignedTo/microsoft.graph.user ne null&$expand=assignedTo($select=id,displayName)
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
  "value": [
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
      "id": "405ee855-dd74-f695-8d7e-be35a6788fe8",
      "disabledServicePlanIds": [
        "f446866a-4b4c-492e-907a-998b3fde5a81"
      ],
      "assignedTo": {
        "@odata.type": "#microsoft.graph.user",
        "id": "d6125d65-8a97-4b1d-b5c9-14d799013255",
        "displayName": "Nasim Ahmed"
      }
    }
  ]
}
```

### Example 4: Get assignments for a group usage right

The following example shows how to get assignments for a group's usage right.

#### Request
<!-- {
  "blockType": "request",
  "name": "list_group_usageright_assignments"
}
-->
``` http
GET https://graph.microsoft.com/beta/groups/d8ee6ba1-2b90-4e77-90e8-3e52a09bc35a/cloudLicensing/usageRights/8gh567ij-1k2l-3m4n-5o6p-7q8r9s0t1u2v/assignments?$expand=allotment($select=id,skuPartNumber,allottedUnits,consumedUnits)
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
  "value": [
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
      "id": "9ef456gh-55b3-6c92-0e9f-gb78c9012345",
      "disabledServicePlanIds": [],
      "allotment": {
        "@odata.type": "#microsoft.graph.cloudLicensing.allotment",
        "id": "551f1755-0184-9e51-0bc7-f32bae5a1afb",
        "skuPartNumber": "TEAMS_PREMIUM",
        "allottedUnits": 100,
        "consumedUnits": 45
      }
    }
  ]
}
```
