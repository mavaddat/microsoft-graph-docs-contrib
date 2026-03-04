---
title: "identityGovernanceUserSettings resource type"
description: "Represents identity governance settings for a user, including the approver delegate configuration."
author: "lnalepa"
ms.localizationpriority: medium
ms.subservice: "entra-id-governance"
doc_type: resourcePageType
ms.date: 03/03/2026
---

# identityGovernanceUserSettings resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents identity governance settings for a user, including the approver delegate configuration. This resource is accessed via the `identityGovernance` property on the [user](user.md) resource.

<!-- ## Methods

| Method | Return type | Description |
|:-------|:------------|:------------|
| [Get approverDelegate](../api/identitygovernanceusersettings-get-approverdelegate.md) | [approverDelegate](approverdelegate.md) | Retrieve the approver delegate information for a user. |
| [Set approverDelegate](../api/identitygovernanceusersettings-put-approverdelegate.md) | None | Set or replace the approver delegate for a user. |
| [Delete approverDelegate](../api/identitygovernanceusersettings-delete-approverdelegate.md) | None | Remove the approver delegate for a user. | -->

## Properties

| Property | Type | Description |
|:---------|:-----|:------------|
| approverDelegate | [approverDelegate](approverdelegate.md) | The approver delegate configuration for the user, including the delegate identity and delegation schedule. Nullable. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.identityGovernanceUserSettings"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.identityGovernanceUserSettings",
  "approverDelegate": {
    "@odata.type": "microsoft.graph.approverDelegate"
  }
}
```
