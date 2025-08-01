---
title: "List allotment"
description: "Get waiting members for an allotment by id."
author: "kchilka07"
ms.date: 07/18/2025
ms.localizationpriority: medium
ms.subservice: "cloud-licensing"
doc_type: apiPageType
---

# List allotment

Namespace: microsoft.graph.cloudLicensing

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get waiting members for an allotment by id.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "cloudlicensing-waitingmember-list-allotment-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/cloudlicensing-waitingmember-list-allotment-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /admin/cloudLicensing/allotments/{allotmentId}/waitingMembers/{waitingMemberId}/allotment
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

If successful, this method returns a `200 OK` response code and a collection of [allotment](../resources/allotment.md) objects in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "list_allotment"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/{allotmentId}/waitingMembers/{waitingMemberId}
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
  "value": [
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.allotment",
      "allottedUnits": "100",
      "assignableTo": "user,group",
      "consumedUnits": "84",
      "id": "551f1755-0184-9e51-0bc7-f32bae5a1afb",
      "services": [
        {
          "@odata.type": "microsoft.graph.cloudLicensing.service"
          "assignableTo": "user,group",
          "planId": "f4f2f6de-6830-442b-a433-e92249faebe2",
          "planName": "TeamsEss"
        }
      ],
      "skuId": "f245ecc8-75af-4f8e-b61f-27d8114de5f3",
      "skuPartNumber": "Teams_Ess"
    }
  ]
}
```

