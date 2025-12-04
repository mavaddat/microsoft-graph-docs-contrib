---
title: "Get externalOriginResourceConnector"
description: "Read the properties and relationships of externalOriginResourceConnector object."
author: "vikama-microsoft"
ms.date: 11/11/2025
ms.localizationpriority: medium
ms.subservice: "entra-id-governance"
doc_type: apiPageType
---

# Get externalOriginResourceConnector

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Read the properties and relationships of [externalOriginResourceConnector](../resources/externaloriginresourceconnector.md) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "externaloriginresourceconnector-get-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/externaloriginresourceconnector-get-permissions.md)]

[!INCLUDE [rbac-entitlement-identity-governance-admin-apis-read](../includes/rbac-for-apis/rbac-entitlement-identity-governance-admin-apis-read.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /identityGovernance/entitlementManagement/accessPackageCatalogs/{accessPackageCatalogId}/accessPackageResources/{accessPackageResourceId}/externalOriginResourceConnector
```

## Optional query parameters

This method supports the `$select` OData query parameter to help customize the response. For general information, see [OData query parameters](/graph/query-parameters).

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and an [externalOriginResourceConnector](../resources/externaloriginresourceconnector.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "get_externaloriginresourceconnector"
}
-->
``` http
GET https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageCatalogs/06a6415b-2f20-44ce-b43e-ae9570f26fa2/accessPackageResources/cedee304-3210-4da3-ba5c-2f3adb400efc/externalOriginResourceConnector
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.externalOriginResourceConnector"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/entitlementManagement/externalOriginResourceConnector/$entity",
  "@odata.type": "#microsoft.graph.externalOriginResourceConnector",
  "id": "06a6415b-2f20-44ce-b43e-ae9570f26fa2",
  "displayName": "SAP Access Control",
  "description": "SAP Access  Control test",
  "connectorType": "sapAc",
  "connectionInfo": {
    "@odata.type": "microsoft.graph.externalTokenBasedSapIagConnectionInfo"
  },
  "createdBy": "kayat@igaelmdev.com",
  "createdDateTime": "2025-11-29T17:45:40Z",
  "modifiedBy": "kayat@igaelmdev.com",
  "modifiedDateTime": "2025-12-001T10:23:10Z"
}
```
