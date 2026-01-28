---
title: "Create qrCodePinAuthenticationMethod"
description: "Create a new QR code PIN authentication method for a user."
author: "jpettere"
ms.reviewer: intelligentaccesspm
ms.date: 01/27/2026
ms.localizationpriority: medium
ms.subservice: "entra-sign-in"
doc_type: apiPageType
---

# Create qrCodePinAuthenticationMethod

Namespace: microsoft.graph

Create a new [qrCodePinAuthenticationMethod](../resources/qrcodepinauthenticationmethod.md) object for a user. This authentication method is designed for frontline workers and requires both a standard QR code and a PIN.

Each user can have only one QR code PIN authentication method. To create a new one when an active method already exists, first delete the existing method.

[!INCLUDE [national-cloud-support](../../includes/global-only.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "authentication_post_qrcodepinauthenticationmethod" } -->
[!INCLUDE [permissions-table](../includes/permissions/authentication-post-qrcodepinauthenticationmethod-permissions.md)]

[!INCLUDE [rbac-authentication-methods-apis-write-others](../includes/rbac-for-apis/rbac-authentication-methods-apis-write-others.md)]

## HTTP request

<!-- { "blockType": "ignored" } -->
```http
PUT /users/{id | userPrincipalName}/authentication/qrCodePinMethod
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

In the request body, supply a JSON representation of the [qrCodePinAuthenticationMethod](../resources/qrcodepinauthenticationmethod.md) object with the required **standardQRCode** and **pin** properties.

|Property|Type|Description|
|:---|:---|:---|
|pin|[qrPin](../resources/qrpin.md)|The PIN for the authentication method. You must provide the **code** property with an 8-20 digit value. Required.|
|standardQRCode|[qrCode](../resources/qrcode.md)|The standard QR code for the authentication method. You must provide the **startDateTime** and **expireDateTime** properties. Required.|

> [!NOTE]
> You can't include a temporary QR code when creating a new QR code PIN authentication method. Temporary QR codes can only be added after the method is created.

## Response

If successful, this method returns a `201 Created` response code and a [qrCodePinAuthenticationMethod](../resources/qrcodepinauthenticationmethod.md) object in the response body. The response includes the generated QR code image data, which is only returned at creation time.

### Error responses

|Scenario|HTTP code|Error code|Error message|
|:---|:---|:---|:---|
|Active method already exists|400 Bad Request|tooManyQRCodePinMethod|There can be only one active QR code auth method for a user, please delete existing QR code auth method to create a new one.|
|PIN too short|400 Bad Request|pinTooShort|PIN needs to be digit only and at least 8 characters long.|
|Missing standard QR code|400 Bad Request|standardQRCodeRequired|Standard QR code is required for adding new QR code auth method.|
|Invalid request with temporary QR code|400 Bad Request|standardQRCodeRequired|Standard QR code is required for adding new QR code auth method.|

## Examples

### Request

The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "create_qrcodepinauthenticationmethod"
}
-->
```http
PUT https://graph.microsoft.com/v1.0/users/7c4999ca-a540-47ab-9ab9-8c362f5bf0fe/authentication/qrCodePinMethod
Content-Type: application/json

{
  "standardQRCode": {
    "startDateTime": "2026-01-27T12:00:00Z",
    "expireDateTime": "2027-01-27T12:00:00Z"
  },
  "pin": {
    "code": "35387687"
  }
}
```

### Response

The following example shows the response.

>**Note:** The response object shown here might be shortened for readability. The **image** property contains the QR code image data and is only returned at creation time.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.qrCodePinAuthenticationMethod"
}
-->
```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.qrCodePinAuthenticationMethod",
  "id": "6C2F8B36-B6F0-46FA-9548-1EBA48BEBBDE",
  "createdDateTime": "2026-01-27T12:00:00Z",
  "standardQRCode": {
    "id": "6C2F8B36-B6F0-46FA-9548-1EBA48BEBBDE",
    "startDateTime": "2026-01-27T12:00:00Z",
    "expireDateTime": "2027-01-27T12:00:00Z",
    "createdDateTime": "2026-01-27T12:00:00Z",
    "lastUsedDateTime": "0001-01-01T00:00:00Z",
    "image": {
      "binaryValue": "Binary",
      "version": 1,
      "errorCorrectionLevel": "l",
      "rawContent": "Binary"
    }
  },
  "temporaryQRCode": null,
  "pin": {
    "code": "35387687",
    "forceChangePinNextSignIn": true,
    "createdDateTime": "2026-01-27T12:00:00Z",
    "updatedDateTime": "0001-01-01T00:00:00Z"
  }
}
```
