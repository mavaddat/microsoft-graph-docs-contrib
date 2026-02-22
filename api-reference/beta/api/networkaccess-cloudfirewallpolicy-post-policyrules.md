---
title: "Create cloudFirewallRule"
description: "Create a new cloudFirewallRule object in a cloud firewall policy."
author: "shkhalid"
ms.date: 01/26/2026
ms.localizationpriority: medium
ms.subservice: "entra-global-secure-access"
doc_type: apiPageType
---

# Create cloudFirewallRule

Namespace: microsoft.graph.networkaccess

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Create a new [cloudFirewallRule](../resources/networkaccess-cloudfirewallrule.md) object in a cloud firewall policy.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "networkaccess-cloudfirewallpolicy-post-policyrules-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/networkaccess-cloudfirewallpolicy-post-policyrules-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /networkAccess/cloudFirewallPolicies/{cloudFirewallPolicyId}/policyRules
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

In the request body, supply a JSON representation of the [cloudFirewallRule](../resources/networkaccess-cloudfirewallrule.md) object.

You can specify the following properties when creating a **cloudFirewallRule**.

|Property|Type|Description|
|:---|:---|:---|
|name|String|A unique display name for the rule. Required.|
|description|String|A description of the rule. Optional.|
|priority|Int64|A unique priority value that determines the rule evaluation order. Required.|
|action|[microsoft.graph.networkaccess.cloudFirewallAction](../resources/enums-networkaccess.md#cloudfirewallaction-values)|The action to take when traffic matches the rule. The possible values are: `allow`, `block`, `unknownFutureValue`. Required.|
|settings|[microsoft.graph.networkaccess.cloudFirewallRuleSettings](../resources/networkaccess-cloudfirewallrulesettings.md)|Configuration settings for the rule. Required.|
|matchingConditions|[microsoft.graph.networkaccess.cloudFirewallMatchingConditions](../resources/networkaccess-cloudfirewallmatchingconditions.md)|The conditions that traffic must match for the rule to apply. Required.|

## Response

If successful, this method returns a `201 Created` response code and a [cloudFirewallRule](../resources/networkaccess-cloudfirewallrule.md) object in the response body.

## Examples

### Request

The following example shows a request that creates a rule to block specific traffic. The matching conditions use AND logic between properties (sources AND destinations must match), while items within collections use OR logic (any one address or port can match).

<!-- {
  "blockType": "request",
  "name": "create_cloudfirewallrule"
}
-->
``` http
POST https://graph.microsoft.com/beta/networkAccess/cloudFirewallPolicies/80b58b7d-572f-4457-8944-c804fcf3b694/policyRules
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallRule",
  "name": "Block outbound to risky destinations",
  "description": "Block traffic to specific IPs and FQDNs on common ports",
  "priority": 100,
  "action": "block",
  "settings": {
    "status": "enabled"
  },
  "matchingConditions": {
    "sources": {
      "addresses": [
        {
          "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallSourceIpAddress",
          "values": ["192.168.1.1", "192.168.0.0/16", "172.16.0.0-172.16.255.255"]
        }
      ],
      "ports": ["80", "443", "445-447"]
    },
    "destinations": {
      "addresses": [
        {
          "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallDestinationIpAddress",
          "values": ["10.0.0.1"]
        },
        {
          "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallDestinationFqdnAddress",
          "values": ["*.contoso.com"]
        }
      ],
      "ports": ["80", "443", "445-447"],
      "protocols": "tcp"
    }
  }
}
```

### Response

The following example shows the response.

>**Note:** The response object shown here might be shortened for readability.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.networkaccess.cloudFirewallRule"
}
-->
``` http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallRule",
  "id": "406ebb24-e229-4011-8240-e11bbaa4f49d",
  "name": "Block outbound to risky destinations",
  "description": "Block traffic to specific IPs and FQDNs on common ports",
  "priority": 100,
  "action": "block",
  "settings": {
    "status": "enabled"
  },
  "matchingConditions": {
    "sources": {
      "addresses": [
        {
          "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallSourceIpAddress",
          "values": ["192.168.1.1", "192.168.0.0/16", "172.16.0.0-172.16.255.255"]
        }
      ],
      "ports": ["80", "443", "445-447"]
    },
    "destinations": {
      "addresses": [
        {
          "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallDestinationIpAddress",
          "values": ["10.0.0.1"]
        },
        {
          "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallDestinationFqdnAddress",
          "values": ["*.contoso.com"]
        }
      ],
      "ports": ["80", "443", "445-447"],
      "protocols": "tcp"
    }
  }
}
```
