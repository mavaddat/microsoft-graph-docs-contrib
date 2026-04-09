---
title: "List inherited app role assignments for an agent identity"
description: "Retrieve the application role assignments (appRoleAssignment objects) that an agent identity inherits from its parent Agent Identity Blueprint Service Principal."
author: "mvoznyarskiy"
ms.date: 04/08/2026
ms.localizationpriority: medium
ms.subservice: "entra-agent-id"
doc_type: apiPageType
---

# List inherited app role assignments for an agent identity

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Retrieve the application role assignments ([appRoleAssignment](../resources/approleassignment.md) objects) that an [agent identity](../resources/agentidentity.md) inherits from its parent Agent Identity Blueprint Service Principal. These inherited assignments are computed at runtime and represent the effective application-level permissions as applied by ESTS when issuing tokens.

## Key behaviors

- The `principalId` on each returned assignment is set to the agent identity's service principal ID, not the parent ABSP ID.
- The `principalType` is always `ServicePrincipal`.
- The `id` of each inherited assignment matches the `id` of the original assignment on the parent ABSP, enabling correlation.
- The `createdDateTime` reflects the creation time of the original assignment on the parent ABSP.
- All other properties (`appRoleId`, `principalDisplayName`, `resourceDisplayName`, `resourceId`) are copied from the parent ABSP assignment.
- The inherited collection is strictly read-only. POST, PATCH, and DELETE requests return `405 Method Not Allowed`. To modify inherited assignments, update the parent ABSP's `appRoleAssignments` instead.
- Pagination isn't supported. All results are returned in a single response, capped at 1,000 items.
- Calling this method on a service principal that isn't an agent identity returns `404 Not Found`.
- The `AgentIdentity.CreateAsManager` and `AgentIdUser.ReadWrite.IdentityParentedBy` roles are excluded from inheritance per ESTS runtime rules.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "agentidentity-list-inheritedapproleassignments-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/agentidentity-list-inheritedapproleassignments-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /servicePrincipals/{agentIdentity-id}/inheritedAppRoleAssignments
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

If successful, this method returns a `200 OK` response code and a collection of [appRoleAssignment](../resources/approleassignment.md) objects in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "list_inheritedapproleassignment"
}
-->
``` http
GET https://graph.microsoft.com/beta/servicePrincipals/00001111-aaaa-2222-bbbb-3333cccc4444/inheritedAppRoleAssignments
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "Collection(microsoft.graph.appRoleAssignment)"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#appRoleAssignments",
  "value": [
    {
      "id": "aabbccdd-1122-3344-5566-778899001122",
      "createdDateTime": "2026-01-15T10:30:00Z",
      "appRoleId": "11112222-aaaa-3333-bbbb-4444cccc5555",
      "principalDisplayName": "My Agent Identity",
      "principalId": "00001111-aaaa-2222-bbbb-3333cccc4444",
      "principalType": "ServicePrincipal",
      "resourceDisplayName": "Microsoft Graph",
      "resourceId": "aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee"
    },
    {
      "id": "eeff0011-2233-4455-6677-889900aabbcc",
      "createdDateTime": "2026-02-01T14:00:00Z",
      "appRoleId": "66667777-aaaa-8888-bbbb-9999cccc0000",
      "principalDisplayName": "My Agent Identity",
      "principalId": "00001111-aaaa-2222-bbbb-3333cccc4444",
      "principalType": "ServicePrincipal",
      "resourceDisplayName": "SharePoint Online",
      "resourceId": "bbbbbbbb-cccc-dddd-eeee-ffffffffffff"
    }
  ]
}
```

