---
title: "Create governanceRequest"
description: "Create a new governance request to establish a relationship with a governed tenant."
author: "hafowler"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: apiPageType
---

# Create governanceRequest

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Create a new [governanceRequest](../resources/tenantgovernance-governancerequest.md) to establish a governance relationship with a governed tenant. The governed tenant can then accept or reject the request.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "tenantgovernanceservices-tenantgovernance-post-governancerequests-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/tenantgovernance-post-governancerequests-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /directory/tenantGovernance/governanceRequests
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.tenantGovernanceServices.governanceRequest](../resources/tenantgovernance-governancerequest.md) object.

You can specify the following properties when creating a **governanceRequest**.

|Property|Type|Description|
|:---|:---|:---|
|governedTenantId|String|The Microsoft Entra tenant ID of the governed tenant. Required.|
|policySnapshot|[microsoft.graph.tenantGovernanceServices.relationshipPolicy](../resources/tenantgovernance-relationshippolicy.md)|Provide the governance policy template id that will be used to generated the policySnapshot. Required.|



## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.tenantGovernanceServices.governanceRequest](../resources/tenantgovernance-governancerequest.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "create_governancerequest_from_"
}
-->
``` http
POST https://graph.microsoft.com/beta/directory/tenantGovernance/governanceRequests
Content-Type: application/json

{
  "governedTenantId": "String",
  "governancePolicyTemplate@odata.bind": {
    "https://graph.microsoft.com/beta/directory/tenantGovernance/governancePolicyTemplates/<id>"
  }
}
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.tenantGovernanceServices.governanceRequest"
}
-->
``` http
HTTP/1.1 201 Created
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

