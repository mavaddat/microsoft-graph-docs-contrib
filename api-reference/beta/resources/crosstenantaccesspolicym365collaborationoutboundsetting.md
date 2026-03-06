---
title: "crossTenantAccessPolicyM365CollaborationOutboundSetting resource type"
description: "Represents the outbound Microsoft 365 collaboration settings for a cross-tenant access policy, defining which users in your organization can collaborate with external organizations using Microsoft 365 apps."
author: "srinivaspadala-msft"
ms.localizationpriority: medium
ms.subservice: "entra-sign-in"
doc_type: resourcePageType
ms.date: 03/06/2026
---

# crossTenantAccessPolicyM365CollaborationOutboundSetting resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents the outbound Microsoft 365 collaboration settings for a cross-tenant access policy, defining which users in your organization can collaborate with external organizations using Microsoft 365 apps.

## Properties

|Property|Type|Description|
|:---|:---|:---|
| usersAndGroups | [crossTenantAccessPolicyTargetConfiguration](../resources/crosstenantaccesspolicytargetconfiguration.md) | Defines the target users and groups in your organization who are allowed outbound Microsoft 365 collaboration with external organizations. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.crossTenantAccessPolicyM365CollaborationOutboundSetting"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.crossTenantAccessPolicyM365CollaborationOutboundSetting",
  "usersAndGroups": {
    "@odata.type": "microsoft.graph.crossTenantAccessPolicyTargetConfiguration"
  }
}
```
