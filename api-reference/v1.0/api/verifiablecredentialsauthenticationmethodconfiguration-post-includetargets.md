---
title: "Create verifiableCredentialAuthenticationMethodTarget"
description: "Create a new verifiableCredentialAuthenticationMethodTarget object."
author: "tilarso"
ms.date: 04/29/2026
ms.localizationpriority: medium
ms.subservice: "entra-sign-in"
doc_type: apiPageType
---

# Create verifiableCredentialAuthenticationMethodTarget

Namespace: microsoft.graph



Create a new verifiableCredentialAuthenticationMethodTarget object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "verifiablecredentialsauthenticationmethodconfiguration-post-includetargets-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/verifiablecredentialsauthenticationmethodconfiguration-post-includetargets-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /verifiableCredentialsAuthenticationMethodConfiguration/includeTargets
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

In the request body, supply a JSON representation of the [verifiableCredentialAuthenticationMethodTarget](../resources/verifiablecredentialauthenticationmethodtarget.md) object.

You can specify the following properties when creating a **verifiableCredentialAuthenticationMethodTarget**.

|Property|Type|Description|
|:---|:---|:---|
|isRegistrationRequired|Boolean|Indicates whether the user is required to register the authentication method. Inherited from [authenticationMethodTarget](../resources/authenticationmethodtarget.md). Required.|
|targetType|authenticationMethodTargetType|The authentication method type. Inherited from [authenticationMethodTarget](../resources/authenticationmethodtarget.md). The possible values are: `user`, `group`, `unknownFutureValue`. Required.|
|verifiedIdProfiles|Guid collection|A collection of Verified ID profile IDs. The profiles define the credentials that users can present to prove their id when signing in, onboarding, or recovering. Verified ID profiles are managed through the [Verified ID APIs](/graph/api/resources/verifiedidprofile?view=graph-rest-beta&preserve-view=true), which are currently available only in the beta endpoint. Required.|



## Response

If successful, this method returns a `201 Created` response code and a [verifiableCredentialAuthenticationMethodTarget](../resources/verifiablecredentialauthenticationmethodtarget.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "create_verifiablecredentialauthenticationmethodtarget_from_"
}
-->
``` http
POST https://graph.microsoft.com/v1.0/verifiableCredentialsAuthenticationMethodConfiguration/includeTargets
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.verifiableCredentialAuthenticationMethodTarget",
  "targetType": "String",
  "isRegistrationRequired": "Boolean",
  "verifiedIdProfiles": [
    "Guid"
  ]
}
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
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.verifiableCredentialAuthenticationMethodTarget",
  "id": "455f0838-8486-82ba-cafd-5bd6612fd5b4",
  "targetType": "String",
  "isRegistrationRequired": "Boolean",
  "verifiedIdProfiles": [
    "Guid"
  ]
}
```

