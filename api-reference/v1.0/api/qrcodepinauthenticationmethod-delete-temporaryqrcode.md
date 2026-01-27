---
title: "Delete temporary QR code"
description: "Delete a user's temporary QR code."
author: "jpettere"
ms.reviewer: intelligentaccesspm
ms.date: 01/27/2026
ms.localizationpriority: medium
ms.subservice: "entra-sign-in"
doc_type: apiPageType
---

# Delete temporary QR code

Namespace: microsoft.graph

Delete a user's temporary [qrCode](../resources/qrcode.md). Use this operation to revoke a temporary QR code before it expires, or to remove an expired temporary QR code.

[!INCLUDE [national-cloud-support](../../includes/global-only.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "qrcodepinauthenticationmethod_delete_temporaryqrcode" } -->
[!INCLUDE [permissions-table](../includes/permissions/qrcodepinauthenticationmethod-delete-temporaryqrcode-permissions.md)]

[!INCLUDE [rbac-authentication-methods-apis-write-others](../includes/rbac-for-apis/rbac-authentication-methods-apis-write-others.md)]

## HTTP request

<!-- { "blockType": "ignored" } -->
```http
DELETE /users/{id | userPrincipalName}/authentication/qrCodePinMethod/temporaryQRCode
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
  "name": "delete_temporaryqrcode"
}
-->
```http
DELETE https://graph.microsoft.com/v1.0/users/7c4999ca-a540-47ab-9ab9-8c362f5bf0fe/authentication/qrCodePinMethod/temporaryQRCode
```

### Response

The following example shows the response.

<!-- {
  "blockType": "response",
  "truncated": true
}
-->
```http
HTTP/1.1 204 No Content
```
