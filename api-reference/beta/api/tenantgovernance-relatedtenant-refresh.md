---
title: "relatedTenant: refresh"
description: "Trigger a refresh operation to update related tenant data and metrics."
author: "hafowler"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: apiPageType
---

# relatedTenant: refresh

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Trigger a refresh operation to update data and metrics for a [relatedTenant](../resources/tenantgovernance-relatedtenant.md). Use the [refreshStatus](../api/tenantgovernance-relatedtenant-refreshstatus.md) method to check the status of the operation.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "tenantgovernanceservices-relatedtenant-refresh-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/tenantgovernance-relatedtenant-refresh-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /directory/tenantGovernance/relatedTenants/refresh
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this action returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "relatedtenantthis.refresh"
}
-->
``` http
POST https://graph.microsoft.com/beta/directory/tenantGovernance/relatedTenants/refresh
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
HTTP/1.1 204 No Content
```

