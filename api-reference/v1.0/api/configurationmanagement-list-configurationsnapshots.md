---
title: "List configurationSnapshots"
description: "Get a list of the configurationSnapshot objects."
author: "swatyario"
ms.date: 03/23/2026
ms.localizationpriority: medium
ms.subservice: "tenant-administration"
doc_type: apiPageType
---

# List configurationSnapshots

Namespace: microsoft.graph

Get a list of [configurationSnapshot](../resources/configurationsnapshot.md) objects.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "configurationmanagement-list-configurationsnapshots-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/configurationmanagement-list-configurationsnapshots-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /admin/configurationManagement/configurationSnapshots
```

## Optional query parameters

This method supports the `$select`, `$filter`, `$orderBy`, and `$top` OData query parameters to help customize the response. The default page size is 100 items and the maximum page size is 999 items. For general information, see [OData query parameters](/graph/query-parameters).

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [configurationBaseline](../resources/configurationbaseline.md) objects in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "list_configurationsnapshots"
}
-->
``` http
GET https://graph.microsoft.com/v1.0/admin/configurationManagement/configurationSnapshots
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "Collection(microsoft.graph.configurationBaseline)"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.configurationBaseline",
      "id": "51511c1b-8700-1ba8-d667-0891eda8015f",
      "displayName": "String",
      "description": "String",
      "parameters": [
        {
          "@odata.type": "microsoft.graph.baselineParameter"
        }
      ],
      "resources": [
        {
          "@odata.type": "microsoft.graph.baselineResource"
        }
      ]
    }
  ]
}
```

