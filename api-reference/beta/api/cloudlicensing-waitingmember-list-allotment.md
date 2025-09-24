---
title: "Get waiting member"
description: "Get waiting members for an allotment by id."
author: "patrick-starrin"
ms.date: 07/18/2025
ms.localizationpriority: medium
ms.subservice: "cloud-licensing"
doc_type: apiPageType
---

# Get waiting member

Namespace: microsoft.graph.cloudLicensing

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get [microsoft.graph.cloudLicensing.waitingMember](../resources/cloudlicensing-waitingmember.md) for an allotment by id.

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
GET /admin/cloudLicensing/allotments/{allotmentId}/waitingMembers/{waitingMemberId}
```

## Optional query parameters

This method supports the `$select`, `$top`, `$expand`, and `$filter` OData query parameters to customize the response. For general information, see [OData query parameters](/graph/query-parameters).

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [allotment](../resources/cloudlicensing-allotment.md) objects in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "get_waitingmember_allotment"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/rkocgef3dgjhnu3gmu2mqhbdbmwcymnf6fk3k6a7zbui5e7gfpmi/waitingMembers/1fb53c08-3f20-4b4e-b2f0-7d8fbb6bcaea
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
  "value": {
    "@odata.type": "#microsoft.graph.cloudLicensing.waitingMember",
    "id": "49caea1b-ad15-64f1-70c5-5c5e3563d19c",
    "waitingSinceDateTime": "2024-11-22T17:11:10.6635939+00:00",
    "assignedTo": {
      "@odata.type": "#microsoft.graph.user",
      "id": "a6c034b8-621b-dee3-6abb-52cbce801fe9",
      "displayName": "Steve Fred",
      "userPrincipalName": "stevefred@contoso.com"
    }
  }
}
```