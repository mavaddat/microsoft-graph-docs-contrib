---
title: "Create governanceInvitation"
description: "Create a new governance invitation to establish a relationship with a governed tenant."
author: "hafowler"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: apiPageType
---

# Create governanceInvitation

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Create a new [governanceInvitation](../resources/tenantgovernance-governanceinvitation.md) to establish a governance relationship with a governed tenant. Invitations provide an alternative mechanism to governance requests for initiating relationships.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "tenantgovernanceservices-tenantgovernance-post-governanceinvitations-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/tenantgovernance-post-governanceinvitations-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /directory/tenantGovernance/governanceInvitations
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.tenantGovernanceServices.governanceInvitation](../resources/tenantgovernance-governanceinvitation.md) object.

You can specify the following properties when creating a **governanceInvitation**.

|Property|Type|Description|
|:---|:---|:---|
|governingTenantId|String|The Microsoft Entra tenant ID of the governing tenant. Required.|



## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.tenantGovernanceServices.governanceInvitation](../resources/tenantgovernance-governanceinvitation.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "create_governanceinvitation"
}
-->
``` http
POST https://graph.microsoft.com/beta/directory/tenantGovernance/governanceInvitations
Content-Type: application/json

{
  "governingTenantId": "String"
}
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.tenantGovernanceServices.governanceInvitation"
}
-->
``` http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.governanceInvitation",
  "id": "502f457f-4db7-9ea5-4c16-fae1807b3be2",
  "governingTenantId": "String",
  "governedTenantId": "String",
  "governingTenantName": "String",
  "governedTenantName": "String",
  "createdDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)"
}
```

