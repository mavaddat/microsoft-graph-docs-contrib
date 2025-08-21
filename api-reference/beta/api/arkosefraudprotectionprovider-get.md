---
title: "Get arkoseFraudProtectionProvider"
description: "Read the properties and relationships of arkoseFraudProtectionProvider object."
author: "more-rasika"
ms.date: 08/05/2025
ms.localizationpriority: medium
ms.subservice: "entra-sign-in"
doc_type: apiPageType
---

# Get arkoseFraudProtectionProvider

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Read the properties and relationships of [arkoseFraudProtectionProvider](../resources/arkosefraudprotectionprovider.md) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "arkosefraudprotectionprovider-get-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/arkosefraudprotectionprovider-get-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /arkoseFraudProtectionProvider
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

If successful, this method returns a `200 OK` response code and an [arkoseFraudProtectionProvider](../resources/arkosefraudprotectionprovider.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "get_arkosefraudprotectionprovider"
}
-->
``` http
GET https://graph.microsoft.com/beta/arkoseFraudProtectionProvider
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.arkoseFraudProtectionProvider"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.arkoseFraudProtectionProvider",
    "id": "37156c9d-7b03-fc84-9125-3a60757d1ef6",
    "displayName": "String",
    "publicKey": "String",
    "privateKey": "String",
    "clientSubDomain": "String",
    "verifySubDomain": "String"
  }
}
```

