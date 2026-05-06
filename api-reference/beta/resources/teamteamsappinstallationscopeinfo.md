---
title: "teamTeamsAppInstallationScopeInfo resource type"
description: "Represents the installation scope details when the Teams app is installed in a team."
author: "sthapliyal"
ms.localizationpriority: medium
ms.subservice: "teams"
doc_type: resourcePageType
ms.date: 12/11/2024
---

# teamTeamsAppInstallationScopeInfo resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents the installation scope details when the Teams app is installed in a [team](../resources/team.md).

Inherits from [teamsAppInstallationScopeInfo](../resources/teamsappinstallationscopeinfo.md).

## Properties

|Property|Type|Description|
|:---|:---|:---|
|scope|teamsAppInstallationScopes|The scope in which the Teams app is installed. The possible values are: `team`, `groupChat`, `personal`, `unknownFutureValue`. Inherited from [teamsAppInstallationScopeInfo](../resources/teamsappinstallationscopeinfo.md).|
|teamId|String|The ID of the team where the Teams app is installed.|

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
