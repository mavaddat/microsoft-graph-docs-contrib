---
title: "Update driveProtectionUnit"
description: "Update the properties of a driveProtectionUnit object."
author: "abbhadauria"
ms.reviewer: "haputta"
ms.localizationpriority: medium
ms.subservice: "m365-backup-storage"
doc_type: apiPageType
ms.date: 03/04/2026
---

# Update driveProtectionUnit

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Update the properties of a [driveProtectionUnit](../resources/driveprotectionunit.md) object.

[!INCLUDE [national-cloud-support](../../includes/global-only.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "driveprotectionunit_update" } -->
[!INCLUDE [permissions-table](../includes/permissions/driveprotectionunit-update-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
```http
PATCH /solutions/backupRestore/protectionUnits/{protectionUnitBaseId}
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

This API supports updates only to the **billingPolicyId** property, and only for protection units removed from backup policies (**policyId** is empty or `null`).

In the request body, provide a JSON representation of the following property.

|Property|Type|Description|
|:---|:---|:---|
|billingPolicyId|String|The unique identifier of the billing policy assigned to the protection unit. Optional. You can update this property only when the protection unit isn't attached to a protection policy (**policyId** is empty or `null`).|

> **Note:** You can't update the **billingPolicyId** property when the protection unit is attached to a protection policy (**policyId** has a value).

## Response

If successful, this method returns a `200 OK` response code and an updated [driveProtectionUnit](../resources/driveprotectionunit.md) object in the response body.

For a list of possible error responses, see [Backup Storage API error responses](/graph/backup-storage-error-codes).

## Examples

### Example 1: Update the billing policy when the protection unit isn't attached to a protection policy

The following example shows how to update the **billingPolicyId** property when the protection unit isn't attached to a protection policy.

#### Request

The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "driveprotectionunit_update_unattached_policy"
}
-->
```msgraph-interactive
PATCH https://graph.microsoft.com/beta/backupRestore/driveProtectionUnits/2b8180db-48ec-4ea3-af9f-4da73f24b9cb
Content-Type: application/json

{
  "billingPolicyId": "fa3d95b5-2878-4de7-94f5-157f4b7607aa"
}
```

#### Response

The following example shows the response.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.driveProtectionUnit"
}
-->
```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.driveProtectionUnit",
  "id": "2b8180db-48ec-4ea3-af9f-4da73f24b9cb",
  "directoryObjectId": "1f14e9e5-5b63-4e42-8a6c-4c2322ba21e1",
  "displayName": "User1",
  "email": "user1@contoso.com",
  "policyId": "",
  "billingPolicyId": "fa3d95b5-2878-4de7-94f5-157f4b7607aa",
  "status": "unprotected",
  "protectionSources": "none",
  "lastModifiedDateTime": "2026-03-05T08:30:00Z"
}
```

### Example 2: Update the billing policy when the protection unit is attached to a protection policy

The following example shows the response you get if you try to update the **billingPolicyId** property when the protection unit is attached to a protection policy.

#### Request

The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "driveprotectionunit_update_attached_policy_error"
}
-->
```http
PATCH https://graph.microsoft.com/beta/backupRestore/driveProtectionUnits/6af54655-590a-4ae6-8d04-84f4248c0f54
Content-Type: application/json

{
  "billingPolicyId": "f65f082d-a073-4451-9a3b-2355956f2cd7"
}
```

#### Response

The following example shows the response.
<!-- {
  "blockType": "response",
  "@odata.type": "microsoft.graph.publicError"
}
-->
```http
HTTP/1.1 403 Operation Not Allowed
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.publicError",
  "code": "OperationNotAllowed",
  "message": "Only protection units removed from backup policies are allowed for this API.",
  "target": "billingPolicyId",
  "details": [],
  "innerError": {
    "@odata.type": "#microsoft.graph.publicError",
    "code": "OperationNotAllowed",
    "message": "The protection unit is attached to a backup policy.",
    "target": "policyId",
    "details": [],
    "innerError": null
  }
}
```

## Related content

- [driveProtectionUnit](../resources/driveprotectionunit.md)
