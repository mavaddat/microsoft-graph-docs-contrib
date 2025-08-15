---
title: "List waitingMember objects"
description: "Get a list of over-assigned users who are in the waiting room for this allotment due to license capacity limits."
author: "patrick-starrin"
ms.date: 07/18/2025
ms.localizationpriority: medium
ms.subservice: "cloud-licensing"
doc_type: apiPageType
---

# List waitingMember objects

Namespace: microsoft.graph.cloudLicensing

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get a list of over-assigned users who are in the waiting room for this allotment due to license capacity limits.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "cloudlicensing-allotment-list-waitingmembers-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/cloudlicensing-allotment-list-waitingmembers-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /admin/cloudLicensing/allotments/{allotmentId}/waitingMembers
GET /users/{userId}/cloudLicensing/waitingMembers
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

If successful, this method returns a `200 OK` response code and a collection of [waitingMember](../resources/cloudlicensing-waitingmember.md) objects in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "list_waitingmember"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/{allotmentId}/waitingMembers
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.cloudLicensing.waitingMember"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.waitingMember",
      "id": "49caea1b-ad15-64f1-70c5-5c5e3563d19c",
      "waitingSinceDateTime": "2024-09-22T17:11:10.6635939+00:00"
    }
  ]
}
```

