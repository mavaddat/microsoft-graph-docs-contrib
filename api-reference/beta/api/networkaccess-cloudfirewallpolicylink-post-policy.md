---
title: "Create cloudFirewallPolicyLink"
description: "Create a new cloudFirewallPolicyLink for a filtering profile."
author: "shkhalid"
ms.date: 01/26/2026
ms.localizationpriority: medium
ms.subservice: "entra-global-secure-access"
doc_type: apiPageType
---

# Create cloudFirewallPolicyLink

Namespace: microsoft.graph.networkaccess

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Create a new [cloudFirewallPolicyLink](../resources/networkaccess-cloudfirewallpolicylink.md) for a [filteringProfile](../resources/networkaccess-filteringprofile.md).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "networkaccess-cloudfirewallpolicylink-post-policy-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/networkaccess-cloudfirewallpolicylink-post-policy-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /networkAccess/filteringProfiles/{filteringProfileId}/policies
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

In the request body, supply a JSON representation of the [cloudFirewallPolicyLink](../resources/networkaccess-cloudfirewallpolicylink.md) object.

You can specify the following properties when creating a **cloudFirewallPolicyLink**.

|Property|Type|Description|
|:---|:---|:---|
|state|microsoft.graph.networkaccess.status|The current state of the policy link. The possible values are: `enabled`, `disabled`. Required.|

You must also supply a reference to the cloud firewall policy to link using `policy@odata.bind`.

## Response

If successful, this method returns a `201 Created` response code and a [cloudFirewallPolicyLink](../resources/networkaccess-cloudfirewallpolicylink.md) object in the response body.

## Examples

### Request

The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "create_cloudfirewallpolicylink"
}
-->
``` http
POST https://graph.microsoft.com/beta/networkAccess/filteringProfiles/519085fd-efb2-437c-af22-04bff0c2b571/policies
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallPolicyLink",
  "state": "enabled",
  "policy@odata.bind": "https://graph.microsoft.com/beta/networkAccess/cloudFirewallPolicies/b5cd1ab8-6e3c-4a80-96d7-ef0d3381d4cc"
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
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallPolicyLink",
  "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
  "state": "enabled",
  "version": "1.0.0"
}
```
