---
title: "Update protectionUnitBase"
description: "Update the properties of a protectionUnitBase object."
author: "abbhadauria"
ms.reviewer: "haputta"
ms.localizationpriority: medium
ms.subservice: "m365-backup-storage"
doc_type: apiPageType
ms.date: 03/04/2026
---

# Update protectionUnitBase

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Update the properties of a [protectionUnitBase](../resources/protectionunitbase.md) object.

[!INCLUDE [national-cloud-support](../../includes/global-only.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "protectionunitbase_update" } -->
[!INCLUDE [permissions-table](../includes/permissions/protectionunitbase-update-permissions.md)]

This API supports only delegated permissions for work or school accounts.

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

[!INCLUDE [table-intro](../../includes/update-property-table-intro.md)]

This API supports updating only the `billingPolicyId` property, and only for protection units removed from backup policies (`policyId` is empty or `null`).

In the request body, provide a JSON representation of the following property.

|Property|Type|Description|
|:---|:---|:---|
|billingPolicyId|String|The unique identifier of the billing policy assigned to the protection unit. Optional. You can update this property only when the protection unit isn't attached to a protection policy (`policyId` is empty or `null`).|

## Response

If successful, this method returns a `200 OK` response code and an updated [protectionUnitBase](../resources/protectionunitbase.md) object in the response body.

Updating `billingPolicyId` isn't allowed when the protection unit is attached to a protection policy (`policyId` has a value).

For a list of more possible error responses, see [Backup Storage API error responses](/graph/backup-storage-error-codes).

## Examples

### Example 1: Update billing policy when the protection unit isn't attached to a protection policy

#### Request

The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "protectionunitbase_update_unattached_policy"
}
-->
```msgraph-interactive
PATCH https://graph.microsoft.com/beta/solutions/backupRestore/protectionUnits/2b8180db-48ec-4ea3-af9f-4da73f24b9cb
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
  "@odata.type": "microsoft.graph.protectionUnitBase"
}
-->
```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "2b8180db-48ec-4ea3-af9f-4da73f24b9cb",
  "policyId": "",
  "billingPolicyId": "fa3d95b5-2878-4de7-94f5-157f4b7607aa",
  "status": "unprotected",
  "protectionSources": "none",
  "lastModifiedDateTime": "2026-03-05T08:30:00Z"
}
```

### Example 2: Update billing policy when the protection unit is attached to a protection policy

#### Request

The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "protectionunitbase_update_attached_policy_error"
}
-->
```http
PATCH https://graph.microsoft.com/beta/solutions/backupRestore/protectionUnits/6af54655-590a-4ae6-8d04-84f4248c0f54
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
  "error": {
    "code": "OperationNotAllowed",
    "message": "Only protection units removed from backup policies are allowed for this API.",
    "details": []
  }
}
```

## Related content

- [protectionUnitBase](../resources/protectionunitbase.md)
