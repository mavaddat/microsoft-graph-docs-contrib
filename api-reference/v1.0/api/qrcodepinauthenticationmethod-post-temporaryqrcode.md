---
title: "Create temporary QR code"
description: "Create a temporary QR code for an existing QR code PIN authentication method."
author: "jpettere"
ms.reviewer: intelligentaccesspm
ms.date: 01/27/2026
ms.localizationpriority: medium
ms.subservice: "entra-sign-in"
doc_type: apiPageType
---

# Create temporary QR code

Namespace: microsoft.graph

Create a temporary [qrCode](../resources/qrcode.md) for an existing [qrCodePinAuthenticationMethod](../resources/qrcodepinauthenticationmethod.md). Use this operation when a user forgets to bring their badge with the standard QR code.

Temporary QR codes have a short lifetime (1-12 hours) and can't be edited after creation. If an active temporary QR code exists, you must delete it before creating a new one.

[!INCLUDE [national-cloud-support](../../includes/global-only.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "qrcodepinauthenticationmethod_post_temporaryqrcode" } -->
[!INCLUDE [permissions-table](../includes/permissions/qrcodepinauthenticationmethod-post-temporaryqrcode-permissions.md)]

[!INCLUDE [rbac-authentication-methods-apis-write-others](../includes/rbac-for-apis/rbac-authentication-methods-apis-write-others.md)]

## HTTP request

<!-- { "blockType": "ignored" } -->
```http
PATCH /users/{id | userPrincipalName}/authentication/qrCodePinMethod/temporaryQRCode
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

In the request body, supply a JSON representation of the [qrCode](../resources/qrcode.md) object with the **startDateTime** and **expireDateTime** properties.

|Property|Type|Description|
|:---|:---|:---|
|expireDateTime|DateTimeOffset|The date and time when the temporary QR code expires. The lifetime must be between 1-12 hours from the **startDateTime**. Required.|
|startDateTime|DateTimeOffset|The date and time when the temporary QR code becomes available for use. Required.|

## Response

If successful, this method returns a `201 Created` response code and a [qrCode](../resources/qrcode.md) object in the response body. The response includes the generated QR code image data, which is only returned at creation time.

### Error responses

|Scenario|HTTP code|Error code|Error message|
|:---|:---|:---|:---|
|Active temporary QR code exists|400 Bad Request|ActiveQRCodeExisted|An active temporaryQRCode exists for QR code auth method. Please delete existing temporaryQRCode before creating a new one.|
|Lifetime exceeds 12 hours|400 Bad Request|qrCodeLifeTimeExceedLimit|TemporaryQRCode lifetime exceeds the limit i.e. maximum 12 hours.|

## Examples

### Request

The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "create_temporaryqrcode"
}
-->
```http
PATCH https://graph.microsoft.com/v1.0/users/7c4999ca-a540-47ab-9ab9-8c362f5bf0fe/authentication/qrCodePinMethod/temporaryQRCode
Content-Type: application/json

{
  "startDateTime": "2026-01-30T08:00:00Z",
  "expireDateTime": "2026-01-30T18:00:00Z"
}
```

### Response

The following example shows the response.

>**Note:** The **image** property contains the QR code image data and is only returned at creation time.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.qrCode"
}
-->
```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.qrCode",
  "id": "8DF9D1B6-B4BD-4EF8-8E90-2CC63C549C80",
  "startDateTime": "2026-01-30T08:00:00Z",
  "expireDateTime": "2026-01-30T18:00:00Z",
  "createdDateTime": "2026-01-30T08:00:00Z",
  "lastUsedDateTime": "0001-01-01T00:00:00Z",
  "image": {
    "binaryValue": "Binary",
    "version": 1,
    "errorCorrectionLevel": "l",
    "rawContent": "Binary"
  }
}
```
