---
title: "Get onFraudProtectionLoadStartListener"
description: "Read the properties and relationships of onFraudProtectionLoadStartListener object."
author: "more-rasika"
ms.date: 08/05/2025
ms.localizationpriority: medium
ms.subservice: "entra-sign-in"
doc_type: apiPageType
---

# Get onFraudProtectionLoadStartListener

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Read the properties and relationships of [onFraudProtectionLoadStartListener](../resources/onfraudprotectionloadstartlistener.md) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "onfraudprotectionloadstartlistener-get-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/onfraudprotectionloadstartlistener-get-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /onFraudProtectionLoadStartListener
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

If successful, this method returns a `200 OK` response code and an [onFraudProtectionLoadStartListener](../resources/onfraudprotectionloadstartlistener.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "get_onfraudprotectionloadstartlistener"
}
-->
``` http
GET https://graph.microsoft.com/beta/onFraudProtectionLoadStartListener
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.onFraudProtectionLoadStartListener"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.onFraudProtectionLoadStartListener",
    "id": "bfb394b8-c495-fda8-d381-265a9cfae0fe",
    "displayName": "String",
    "priority": "Integer",
    "conditions": {
      "@odata.type": "microsoft.graph.authenticationConditions"
    },
    "authenticationEventsFlowId": "String",
    "handler": {
      "@odata.type": "microsoft.graph.onFraudProtectionLoadStartHandler"
    }
  }
}
```

