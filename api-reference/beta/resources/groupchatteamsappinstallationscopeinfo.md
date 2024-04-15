---
title: "groupChatTeamsAppInstallationScopeInfo resource type"
description: "Chat installation scope details for Teams app."
author: "sthapliyal"
ms.localizationpriority: medium
ms.subservice: "teams"
doc_type: resourcePageType
---

# groupChatTeamsAppInstallationScopeInfo resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

The details of the installation scope when Teams app is installed in chat.

Inherits from [teamsAppInstallationScopeInfo](../resources/teamsappinstallationscopeinfo.md).

## Properties
|Property|Type|Description|
|:---|:---|:---|
|chatId|String|Chat Id in of the chat in which Teams app is installed.|
|scope|teamsAppInstallationScopes|The scope in which Teams app has been installed. Inherited from [teamsAppInstallationScopeInfo](../resources/teamsappinstallationscopeinfo.md).The possible values are: `team`, `groupChat`, `personal`, `unknownFutureValue`.|

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.groupChatTeamsAppInstallationScopeInfo"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.groupChatTeamsAppInstallationScopeInfo",
  "scope": "String",
  "chatId": "String"
}
```
