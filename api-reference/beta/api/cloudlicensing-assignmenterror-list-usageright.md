---
title: "List usageRight objects"
description: "Get a list of the usageRight objects affected by an assignmentError."
author: "patrick-starrin"
ms.date: 07/18/2025
ms.localizationpriority: medium
ms.subservice: "cloud-licensing"
doc_type: apiPageType
---

# List usageRight objects

Namespace: microsoft.graph.cloudLicensing

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get a list of the [usageRight](../resources/cloudlicensing-usageright.md) objects affected by an [microsoft.graph.cloudLicensing.assignmentError](../resources/cloudlicensing-assignmenterror.md). One will only be returned if there is a preexisting usageRight in effect which is prevented from updating by this assignmentError.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "cloudlicensing-assignmenterror-list-usageright-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/cloudlicensing-assignmenterror-list-usageright-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /admin/cloudLicensing/assignmentErrors/{assignmentErrorId}/usageRight
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

If successful, this method returns a `200 OK` response code and a collection of [usageRight](../resources/usageright.md) objects in the response body.

## Examples

### Example 1: Get affected usageRight for an assignment error

#### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "list_usageright"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/assignmentErrors/405ee855-dd74-f695-8d7e-be35a6788fe8/usageRight
```

#### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.cloudLicensing.usageRight"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudLicensing.usageRight",
  "id": "j6sq63x2vd3esbkifv7m42xdaugc6lfpqf3ozgvdlvk3ttnamby4",
  "skuId": "f48db87f-583c-486e-a6de-096155d8fb8f",
  "skuPartNumber": "TIME_TRAVEL_BACKUP_RESTORE",
  "services": [
    {
      "@odata.type": "microsoft.graph.cloudLicensing.service",
      "assignableTo": "user,group",
      "planId": "fe6c28b3-d468-44ea-bbd0-a10a5167435c",
      "planName": "TIME_TRAVEL_BACKUP_RESTORE_PREMIUM"
    }
  ]
}
```

### Example 2: Get affected usageRight with assignment details

The following example shows how to get the affected usageRight and include details about the assignments that contribute to it.

#### Request
<!-- {
  "blockType": "request",
  "name": "list_usageright_with_assignments"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/assignmentErrors/7bc123ef-44a2-5c91-9d8e-fa67b8901234/usageRight?$expand=assignments($expand=allotment($select=id,skuPartNumber),assignedTo($select=id,displayName))
```

#### Response
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.cloudLicensing.usageRight"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudLicensing.usageRight",
  "id": "k7tr74y3we4ftclkgw8n53yebvhd7mgqqg4p0h2ewml4uuobnczp5",
  "skuId": "f48db87f-583c-486e-a6de-096155d8fb8f",
  "skuPartNumber": "TIME_TRAVEL_BACKUP_RESTORE",
  "services": [
    {
      "@odata.type": "microsoft.graph.cloudLicensing.service",
      "assignableTo": "user,group",
      "planId": "fe6c28b3-d468-44ea-bbd0-a10a5167435c",
      "planName": "TIME_TRAVEL_BACKUP_RESTORE_PREMIUM"
    }
  ],
  "assignments": [
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
      "id": "9ef456gh-55b3-6c92-0e9f-gb78c9012345",
      "disabledServicePlanIds": [],
      "allotment": {
        "@odata.type": "#microsoft.graph.cloudLicensing.allotment",
        "id": "3cde67fg-4567-890a-bcde-fghijklmnopq",
        "skuPartNumber": "TIME_TRAVEL_BACKUP_RESTORE"
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

### Example 3: Check if assignment error affects existing usage rights

The following example shows how to determine if an assignment error is preventing updates to an existing usage right (returns empty if no existing usage right is affected).

#### Request
<!-- {
  "blockType": "request",
  "name": "check_usageright_impact"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/assignmentErrors/9ef456gh-55b3-6c92-0e9f-gb78c9012345/usageRight?$select=id,skuPartNumber,services
```

#### Response (when no existing usageRight is affected)
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.cloudLicensing.usageRight"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": []
}
```

### Example 4: Get affected usageRight filtered by service plans

The following example shows how to get the affected usageRight but only include specific service plans.

#### Request
<!-- {
  "blockType": "request",
  "name": "list_usageright_filtered_services"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/assignmentErrors/405ee855-dd74-f695-8d7e-be35a6788fe8/usageRight?$expand=services($filter=planId eq 'fe6c28b3-d468-44ea-bbd0-a10a5167435c')&$select=id,skuPartNumber,services
```

#### Response
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.cloudLicensing.usageRight"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudLicensing.usageRight",
  "id": "j6sq63x2vd3esbkifv7m42xdaugc6lfpqf3ozgvdlvk3ttnamby4",
  "skuPartNumber": "TIME_TRAVEL_BACKUP_RESTORE",
  "services": [
    {
      "@odata.type": "microsoft.graph.cloudLicensing.service",
      "assignableTo": "user,group",
      "planId": "fe6c28b3-d468-44ea-bbd0-a10a5167435c",
      "planName": "TIME_TRAVEL_BACKUP_RESTORE_PREMIUM"
    }
  ]
}
```