---
author: humbertorMSFT
ms.author: humbertor
ms.date: 11/17/2025
title: SharePointGroupIdentity - OneDrive API
description: "Represents an identity of type SharePointGroup"
---

# SharePointGroupIdentity resource type

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

The **SharePointGroupIdentity** resource represents the identity of a sharePointGroup resource.
It extends from the **sharePointIdentity** resource to provide capability to expose SharePointGroup specific information, for principalId and title.

## JSON representation

<!-- { "blockType": "resource", "@odata.type": "microsoft.graph.sharePointGroupIdentity",
  "openType": true 
} -->

```json
{
  "principalId": "string",
  "title": "string",
  "id": "string"
}
```

## Properties

| Property              | Type                        | Description                      |
|:----------------------|:----------------------------|:---------------------------------|
| title                 | String                      | Title of the sharePointGroup
| principalId           | String                      | The identifier of the Principal corresponding to the sharePointGroup
| id                    | String                      | Unique identifier for the identity.

## Remarks

The "id" property represents the ID field of the relevant sharePointGroup entity.