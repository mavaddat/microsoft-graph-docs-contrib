---
title: "Reset PIN"
description: "Reset a user's PIN and generate a new temporary PIN."
author: "jpettere"
ms.reviewer: intelligentaccesspm
ms.date: 01/27/2026
ms.localizationpriority: medium
ms.subservice: "entra-sign-in"
doc_type: apiPageType
---

# Reset PIN

Namespace: microsoft.graph

Reset a user's [qrPin](../resources/qrpin.md) and generate a new temporary PIN. Use this operation when a user has forgotten their PIN. The new PIN is automatically generated and the user must change it on their next sign-in.

[!INCLUDE [national-cloud-support](../../includes/global-only.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "qrcodepinauthenticationmethod_resetpin" } -->
[!INCLUDE [permissions-table](../includes/permissions/qrcodepinauthenticationmethod-resetpin-permissions.md)]

[!INCLUDE [rbac-authentication-methods-apis-write-others](../includes/rbac-for-apis/rbac-authentication-methods-apis-write-others.md)]

## HTTP request

<!-- { "blockType": "ignored" } -->
```http
PATCH /users/{id | userPrincipalName}/authentication/qrCodePinMethod/pin
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

In the request body, supply an empty JSON object or a JSON representation with an empty **pin** property.

```json
{
  "pin": ""
}
```

## Response

If successful, this method returns a `201 Created` response code and a [qrPin](../resources/qrpin.md) object in the response body. The response includes the new temporary PIN code, which should be communicated to the user. The **forceChangePinNextSignIn** property is set to `true`.

## Examples

### Request

The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "reset_pin"
}
-->
```http
PATCH https://graph.microsoft.com/v1.0/users/7c4999ca-a540-47ab-9ab9-8c362f5bf0fe/authentication/qrCodePinMethod/pin
Content-Type: application/json

{
  "pin": ""
}
```

### Response

The following example shows the response.

>**Note:** The **code** property contains the new temporary PIN that should be communicated to the user. This value is only returned in the response to this operation.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.qrPin"
}
-->
```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.qrPin",
  "code": "35387687",
  "forceChangePinNextSignIn": true,
  "createdDateTime": "2026-01-27T12:00:00Z",
  "updatedDateTime": "2026-01-30T10:00:00Z"
}
```
