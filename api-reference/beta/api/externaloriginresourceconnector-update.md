---
title: "Update externalOriginResourceConnector"
description: "Update the properties of an externalOriginResourceConnector object."
author: "vikama-microsoft"
ms.date: 11/11/2025
ms.localizationpriority: medium
ms.subservice: "entra-id-governance"
doc_type: apiPageType
---

# Update externalOriginResourceConnector

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Update the properties of an externalOriginResourceConnector object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "externaloriginresourceconnector-update-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/externaloriginresourceconnector-update-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
PATCH /identityGovernance/entitlementManagement/accessPackageCatalogs/{accessPackageCatalogId}/accessPackageResources/{accessPackageResourceId}/externalOriginResourceConnector
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

[!INCLUDE [table-intro](../../includes/update-property-table-intro.md)]


|Property|Type|Description|
|:---|:---|:---|
|displayName|String|The display name of the connector. Optional.|
|description|String|A description of the connector. Optional.|
|connectorType|connectorType|The type of connector. The possible values are: `sapIag`, `sapAc`, `unknownFutureValue`. Optional.|
|connectionInfo|[connectionInfo](../resources/connectioninfo.md)|The connection information used to communicate with the external resource system. Optional.|



## Response

If successful, this method returns a `200 OK` response code and an updated [externalOriginResourceConnector](../resources/externaloriginresourceconnector.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "update_externaloriginresourceconnector"
}
-->
``` http
PATCH https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageCatalogs/{accessPackageCatalogId}/accessPackageResources/{accessPackageResourceId}/externalOriginResourceConnector
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.externalOriginResourceConnector",
  "displayName": "String",
  "description": "String",
  "connectorType": "String",
  "connectionInfo": {
    "@odata.type": "microsoft.graph.connectionInfo"
  }
}
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
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.externalOriginResourceConnector",
  "id": "9a0f91bb-5937-2801-383e-5946f51c5f46",
  "displayName": "String",
  "description": "String",
  "connectorType": "String",
  "connectionInfo": {
    "@odata.type": "microsoft.graph.connectionInfo"
  },
  "createdBy": "String",
  "createdDateTime": "String (timestamp)",
  "modifiedBy": "String",
  "modifiedDateTime": "String (timestamp)"
}
```

