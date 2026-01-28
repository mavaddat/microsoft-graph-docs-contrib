---
title: "Create standard QR code"
description: "Create a new standard QR code for an existing QR code PIN authentication method."
author: "jpettere"
ms.reviewer: intelligentaccesspm
ms.date: 01/27/2026
ms.localizationpriority: medium
ms.subservice: "entra-sign-in"
doc_type: apiPageType
---

# Create standard QR code

Namespace: microsoft.graph

Create a new standard [qrCode](../resources/qrcode.md) for an existing [qrCodePinAuthenticationMethod](../resources/qrcodepinauthenticationmethod.md). Use this operation when a user needs a new standard QR code, for example when their badge with the previous QR code was lost.

If an active standard QR code exists, you must delete it before creating a new one.

[!INCLUDE [national-cloud-support](../../includes/global-only.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "qrcodepinauthenticationmethod_post_standardqrcode" } -->
[!INCLUDE [permissions-table](../includes/permissions/qrcodepinauthenticationmethod-post-standardqrcode-permissions.md)]

[!INCLUDE [rbac-authentication-methods-apis-write-others](../includes/rbac-for-apis/rbac-authentication-methods-apis-write-others.md)]

## HTTP request

<!-- { "blockType": "ignored" } -->
```http
PATCH /users/{id | userPrincipalName}/authentication/qrCodePinMethod/standardQRCode
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
|expireDateTime|DateTimeOffset|The date and time when the QR code expires. The lifetime must be in days, with a minimum of 1 day and a maximum of 395 days (13 months). The default is 365 days.|
|startDateTime|DateTimeOffset|The date and time when the QR code becomes available for use.|

## Response

If successful, this method returns a `201 Created` response code and a [qrCode](../resources/qrcode.md) object in the response body. The response includes the generated QR code image data, which is only returned at creation time.

### Error responses

|Scenario|HTTP code|Error code|Error message|
|:---|:---|:---|:---|
|Active standard QR code exists|400 Bad Request|ActiveQRCodeExisted|An active standardQRCode exists for QR code auth method. Please delete existing standardQRCode before creating a new one.|

## Examples

### Request

The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "create_standardqrcode"
}
-->
```http
PATCH https://graph.microsoft.com/v1.0/users/7c4999ca-a540-47ab-9ab9-8c362f5bf0fe/authentication/qrCodePinMethod/standardQRCode
Content-Type: application/json

{
  "startDateTime": "2026-01-27T12:00:00Z",
  "expireDateTime": "2027-01-27T12:00:00Z"
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
  "id": "6C2F8B36-B6F0-46FA-9548-1EBA48BEBBDE",
  "startDateTime": "2026-01-27T12:00:00Z",
  "expireDateTime": "2027-01-27T12:00:00Z",
  "createdDateTime": "2026-01-27T12:00:00Z",
  "lastUsedDateTime": "0001-01-01T00:00:00Z",
  "image": {
    "binaryValue": "iVBORw0KGgoAAAANSUhEUgAAAAUA",
    "version": 1,
    "errorCorrectionLevel": "l",
    "rawContent": "dXNlcjpwYXNzd29yZA=="
  }
}
```
