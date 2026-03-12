---
title: "Get governanceInvitation"
description: "Read the properties of a governance invitation."
author: "hafowler"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: apiPageType
---

# Get governanceInvitation

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Read the properties of a [governanceInvitation](../resources/tenantgovernance-governanceinvitation.md) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "tenantgovernanceservices-governanceinvitation-get-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/tenantgovernance-governanceinvitation-get-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /directory/tenantGovernance/governanceInvitations/{governanceInvitationId}
```

## Optional query parameters

This method doesn't support OData query parameters to help customize the response. For general information, see [OData query parameters](/graph/query-parameters).

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.tenantGovernanceServices.governanceInvitation](../resources/tenantgovernance-governanceinvitation.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "get_governanceinvitation"
}
-->
``` http
GET https://graph.microsoft.com/beta/directory/tenantGovernance/governanceInvitations/{governanceInvitationId}
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
HTTP/1.1 200 OK
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

