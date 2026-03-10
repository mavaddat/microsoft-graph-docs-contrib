---
title: "Get governanceRelationship"
description: "Read the properties of a governance relationship."
author: "hafowler"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: apiPageType
---

# Get governanceRelationship

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Read the properties of a [governanceRelationship](../resources/tenantgovernance-governancerelationship.md) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "tenantgovernanceservices-governancerelationship-get-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/tenantgovernance-governancerelationship-get-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /directory/tenantGovernance/governanceRelationships/{governanceRelationshipId}
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

If successful, this method returns a `200 OK` response code and a [microsoft.graph.tenantGovernanceServices.governanceRelationship](../resources/tenantgovernance-governancerelationship.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "get_governancerelationship"
}
-->
``` http
GET https://graph.microsoft.com/beta/directory/tenantGovernance/governanceRelationships/{governanceRelationshipId}
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.tenantGovernanceServices.governanceRelationship"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.tenantGovernanceServices.governanceRelationship",
    "id": "4dc75e3b-731c-9741-d3c6-66eb7620d6fa",
    "governingTenantId": "String",
    "governingTenantName": "String",
    "governedTenantId": "String",
    "governedTenantName": "String",
    "status": "String",
    "policySnapshot": {
      "@odata.type": "microsoft.graph.tenantGovernanceServices.relationshipPolicy"
    },
    "createdType": "String",
    "creationDateTime": "String (timestamp)"
  }
}
```

