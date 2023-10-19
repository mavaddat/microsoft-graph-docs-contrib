---
title: "nicEvidence resource type"
description: "Represents a NIC (v2) entity reported as part of a security detection alert."
author: "MSLironLevy"
ms.localizationpriority: medium
ms.prod: "security"
doc_type: resourcePageType
---

# nicEvidence resource type

Namespace: microsoft.graph.security

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents a NIC (v2) entity that is reported as part of the security detection alert.

Inherits from [alertEvidence](../resources/security-alertevidence.md).

## Properties

| Property   | Type                                                            | Description                    |
|:-----------|:----------------------------------------------------------------|:-------------------------------|
| macAddress | String                                                          | The MAC for the NIC.           |
| ipAddress  | [microsoft.graph.security.ipEvidence](./security-ipevidence.md) | The current IP for the NIC.    |
| vlans      | String Collection                                               | The current VLANs for the NIC. |

## Relationships

None.

## JSON representation

The following is a JSON representation of the resource.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.security.nicEvidence"
}
-->

``` json
{
  "@odata.type": "#microsoft.graph.security.nicEvidence",
  "macAddress": "String",
  "ipAddress": {
      "@odata.type": "microsoft.graph.security.ipEvidence"
   },
  "vlans": ["String"]
}
```