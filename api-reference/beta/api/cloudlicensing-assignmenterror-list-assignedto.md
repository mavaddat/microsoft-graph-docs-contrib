---
title: "List assignedTo"
description: "Get a user or group object for a given assignmentError to which licenses are assigned."
author: "patrick-starrin"
ms.date: 07/18/2025
ms.localizationpriority: medium
ms.subservice: "cloud-licensing"
doc_type: apiPageType
---

# List assignedTo

Namespace: microsoft.graph.cloudLicensing

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get a [user](../resources/directoryobject.md) or [group](../resources/directoryobject.md) object for a given [assignmentError](../resources/cloudlicensing-assignmenterror.md) to which licenses are assigned.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "cloudlicensing-assignmenterror-list-assignedto-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/cloudlicensing-assignmenterror-list-assignedto-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /admin/cloudLicensing/assignmentErrors/{assignmentErrorId}/assignedTo
```

## Optional query parameters

This method supports the `$select` OData query parameter to help customize the response. For general information, see [OData query parameters](/graph/query-parameters).

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [directoryObject](../resources/directoryobject.md) objects in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "list_assignmenterror_assignedto",
  "sampleKeys": ["405ee855-dd74-f695-8d7e-be35a6788fe8"]
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/assignmentErrors/405ee855-dd74-f695-8d7e-be35a6788fe8/assignedTo
```

### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "Collection(microsoft.graph.directoryObject)"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.user",
      "id": "a6c034b8-621b-dee3-6abb-52cbce801fe9",
      "displayName": "Steve Fred",
      "userPrincipalName": "stevefred@contoso.com"
    }
  ]
}
```

