---
title: "Get onPasswordSubmitListener"
description: "Read the properties and relationships of onPasswordSubmitListener object."
author: "**TODO: Provide GitHub Name. See [topic-level metadata reference](https://eng.ms/docs/products/microsoft-graph-service/microsoft-graph/document-apis/metadata)**"
ms.date: 01/13/2026
ms.localizationpriority: medium
ms.subservice: "**TODO: Add MS subservice. See [topic-level metadata reference](https://eng.ms/docs/products/microsoft-graph-service/microsoft-graph/document-apis/metadata)**"
doc_type: apiPageType
---

# Get onPasswordSubmitListener

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Read the properties and relationships of [onPasswordSubmitListener](../resources/onpasswordsubmitlistener.md) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "onpasswordsubmitlistener-get-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/onpasswordsubmitlistener-get-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /onPasswordSubmitListener
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

If successful, this method returns a `200 OK` response code and an [onPasswordSubmitListener](../resources/onpasswordsubmitlistener.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "get_onpasswordsubmitlistener"
}
-->
``` http
GET https://graph.microsoft.com/beta/onPasswordSubmitListener
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.onPasswordSubmitListener"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.onPasswordSubmitListener",
    "id": "b2e2ea91-9a99-56e1-b0ae-9bbcb7323b2a",
    "displayName": "String",
    "priority": "Integer",
    "conditions": {
      "@odata.type": "microsoft.graph.authenticationConditions"
    },
    "authenticationEventsFlowId": "String",
    "handler": {
      "@odata.type": "microsoft.graph.onPasswordSubmitHandler"
    }
  }
}
```

