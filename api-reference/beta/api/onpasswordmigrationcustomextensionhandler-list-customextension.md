---
title: "List onPasswordSubmitCustomExtension objects"
description: "Get a list of the onPasswordSubmitCustomExtension objects and their properties."
author: "**TODO: Provide GitHub Name. See [topic-level metadata reference](https://eng.ms/docs/products/microsoft-graph-service/microsoft-graph/document-apis/metadata)**"
ms.date: 01/13/2026
ms.localizationpriority: medium
ms.subservice: "**TODO: Add MS subservice. See [topic-level metadata reference](https://eng.ms/docs/products/microsoft-graph-service/microsoft-graph/document-apis/metadata)**"
doc_type: apiPageType
---

# List onPasswordSubmitCustomExtension objects

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get a list of the onPasswordSubmitCustomExtension objects and their properties.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "onpasswordmigrationcustomextensionhandler-list-customextension-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/onpasswordmigrationcustomextensionhandler-list-customextension-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET ** Collection URI for microsoft.graph.onPasswordSubmitCustomExtension not found
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

If successful, this method returns a `200 OK` response code and a collection of [onPasswordSubmitCustomExtension](../resources/onpasswordsubmitcustomextension.md) objects in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "list_onpasswordsubmitcustomextension"
}
-->
``` http
GET https://graph.microsoft.com/beta** Collection URI for microsoft.graph.onPasswordSubmitCustomExtension not found
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.onPasswordSubmitCustomExtension"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.onPasswordSubmitCustomExtension",
      "id": "a399e619-5c52-52b4-480f-2aa11c867a3e",
      "authenticationConfiguration": {
        "@odata.type": "microsoft.graph.customExtensionAuthenticationConfiguration"
      },
      "clientConfiguration": {
        "@odata.type": "microsoft.graph.customExtensionClientConfiguration"
      },
      "description": "String",
      "displayName": "String",
      "endpointConfiguration": {
        "@odata.type": "microsoft.graph.customExtensionEndpointConfiguration"
      },
      "behaviorOnError": {
        "@odata.type": "microsoft.graph.customExtensionBehaviorOnError"
      }
    }
  ]
}
```

