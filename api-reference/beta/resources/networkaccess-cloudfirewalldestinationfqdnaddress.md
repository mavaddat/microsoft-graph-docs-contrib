---
title: "cloudFirewallDestinationFqdnAddress resource type"
description: "Specifies destination addresses using fully qualified domain names (FQDNs) for cloud firewall rule matching."
author: "shkhalid"
ms.date: 01/26/2026
ms.localizationpriority: medium
ms.subservice: "entra-global-secure-access"
doc_type: resourcePageType
---

# cloudFirewallDestinationFqdnAddress resource type

Namespace: microsoft.graph.networkaccess

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Specifies destination addresses using fully qualified domain names (FQDNs) for cloud firewall rule matching.

Inherits from [microsoft.graph.networkaccess.cloudFirewallDestinationAddress](../resources/networkaccess-cloudfirewalldestinationaddress.md).

## Properties

|Property|Type|Description|
|:---|:---|:---|
|values|String collection|A collection of FQDNs. Supports wildcards, for example, `*.example.com`. The collection must not be empty. Required.|

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.networkaccess.cloudFirewallDestinationFqdnAddress",
  "baseType": "microsoft.graph.networkaccess.cloudFirewallDestinationAddress"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallDestinationFqdnAddress",
  "values": ["*.example.com", "api.contoso.com"]
}
```
