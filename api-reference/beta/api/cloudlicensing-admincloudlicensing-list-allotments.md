---
title: "List allotment objects"
description: "Get a list of the allotment objects and their properties."
author: "kunal-chilka"
ms.date: 07/18/2025
ms.localizationpriority: medium
ms.subservice: "cloud-licensing"
doc_type: apiPageType
---

# List allotment objects

Namespace: microsoft.graph.cloudLicensing

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get a list of the [microsoft.graph.cloudLicensing.allotment](../resources/cloudlicensing-allotment.md) objects and their properties.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "cloudlicensing-admincloudlicensing-list-allotments-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/cloudlicensing-admincloudlicensing-list-allotments-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /admin/cloudLicensing/allotments
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
GET https://graph.microsoft.com/beta/admin/cloudLicensing/allotments
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
  ]
}
```

