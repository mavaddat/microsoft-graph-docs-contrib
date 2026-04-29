---
title: "Update verifiableCredentialAuthenticationMethodTarget"
description: "Update the properties of a verifiableCredentialAuthenticationMethodTarget object."
author: "tilarso"
ms.date: 04/29/2026
ms.localizationpriority: medium
ms.subservice: "entra-sign-in"
doc_type: apiPageType
---

# Update verifiableCredentialAuthenticationMethodTarget

Namespace: microsoft.graph



Update the properties of a verifiableCredentialAuthenticationMethodTarget object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "verifiablecredentialauthenticationmethodtarget-update-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/verifiablecredentialauthenticationmethodtarget-update-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
PATCH /verifiableCredentialsAuthenticationMethodConfiguration/includeTargets/{verifiableCredentialAuthenticationMethodTargetId}
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

[!INCLUDE [table-intro](../../includes/update-property-table-intro.md)]

|Property|Type|Description|
|:---|:---|:---|
|isRegistrationRequired|Boolean|Indicates whether the user is required to register the authentication method. Inherited from [authenticationMethodTarget](../resources/authenticationmethodtarget.md). Optional.|
|targetType|authenticationMethodTargetType|The authentication method type. Inherited from [authenticationMethodTarget](../resources/authenticationmethodtarget.md). The possible values are: `user`, `group`, `unknownFutureValue`. Optional.|
|verifiedIdProfiles|Guid collection|A collection of Verified ID profile IDs. The profiles define the credentials that users can present to prove their id when signing in, onboarding, or recovering. Verified ID profiles are managed through the [Verified ID APIs](/graph/api/resources/verifiedidprofile?view=graph-rest-beta&preserve-view=true), which are currently available only in the beta endpoint. Optional.|



## Response

If successful, this method returns a `200 OK` response code and an updated [verifiableCredentialAuthenticationMethodTarget](../resources/verifiablecredentialauthenticationmethodtarget.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "update_verifiablecredentialauthenticationmethodtarget"
}
-->
``` http
PATCH https://graph.microsoft.com/v1.0/verifiableCredentialsAuthenticationMethodConfiguration/includeTargets/{verifiableCredentialAuthenticationMethodTargetId}
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
  "truncated": true
}
-->
``` http
HTTP/1.1 200 OK
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

