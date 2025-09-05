---
title: "Get allotment"
description: "Get the allotment that is the source of an assignment's licenses."
author: "patrick-starrin"
ms.date: 07/18/2025
ms.localizationpriority: medium
ms.subservice: "cloud-licensing"
doc_type: apiPageType
---

# Get allotment

Namespace: microsoft.graph.cloudLicensing

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get the [microsoft.graph.cloudLicensing.allotment](../resources/cloudlicensing-allotment.md) that is the source of an assignment's licenses.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).


Permissions to get an **allotment** for an admin:

<!-- { "blockType": "ignored"} -->
``` http
GET /admin/cloudLicensing/assignments/{assignmentId}/allotment
```

<!-- { "blockType": "permissions", "name": "cloudlicensing-assignment-list-allotment-permissions" } -->
[!INCLUDE [permissions-table](../includes/permissions/cloudlicensing-assignment-list-allotment-permissions.md)]


Permissions to get an **allotment** for a user:

<!-- { "blockType": "ignored"} -->
``` http
GET /users/{userId}/cloudLicensing/assignments/{assignmentId}/allotment
```

<!-- { "blockType": "permissions", "name": "cloudlicensing-assignment-list-allotment-user-permissions" } -->
[!INCLUDE [permissions-table](../includes/permissions/cloudlicensing-assignment-list-allotment-user-permissions.md)]


Permissions to get an **allotment** for a group:

<!-- { "blockType": "ignored"} -->
``` http
GET /groups/{groupId}/cloudLicensing/assignments/{assignmentId}/allotment
```

<!-- { "blockType": "permissions", "name": "cloudlicensing-assignment-list-allotment-group-permissions" } -->
[!INCLUDE [permissions-table](../includes/permissions/cloudlicensing-assignment-list-allotment-group-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /admin/cloudLicensing/assignments/{assignmentId}/allotment
GET /users/{userId}/cloudLicensing/assignments/{assignmentId}/allotment
GET /groups/{groupId}/cloudLicensing/assignments/{assignmentId}/allotment
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

If successful, this method returns a `200 OK` response code and a collection of [allotment](../resources/cloudlicensing-allotment.md) objects in the response body.

## Examples

### Example 1: Get allotment for a given assignment

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "get_assignment_allotment"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/assignments/405ee855-dd74-f695-8d7e-be35a6788fe8/allotment
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.cloudLicensing.allotment"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value":
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.allotment",
      "id": "551f1755-0184-9e51-0bc7-f32bae5a1afb",
      "allottedUnits": "250",
      "assignableTo": "user,group",
      "consumedUnits": "224",
      "services": [
        {
          "@odata.type": "microsoft.graph.cloudLicensing.service",
          "assignableTo": "user,group",
          "planId": "9aaf7827-d63c-4b61-89c3-182f06f82e5c",
          "planName": "EXCHANGE_S_STANDARD"
        },
        {
          "@odata.type": "microsoft.graph.cloudLicensing.service",
          "assignableTo": "none",
          "planId": "6f23d6a9-adbf-481c-8538-b4c095654487",
          "planName": "M365_LIGHTHOUSE_CUSTOMER_PLAN1"
        },
        {
          "@odata.type": "microsoft.graph.cloudLicensing.service",
          "assignableTo": "none",
          "planId": "882e1d05-acd1-4ccb-8708-6ee03664b117",
          "planName": "INTUNE_O365"
        },
        {
          "@odata.type": "microsoft.graph.cloudLicensing.service",
          "assignableTo": "user,group",
          "planId": "5e62787c-c316-451f-b873-1d05acd4d12c",
          "planName": "BPOS_S_TODO_1"
        }
      ],
      "skuId": "4b9405b0-7788-4568-add1-99614e613b69",
      "skuPartNumber": "EXCHANGESTANDARD"
    }  
}
```

### Example 2: Get allotment with expanded assignments

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "get_assignment_allotment"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/assignments/405ee855-dd74-f695-8d7e-be35a6788fe8/allotment?$expand=assignments($expand=assignedTo($select=id,displayName))&$select=id,allottedUnits,consumedUnits,skuId,skuPartNumber,services
```

### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.cloudLicensing.allotment"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudLicensing.allotment",
  "id": "551f1755-0184-9e51-0bc7-f32bae5a1afb",
  "allottedUnits": 250,
  "assignableTo": "user,group",
  "consumedUnits": 224,
  "services": [
    {
      "@odata.type": "microsoft.graph.cloudLicensing.service",
      "assignableTo": "user,group",
      "planId": "9aaf7827-d63c-4b61-89c3-182f06f82e5c",
      "planName": "EXCHANGE_S_STANDARD"
    },
    {
      "@odata.type": "microsoft.graph.cloudLicensing.service",
      "assignableTo": "none",
      "planId": "6f23d6a9-adbf-481c-8538-b4c095654487",
      "planName": "M365_LIGHTHOUSE_CUSTOMER_PLAN1"
    },
    {
      "@odata.type": "microsoft.graph.cloudLicensing.service",
      "assignableTo": "user,group",
      "planId": "5e62787c-c316-451f-b873-1d05acd4d12c",
      "planName": "BPOS_S_TODO_1"
    }
  ],
  "skuId": "4b9405b0-7788-4568-add1-99614e613b69",
  "skuPartNumber": "EXCHANGESTANDARD",
  "assignments": [
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
      "id": "405ee855-dd74-f695-8d7e-be35a6788fe8",
      "disabledServicePlanIds": [
        "6f23d6a9-adbf-481c-8538-b4c095654487"
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
    }
  ]
}
```

### Example 3: Get allotment with filtered services

### Request

The following example shows how to get an allotment but only include services that can be assigned to users.

<!-- {
  "blockType": "request",
  "name": "get_assignment_allotment_filtered_services"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/assignments/405ee855-dd74-f695-8d7e-be35a6788fe8/allotment?$expand=services($filter=assignableTo eq 'user,group')&$select=id,skuPartNumber,services
```

### Response

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.cloudLicensing.allotment"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
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
```

### Example 4: Get allotment with computed available licenses

### Request

The following example shows how to get an allotment and compute the number of available licenses.

<!-- {
  "blockType": "request",
  "name": "get_assignment_allotment_computed"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/assignments/405ee855-dd74-f695-8d7e-be35a6788fe8/allotment?$apply=compute(allottedUnits sub consumedUnits as availableUnits)&$select=id,skuPartNumber,allottedUnits,consumedUnits,availableUnits
```

### Response

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.cloudLicensing.allotment"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudLicensing.allotment",
  "id": "551f1755-0184-9e51-0bc7-f32bae5a1afb",
  "skuPartNumber": "EXCHANGESTANDARD",
  "allottedUnits": 250,
  "consumedUnits": 224,
  "availableUnits": 26
}
```

### Example 5: Get allotment with assignment count

### Request

The following example shows how to get an allotment and include the total count of assignments.

<!-- {
  "blockType": "request",
  "name": "get_assignment_allotment_with_count"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/assignments/405ee855-dd74-f695-8d7e-be35a6788fe8/allotment?$expand=assignments($count=true;$top=0)&$select=id,skuPartNumber,allottedUnits,consumedUnits
```

### Response

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.cloudLicensing.allotment"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudLicensing.allotment",
  "id": "551f1755-0184-9e51-0bc7-f32bae5a1afb",
  "skuPartNumber": "EXCHANGESTANDARD",
  "allottedUnits": 250,
  "consumedUnits": 224,
  "assignments@odata.count": 18,
  "assignments": []
}
```