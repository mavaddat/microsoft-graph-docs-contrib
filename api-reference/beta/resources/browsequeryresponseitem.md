---
title: "browseQueryResponseItem resource type"
description: "Represents the response of the browse API."
author: "manikantsinghms"
ms.date: 09/23/2025
ms.localizationpriority: medium
ms.subservice: "m365-backup-storage"
doc_type: resourcePageType
---

# browseQueryResponseItem resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents the response of the [SharePointBrowse Query](../api/sharepointbrowsesession-browse.md) and [OneDriveForBusinessBrowse Query](../api/onedriveforbusinessbrowsesession-browse.md) APIs.


## Properties
|Property|Type|Description|
|:---|:---|:---|
|itemKey|String|Unique identifier of the returned item.|
|itemsCount|Int32|Count of items presents within the items. e.g, count of files in a folder.|
|name|String|Name of the item.|
|sizeInBytes|String|Size of the item in bytes.|
|type|browseQueryResponseItemType|The type of the item. The possible values are: `none`, `site`, `documentLibrary`, `folder`, `file`, `unknownFutureValue`.|
|webUrl|String|The web url of the item.|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.browseQueryResponseItem"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.browseQueryResponseItem",
  "itemKey": "String",
  "name": "String",
  "webUrl": "String",
  "type": "String",
  "itemsCount": "Integer",
  "sizeInBytes": "String"
}
```

