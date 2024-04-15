---
title: "personalTeamsAppInstallationScopeInfo resource type"
description: "Personal scope installation details for Teams app."
author: "sthapliyal"
ms.localizationpriority: medium
ms.subservice: "teams"
doc_type: resourcePageType
---

# personalTeamsAppInstallationScopeInfo resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

The details of the installation scope when Teams app is installed for a user.

Inherits from [teamsAppInstallationScopeInfo](../resources/teamsappinstallationscopeinfo.md).

## Properties
|Property|Type|Description|
|:---|:---|:---|
|scope|teamsAppInstallationScopes|The scope in which Teams app has been installed. Inherited from [teamsAppInstallationScopeInfo](../resources/teamsappinstallationscopeinfo.md).The possible values are: `team`, `groupChat`, `personal`, `unknownFutureValue`.|
|userId|String|The user id of the user for which Teams app has been installed.|

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.personalTeamsAppInstallationScopeInfo"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.personalTeamsAppInstallationScopeInfo",
  "scope": "String",
  "userId": "String"
}
```