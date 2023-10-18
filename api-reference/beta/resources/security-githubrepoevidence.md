---
title: "gitHubRepoEvidence resource type"
description: "Represents a repository in GitHub."
author: "MSLironLevy"
ms.localizationpriority: medium
ms.prod: "security"
doc_type: resourcePageType
---

# gitHubRepoEvidence resource type

Namespace: microsoft.graph.security

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents a repository in GitHub.

Inherits from [alertEvidence](../resources/security-alertevidence.md).

## Properties

| Property  | Type   | Description                                                          |
|:----------|:-------|:---------------------------------------------------------------------|
| repoId    | String | The unique and immutable id of the GitHub repository.                |
| login     | String | The login (aka name) of the repository.                              |
| owner     | String | The login of the owner of the repository.                            |
| ownerType | String | The type of owner of the repository (e.g. “User” or ‘Organization"). |
| baseUrl   | String | The base URL of the repository's web page.                           |

## Relationships

None.

## JSON representation

The following is a JSON representation of the resource.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.security.gitHubRepoEvidence"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.security.gitHubRepoEvidence",
  "repoId": "String",
  "login": "String",
  "owner": "String",
  "ownerType": "String",
  "baseUrl": "String"
}
```