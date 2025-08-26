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

Get a list of the usageRight objects affected by an assignmentError. One will only be returned if there is a preexisting usageRight in effect which is prevented from updating by this assignmentError.

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

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "list_usageright"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/assignmentErrors/{assignmentErrorId}/usageRight
```


### Response

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
  "skuId": "639dec6b-bb19-468b-871c-c5c441c4b0cb",
  "skuPartNumber": "Microsoft_365_Copilot",
  "services": [
    {
      "@odata.type": "microsoft.graph.cloudLicensing.service",
      "assignableTo": "user,group",
      "planId": "fe6c28b3-d468-44ea-bbd0-a10a5167435c",
      "planName": "COPILOT_STUDIO_IN_COPILOT_FOR_M365"
    }
  ]
}
```

