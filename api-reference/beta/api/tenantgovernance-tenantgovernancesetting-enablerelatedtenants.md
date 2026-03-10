---
title: "tenantGovernanceSetting: enableRelatedTenants"
description: "Enable the related tenants feature for tenant discovery."
author: "hafowler"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: apiPageType
---

# tenantGovernanceSetting: enableRelatedTenants

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Enable the related tenants feature for tenant discovery. After calling this action, the **isRelatedTenantsEnabled** property is set to `true`, which allows the use of related tenant APIs.

> [!IMPORTANT]
> This action must be called before using any related tenant APIs. Related tenant APIs will not work unless this feature is explicitly enabled.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "tenantgovernanceservices-tenantgovernancesetting-enablerelatedtenants-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/tenantgovernance-tenantgovernancesetting-enablerelatedtenants-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /directory/tenantGovernance/settings/enableRelatedTenants
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
  "name": "tenantgovernancesettingthis.enablerelatedtenants"
}
-->
``` http
POST https://graph.microsoft.com/beta/directory/tenantGovernance/settings/enableRelatedTenants
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

