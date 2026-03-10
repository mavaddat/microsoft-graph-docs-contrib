---
title: "relatedTenant: refreshStatus"
description: "Get the status of a refresh operation for a related tenant."
author: "hafowler"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: apiPageType
---

# relatedTenant: refreshStatus

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get the status of a refresh operation for a [relatedTenant](../resources/tenantgovernance-relatedtenant.md) that was initiated by the [refresh](../api/tenantgovernance-relatedtenant-refresh.md) method.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "tenantgovernanceservices-relatedtenant-refreshstatus-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/tenantgovernance-relatedtenant-refreshstatus-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /directory/tenantGovernance/relatedTenants/refreshStatus
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [relatedTenantsRefreshStatus](../resources/tenantgovernance-relatedtenantsrefreshstatus.md) in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "relatedtenantthis.refreshstatus"
}
-->
``` http
GET https://graph.microsoft.com/beta/directory/tenantGovernance/relatedTenants/refreshStatus
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.tenantGovernanceServices.relatedTenantsRefreshStatus"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "microsoft.graph.tenantGovernanceServices.relatedTenantsRefreshStatus"
  }
}
```

