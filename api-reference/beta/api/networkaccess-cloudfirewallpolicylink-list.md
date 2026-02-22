---
title: "List cloudFirewallPolicyLink objects"
description: "Get a list of the cloudFirewallPolicyLink objects and their properties."
author: "shkhalid"
ms.date: 01/26/2026
ms.localizationpriority: medium
ms.subservice: "entra-global-secure-access"
doc_type: apiPageType
---

# List cloudFirewallPolicyLink objects

Namespace: microsoft.graph.networkaccess

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get a list of the [cloudFirewallPolicyLink](../resources/networkaccess-cloudfirewallpolicylink.md) objects and their properties.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "networkaccess-cloudfirewallpolicylink-list-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/networkaccess-cloudfirewallpolicylink-list-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /networkAccess/filteringProfiles/{filteringProfileId}/policies
```

## Optional query parameters

This method supports the `$select`, `$top`, `$expand`, and `$filter` OData query parameters to help customize the response. For general information, see [OData query parameters](/graph/query-parameters).

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [cloudFirewallPolicyLink](../resources/networkaccess-cloudfirewallpolicylink.md) objects in the response body.

## Examples

### Request

The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "list_cloudfirewallpolicylink"
}
-->
``` http
GET https://graph.microsoft.com/beta/networkAccess/filteringProfiles/519085fd-efb2-437c-af22-04bff0c2b571/policies
```

### Response

The following example shows the response.

>**Note:** The response object shown here might be shortened for readability.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "Collection(microsoft.graph.networkaccess.cloudFirewallPolicyLink)"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallPolicyLink",
      "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
      "state": "enabled",
      "version": "1.0.0"
    }
  ]
}
```
