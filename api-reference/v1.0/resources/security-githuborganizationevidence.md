---
title: "gitHubOrganizationEvidence resource type"
description: "Represents an organization in GitHub."
author: "Lirlev48"
ms.localizationpriority: medium
ms.subservice: "security"
doc_type: resourcePageType
---

# gitHubOrganizationEvidence resource type

Namespace: microsoft.graph.security

Represents an organization in GitHub.

Inherits from [alertEvidence](../resources/security-alertevidence.md).

## Properties

|Property|Type|Description|
|:------------|:-------|:----------------------------------------------------|
|orgId|String|The unique and immutable ID of the organization.|
|login|String|The login (name) of the organization.|
|email|String|The email address of the organization.|
|displayName|String|The display name of the organization.|
|company|String|The name of the company that owns the organization.|
|webUrl|String|The URL of the organization's web page|

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.security.gitHubOrganizationEvidence"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.security.gitHubOrganizationEvidence",
  "orgId": "String",
  "login": "String",
  "email": "String",
  "displayName": "String",
  "company": "String",
  "webUrl": "String"
}

```