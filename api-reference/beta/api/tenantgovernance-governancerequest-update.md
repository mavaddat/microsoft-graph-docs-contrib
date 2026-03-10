---
title: "Update governanceRequest"
description: "Update the status property to accept or reject a governance request."
author: "hafowler"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: apiPageType
---

# Update governanceRequest

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Update the **status** property of a [governanceRequest](../resources/tenantgovernance-governancerequest.md) to accept or reject the governance request. Only the governed tenant can update the request status.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "tenantgovernanceservices-governancerequest-update-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/tenantgovernance-governancerequest-update-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
PATCH /directory/tenantGovernance/governanceRequests/{governanceRequestId}
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

[!INCLUDE [table-intro](../../includes/update-property-table-intro.md)]


**TODO: Remove properties that don't apply**
|Property|Type|Description|
|:---|:---|:---|
|governingTenantId|String|**TODO: Add Description** Required.|
|governingTenantName|String|**TODO: Add Description** Required.|
|governedTenantId|String|**TODO: Add Description** Required.|
|governedTenantName|String|**TODO: Add Description** Required.|
|policySnapshot|[microsoft.graph.tenantGovernanceServices.relationshipPolicy](../resources/tenantgovernance-relationshippolicy.md)|**TODO: Add Description** Required.|
|status|microsoft.graph.tenantGovernanceServices.requestStatus|**TODO: Add Description**. The possible values are: `pending`, `accepted`, `rejected`, `unknownFutureValue`. Required.|
|requestDateTime|DateTimeOffset|**TODO: Add Description** Required.|
|expirationDateTime|DateTimeOffset|**TODO: Add Description** Required.|



## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.tenantGovernanceServices.governanceRequest](../resources/tenantgovernance-governancerequest.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "update_governancerequest"
}
-->
``` http
PATCH https://graph.microsoft.com/beta/directory/tenantGovernance/governanceRequests/{governanceRequestId}
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.governanceRequest",
  "governingTenantId": "String",
  "governingTenantName": "String",
  "governedTenantId": "String",
  "governedTenantName": "String",
  "policySnapshot": {
    "@odata.type": "microsoft.graph.tenantGovernanceServices.relationshipPolicy"
  },
  "status": "String",
  "requestDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)"
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
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.governanceRequest",
  "id": "e8981861-afa6-2fe8-f46a-b3ef379f955e",
  "governingTenantId": "String",
  "governingTenantName": "String",
  "governedTenantId": "String",
  "governedTenantName": "String",
  "policySnapshot": {
    "@odata.type": "microsoft.graph.tenantGovernanceServices.relationshipPolicy"
  },
  "status": "String",
  "requestDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)"
}
```

