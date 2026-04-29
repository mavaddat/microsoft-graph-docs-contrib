---
title: "Delete verifiableCredentialAuthenticationMethodTarget"
description: "Delete a verifiableCredentialAuthenticationMethodTarget object."
author: "tilarso"
ms.date: 04/29/2026
ms.localizationpriority: medium
ms.subservice: "entra-sign-in"
doc_type: apiPageType
---

# Delete verifiableCredentialAuthenticationMethodTarget

Namespace: microsoft.graph



Delete a verifiableCredentialAuthenticationMethodTarget object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "verifiablecredentialsauthenticationmethodconfiguration-delete-includetargets-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/verifiablecredentialsauthenticationmethodconfiguration-delete-includetargets-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
DELETE /verifiableCredentialsAuthenticationMethodConfiguration/includeTargets/{verifiableCredentialAuthenticationMethodTargetId}/$ref
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "delete_verifiablecredentialauthenticationmethodtarget"
}
-->
``` http
DELETE https://graph.microsoft.com/v1.0/verifiableCredentialsAuthenticationMethodConfiguration/includeTargets/{verifiableCredentialAuthenticationMethodTargetId}
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true
}
-->
``` http
HTTP/1.1 204 No Content
```

