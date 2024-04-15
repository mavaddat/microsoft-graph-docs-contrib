---
title: "teamsAppInstallationScopeInfo resource type"
description: "Teams app installation scope details."
author: "sthapliyal"
ms.localizationpriority: medium
ms.subservice: "teams"
doc_type: resourcePageType
---

# teamsAppInstallationScopeInfo resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

The details about the scope in which the Teams app is installed.
This is an abstract type.

## Properties
|Property|Type|Description|
|:---|:---|:---|
|scope|teamsAppInstallationScopes|The scope in which Teams app is installed.The possible values are: `team`, `groupChat`, `personal`, `unknownFutureValue`.|

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.teamsAppInstallationScopeInfo"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.teamsAppInstallationScopeInfo",
  "scope": "String"
}
```
