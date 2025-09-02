---
title: "Restore crossTenantIdentitySyncPolicyPartner"
description: "Restore a deleted crossTenantIdentitySyncPolicyPartner object."
author: "ashyasingh"
ms.date: 06/18/2025
ms.localizationpriority: medium
ms.subservice: "entra-sign-in"
doc_type: apiPageType
---

# Restore crossTenantIdentitySyncPolicyPartner

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Restore a deleted crossTenantIdentitySyncPolicyPartner object.


[!INCLUDE [national-cloud-support](../../includes/global-only.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "crosstenantidentitysyncpolicypartner-restore-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/crosstenantidentitysyncpolicypartner-restore-permissions.md)]

[!INCLUDE [rbac-xtap-apis-write](../includes/rbac-for-apis/rbac-xtap-apis-write.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /policies/deletedItems/crossTenantSyncPolicyPartners/{crossTenantIdentitySyncPolicyPartnerId}/restore

```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this action returns a `200 OK` response code and a [crossTenantIdentitySyncPolicyPartner](../resources/crosstenantidentitysyncpolicypartner.md) in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "crosstenantidentitysyncpolicypartnerthis.restore"
}
-->
``` http
POST https://graph.microsoft.com/beta/policies/deletedItems/crossTenantSyncPolicyPartners/01d0e717-bc90-46ba-94a9-71b4a811fddb/restore
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.crossTenantIdentitySyncPolicyPartner"
}
-->
```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft-ppe.com/testppebetadeleteapis/$metadata#microsoft.graph.crossTenantIdentitySyncPolicyPartner",
  "tenantId": "01d0e717-bc90-46ba-94a9-71b4a811fddb",
  "displayName": null,
  "deletedDateTime": "2025-06-18T23:14:25Z",
  "externalCloudAuthorizedApplicationId": null,
  "userSyncInbound": null
}
```
