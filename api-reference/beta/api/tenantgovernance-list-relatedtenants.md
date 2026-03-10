---
title: "List relatedTenants"
description: "Get a list of related tenants discovered through the tenant discovery feature."
author: "hafowler"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: apiPageType
---

# List relatedTenants

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get a list of the [relatedTenant](../resources/tenantgovernance-relatedtenant.md) objects and their properties. This returns tenants discovered through the tenant discovery feature.

> [!IMPORTANT]
> This API requires that the **isRelatedTenantsEnabled** property is set to `true` by calling the [enableRelatedTenants](../api/tenantgovernance-tenantgovernancesetting-enablerelatedtenants.md) action first.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "tenantgovernanceservices-tenantgovernance-list-relatedtenants-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/tenantgovernance-tenantgovernance-list-relatedtenants-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /directory/tenantGovernance/relatedTenants
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](/graph/query-parameters).

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [relatedTenant](../resources/relatedtenant.md) objects in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "list_relatedtenant"
}
-->
``` http
GET https://graph.microsoft.com/beta/directory/tenantGovernance/relatedTenants
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.tenantGovernanceServices.relatedTenant"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.tenantGovernanceServices.relatedTenant",
      "id": "9e95a368-1877-7e3e-206d-34ac51cb1397",
      "createdDateTime": "String (timestamp)"
    }
  ]
}
```

