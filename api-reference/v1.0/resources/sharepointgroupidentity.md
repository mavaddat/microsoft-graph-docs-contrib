---
author: "humbertorMSFT"
ms.author: "humbertor"
ms.date: 11/17/2025
ms.subservice: "onedrive"
doc_type: resourcePageType
title: "sharePointGroupIdentity resource type"
description: "Represents an identity of type sharePointGroup"
---

# sharePointGroupIdentity resource type

Represents the identity of a sharePointGroup resource. It provides capability to expose sharePointGroup specific information, for the principalId and title properties.
It provides capability to expose sharePointGroup specific information, for the principalId and title properties.

## Properties

| Property              | Type                        | Description                      |
|:----------------------|:----------------------------|:---------------------------------|
| title                 | String                      | Title of the sharePointGroup.|
| principalId           | String                      | The identifier of the principal corresponding to the sharePointGroup.|
| id                    | String                      | Unique identifier for the identity. Represents the ID field of the relevant sharePointGroup entity.|

## JSON representation

<!-- { "blockType": "resource", "@odata.type": "microsoft.graph.sharePointGroupIdentity",
  "openType": true 
} -->

```json
{
  "principalId": "string",
  "title": "string",
  "id": "string",
  "@odata.type": "#microsoft.graph.sharePointGroupIdentity"
}
```