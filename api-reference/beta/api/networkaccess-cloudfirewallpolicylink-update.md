---
title: "Update cloudFirewallPolicyLink"
description: "Update the properties of a cloudFirewallPolicyLink object."
author: "shkhalid"
ms.date: 01/26/2026
ms.localizationpriority: medium
ms.subservice: "entra-global-secure-access"
doc_type: apiPageType
---

# Update cloudFirewallPolicyLink

Namespace: microsoft.graph.networkaccess

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Update the properties of a [cloudFirewallPolicyLink](../resources/networkaccess-cloudfirewallpolicylink.md) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "networkaccess-cloudfirewallpolicylink-update-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/networkaccess-cloudfirewallpolicylink-update-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
PATCH /networkAccess/filteringProfiles/{filteringProfileId}/policies/{policyLinkId}
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
|state|microsoft.graph.networkaccess.status|The current state of the policy link. The possible values are: `enabled`, `disabled`. Optional.|

## Response

If successful, this method returns a `200 OK` response code and an updated [cloudFirewallPolicyLink](../resources/networkaccess-cloudfirewallpolicylink.md) object in the response body.

## Examples

### Request

The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "update_cloudfirewallpolicylink"
}
-->
``` http
PATCH https://graph.microsoft.com/beta/networkAccess/filteringProfiles/519085fd-efb2-437c-af22-04bff0c2b571/policies/a1b2c3d4-e5f6-7890-abcd-ef1234567890
Content-Type: application/json

{
  "state": "disabled"
}
```

### Response

The following example shows the response.

>**Note:** The response object shown here might be shortened for readability.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.networkaccess.cloudFirewallPolicyLink"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallPolicyLink",
  "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
  "state": "disabled",
  "version": "1.0.0"
}
```
