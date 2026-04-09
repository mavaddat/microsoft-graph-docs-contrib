---
title: "List inherited OAuth2 permission grants for an agent identity"
description: "Retrieve the delegated permission grants (oAuth2PermissionGrant objects) that an agent identity inherits from its parent Agent Identity Blueprint Service Principal."
author: "mvoznyarskiy"
ms.date: 04/08/2026
ms.localizationpriority: medium
ms.subservice: "entra-agent-id"
doc_type: apiPageType
---

# List inherited OAuth2 permission grants for an agent identity

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Retrieve the delegated permission grants ([oAuth2PermissionGrant](../resources/oauth2permissiongrant.md) objects) that an [agent identity](../resources/agentidentity.md) inherits from its parent Agent Identity Blueprint Service Principal. These inherited grants are computed at runtime and represent the effective delegated permissions as applied by ESTS when issuing tokens.

This method returns only inherited grants of `consentType` **AllPrincipals** (tenant-wide, admin-consented grants). Grants of `consentType` **Principal** (user-specific grants) aren't returned by this method.

## Key behaviors

- The `clientId` on each returned grant is set to the agent identity's service principal ID, not the parent ABSP ID.
- The `id` of each inherited grant matches the `id` of the original grant on the parent ABSP, enabling correlation.
- All other properties (`consentType`, `principalId`, `resourceId`, `scope`) are copied from the parent ABSP grant.
- The inherited collection is strictly read-only. POST, PATCH, and DELETE requests return `405 Method Not Allowed`. To modify inherited grants, update the parent ABSP's `oauth2PermissionGrants` instead.
- Pagination isn't supported. All results are returned in a single response, capped at 1,000 items.
- Calling this method on a service principal that isn't an agent identity returns `404 Not Found`.
- The `Directory.ReadWrite.All` scope is excluded from inheritance per ESTS runtime rules.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "agentidentity-list-inheritedoauth2permissiongrants-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/agentidentity-list-inheritedoauth2permissiongrants-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /servicePrincipals/{agentIdentity-id}/inheritedOauth2PermissionGrants
```

## Optional query parameters

This method doesn't support OData query parameters. The `$filter`, `$top`, `$skip`, `$count`, `$orderBy`, `$expand`, and `$select` query parameters aren't supported.

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [oAuth2PermissionGrant](../resources/oauth2permissiongrant.md) objects in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "list_inheritedoauth2permissiongrant"
}
-->
``` http
GET https://graph.microsoft.com/beta/servicePrincipals/00001111-aaaa-2222-bbbb-3333cccc4444/inheritedOauth2PermissionGrants
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "Collection(microsoft.graph.oAuth2PermissionGrant)"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#oAuth2PermissionGrants",
  "value": [
    {
      "id": "abc123def456",
      "clientId": "00001111-aaaa-2222-bbbb-3333cccc4444",
      "consentType": "AllPrincipals",
      "principalId": null,
      "resourceId": "aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee",
      "scope": "User.Read Mail.Read"
    }
  ]
}
```

