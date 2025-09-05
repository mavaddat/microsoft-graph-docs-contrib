---
title: "List assignments"
description: "Get a list of license assignments which consume licenses from this allotment."
author: "patrick-starrin"
ms.date: 07/18/2025
ms.localizationpriority: medium
ms.subservice: "cloud-licensing"
doc_type: apiPageType
---

# List assignments

Namespace: microsoft.graph.cloudLicensing

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get a list of license [microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md) which consume licenses from this allotment.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "cloudlicensing-allotment-list-assignments-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/cloudlicensing-allotment-list-assignments-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /admin/cloudLicensing/allotments/{allotmentId}/assignments
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

### Example 1: Get a list of license assignments for a given allotment

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "allotment_list_assignments"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/rkocgef3dgjhnu3gmu2mqhbdbmwcymnf6fk3k6a7zbui5e7gfpmi/assignments
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

### Example 2: Get aggregated assignment count by assignee type

The following example shows how to get an aggregated count of assignments grouped by the type of entity they're assigned to (users vs groups).

#### Request
<!-- {
  "blockType": "request",
  "name": "allotment_list_assignments_aggregated"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/rkocgef3dgjhnu3gmu2mqhbdbmwcymnf6fk3k6a7zbui5e7gfpmi/assignments?$apply=groupby((assignedTo/$type), aggregate($count as assignmentCount))&$expand=assignedTo($select=@odata.type)
```

#### Response
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "assignedTo": {
        "@odata.type": "#microsoft.graph.user"
      },
      "assignmentCount": 15
    },
    {
      "assignedTo": {
        "@odata.type": "#microsoft.graph.group"
      },
      "assignmentCount": 3
    }
  ]
}
```

### Example 3: Get assignments with expanded assignee details

The following example shows how to get assignments and include details about who they're assigned to.

#### Request
<!-- {
  "blockType": "request",
  "name": "allotment_list_assignments_expanded"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/rkocgef3dgjhnu3gmu2mqhbdbmwcymnf6fk3k6a7zbui5e7gfpmi/assignments?$expand=assignedTo($select=id,displayName)&$top=3
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
  "@odata.nextLink": "https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/rkocgef3dgjhnu3gmu2mqhbdbmwcymnf6fk3k6a7zbui5e7gfpmi/assignments?$expand=assignedTo($select=id,displayName)&$top=3&$skipToken=x6eCRVFnunybXESDcrnuMIUBYtvc5r7x",
  "value": [
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
      "id": "405ee855-dd74-f695-8d7e-be35a6788fe8",
      "disabledServicePlanIds": [
        "5e62787c-c316-451f-b873-1d05acd4d12c"
      ],
      "assignedTo": {
        "@odata.type": "#microsoft.graph.user",
        "id": "d6125d65-8a97-4b1d-b5c9-14d799013255",
        "displayName": "John Smith"
      }
    },
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
      "id": "7bc123ef-44a2-5c91-9d8e-fa67b8901234",
      "disabledServicePlanIds": [],
      "assignedTo": {
        "@odata.type": "#microsoft.graph.group",
        "id": "d8ee6ba1-2b90-4e77-90e8-3e52a09bc35a",
        "displayName": "Marketing Team"
      }
    },
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
      "id": "9ef456gh-55b3-6c92-0e9f-gb78c9012345",
      "disabledServicePlanIds": [
        "6f23d6a9-adbf-481c-8538-b4c095654487"
      ],
      "assignedTo": {
        "@odata.type": "#microsoft.graph.user",
        "id": "f7bcb3b5-57c3-40e3-8075-4e9060a052ab",
        "displayName": "Jane Doe"
      }
    }
  ]
}
```

### Example 4: Filter assignments by assignee type

The following example shows how to get only assignments that are assigned to groups.

#### Request
<!-- {
  "blockType": "request",
  "name": "allotment_list_assignments_filtered_groups"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/rkocgef3dgjhnu3gmu2mqhbdbmwcymnf6fk3k6a7zbui5e7gfpmi/assignments?$filter=assignedTo/microsoft.graph.group ne null&$expand=assignedTo($select=id,displayName)
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
      "id": "7bc123ef-44a2-5c91-9d8e-fa67b8901234",
      "disabledServicePlanIds": [],
      "assignedTo": {
        "@odata.type": "#microsoft.graph.group",
        "id": "d8ee6ba1-2b90-4e77-90e8-3e52a09bc35a",
        "displayName": "Marketing Team"
      }
    }
  ]
}
```

### Example 5: Get assignments with specific service plans disabled

The following example shows how to find assignments that have a specific service plan disabled.

#### Request
<!-- {
  "blockType": "request",
  "name": "allotment_list_assignments_filtered_disabled_plans"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/rkocgef3dgjhnu3gmu2mqhbdbmwcymnf6fk3k6a7zbui5e7gfpmi/assignments?$filter=disabledServicePlanIds/any(plan: plan eq '5e62787c-c316-451f-b873-1d05acd4d12c')&$expand=assignedTo($select=id,displayName)
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
        "5e62787c-c316-451f-b873-1d05acd4d12c"
      ],
      "assignedTo": {
        "@odata.type": "#microsoft.graph.user",
        "id": "d6125d65-8a97-4b1d-b5c9-14d799013255",
        "displayName": "John Smith"
      }
    }
  ]
}
```