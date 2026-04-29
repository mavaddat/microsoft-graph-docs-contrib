---
title: "List verifiableCredentialAuthenticationMethodTarget objects"
description: "Get a list of the verifiableCredentialAuthenticationMethodTarget objects and their properties."
author: "tilarso"
ms.date: 04/29/2026
ms.localizationpriority: medium
ms.subservice: "entra-sign-in"
doc_type: apiPageType
---

# List verifiableCredentialAuthenticationMethodTarget objects

Namespace: microsoft.graph



Get a list of the verifiableCredentialAuthenticationMethodTarget objects and their properties.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "verifiablecredentialsauthenticationmethodconfiguration-list-includetargets-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/verifiablecredentialsauthenticationmethodconfiguration-list-includetargets-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /verifiableCredentialsAuthenticationMethodConfiguration/includeTargets
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

If successful, this method returns a `200 OK` response code and a collection of [verifiableCredentialAuthenticationMethodTarget](../resources/verifiablecredentialauthenticationmethodtarget.md) objects in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "list_verifiablecredentialauthenticationmethodtarget"
}
-->
``` http
GET https://graph.microsoft.com/v1.0/verifiableCredentialsAuthenticationMethodConfiguration/includeTargets
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.verifiableCredentialAuthenticationMethodTarget"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.verifiableCredentialAuthenticationMethodTarget",
      "id": "455f0838-8486-82ba-cafd-5bd6612fd5b4",
      "targetType": "String",
      "isRegistrationRequired": "Boolean",
      "verifiedIdProfiles": [
        "Guid"
      ]
    }
  ]
}
```

