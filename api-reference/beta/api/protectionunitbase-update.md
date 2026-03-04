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

In the request body, provide a JSON representation of the following property.

|Property|Type|Description|
|:---|:---|:---|
|billingPolicyId|String|The unique identifier of the billing policy assigned to the protection unit. Optional.|

## Response

If successful, this method returns a `200 OK` response code and an updated [protectionUnitBase](../resources/protectionunitbase.md) object in the response body.

### Errors

The following error scenarios are specific to this API:
- `404 Not Found` with error code `BillingPolicyNotFound`.
- `409 Conflict` with error code `ConflictState`.
- `422 Unprocessable Entity` with error code `InvalidBillingPolicyAssignment`.

For a list of more possible error responses, see [Backup Storage API error responses](/graph/backup-storage-error-codes).

## Examples

### Example 1: Update billing policy on a protection unit

#### Request

The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "protectionunitbase_update"
}
-->
```msgraph-interactive
PATCH https://graph.microsoft.com/beta/solutions/backupRestore/protectionUnits/89014d8c-71fe-4d00-a01a-31850bc5b32c
Content-Type: application/json

{
  "billingPolicyId": "7b18e4d3-4033-4408-a165-b0f352dec262"
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
  "id": "89014d8c-71fe-4d00-a01a-31850bc5b32c",
  "policyId": "845457dc-4bb2-4815-bef3-8628ebd1952e",
  "billingPolicyId": "7b18e4d3-4033-4408-a165-b0f352dec262",
  "status": "protected",
  "lastModifiedDateTime": "2026-02-20T12:00:00Z"
}
```

### Example 2: Update with a billing policy that doesn't exist

#### Request

The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "protectionunitbase_update_error_example"
}
-->
```http
PATCH https://graph.microsoft.com/beta/solutions/backupRestore/protectionUnits/12345678-1234-1234-1234-123456789012
Content-Type: application/json

{
  "billingPolicyId": "00000000-0000-0000-0000-000000000000"
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
HTTP/1.1 404 Not Found
Content-Type: application/json

{
  "error": {
    "code": "BillingPolicyNotFound",
    "message": "The specified billing policy '00000000-0000-0000-0000-000000000000' does not exist or is not accessible.",
    "innerError": {
      "date": "2026-02-20T12:00:00",
      "request-id": "12345678-1234-1234-1234-123456789012",
      "client-request-id": "87654321-4321-4321-4321-210987654321"
    }
  }
}
```

## Related content

- [protectionUnitBase](../resources/protectionunitbase.md)
- [Backup Storage API error responses](/graph/backup-storage-error-codes)
