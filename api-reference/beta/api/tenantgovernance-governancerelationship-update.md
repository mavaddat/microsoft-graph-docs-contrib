---
title: "Update governanceRelationship"
description: "Update the status property to initiate termination of a governance relationship."
author: "hafowler"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: apiPageType
---

# Update governanceRelationship

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Update the **status** property of a [governanceRelationship](../resources/tenantgovernance-governancerelationship.md) to initiate the termination process. 

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "tenantgovernanceservices-governancerelationship-update-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/tenantgovernance-governancerelationship-update-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
PATCH /directory/tenantGovernance/governanceRelationships/{governanceRelationshipId}
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
|status|microsoft.graph.tenantGovernanceServices.relationshipStatus|The current status of the governance relationship. The possible values are: `active`, `terminated`, `terminationRequestedByGoverningTenant`, `unknownFutureValue`. Required.|

## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.tenantGovernanceServices.governanceRelationship](../resources/tenantgovernance-governancerelationship.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "update_governancerelationship"
}
-->
``` http
PATCH https://graph.microsoft.com/beta/directory/tenantGovernance/governanceRelationships/{governanceRelationshipId}
Content-Type: application/json

{
  "status": "String",
}
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
```

