---
title: "teamTeamsAppInstallationScopeInfo resource type"
description: "Teams scope installation details for Teams app."
author: "sthapliyal"
ms.localizationpriority: medium
ms.subservice: "teams"
doc_type: resourcePageType
---

# teamTeamsAppInstallationScopeInfo resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

The details of the installation scope when Teams app is installed in a Team.

Inherits from [teamsAppInstallationScopeInfo](../resources/teamsappinstallationscopeinfo.md).

## Properties
|Property|Type|Description|
|:---|:---|:---|
|scope|teamsAppInstallationScopes|The scope in which Teams app is installed. Inherited from [teamsAppInstallationScopeInfo](../resources/teamsappinstallationscopeinfo.md).The possible values are: `team`, `groupChat`, `personal`, `unknownFutureValue`.|
|teamId|String|The team id of the team in which Teams app has been installed.|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.teamTeamsAppInstallationScopeInfo"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.teamTeamsAppInstallationScopeInfo",
  "scope": "String",
  "teamId": "String"
}
```
