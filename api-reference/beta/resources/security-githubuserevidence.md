---
title: "gitHubUserEvidence resource type"
description: "Represents a user account in GitHub."
author: "Lirlev48"
ms.localizationpriority: medium
ms.subservice: "security"
doc_type: resourcePageType
ms.date: 05/07/2026
---

# gitHubUserEvidence resource type

Namespace: microsoft.graph.security

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents a user account in GitHub.

Inherits from [alertEvidence](../resources/security-alertevidence.md).

## Properties

|Property|Type|Description|
|:---------|:-------|:----------------------------------------------------------------------------------|
|userId|String|The unique and immutable ID of the user account.|
|login|String|User's login (GitHub handle).|
|email|String|The email address of the user account.|
|name|String|User's name.|
|webUrl|String|The URL of the user's profile web page, for example "https://github.com/my-login".|

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.security.gitHubUserEvidence"
}
-->

``` json
{
  "@odata.type": "#microsoft.graph.security.gitHubUserEvidence",
  "userId": "String",
  "login": "String",
  "email": "String",
  "name": "String",
  "webUrl": "String"
}
```