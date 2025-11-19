---
title: "externalOriginResourceConnector resource type"
description: "**TODO: Add Description**"
author: "**TODO: Provide GitHub Name. See [topic-level metadata reference](https://eng.ms/docs/products/microsoft-graph-service/microsoft-graph/document-apis/metadata)**"
ms.date: 11/11/2025
ms.localizationpriority: medium
ms.subservice: "**TODO: Add MS subservice. See [topic-level metadata reference](https://eng.ms/docs/products/microsoft-graph-service/microsoft-graph/document-apis/metadata)**"
doc_type: resourcePageType
---

# externalOriginResourceConnector resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

**TODO: Add Description**


Inherits from [entity](../resources/entity.md).


## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[List](../api/customdataprovidedresource-list-externaloriginresourceconnector.md)|[externalOriginResourceConnector](../resources/externaloriginresourceconnector.md) collection|Get a list of the externalOriginResourceConnector objects and their properties.|
|[Create](../api/customdataprovidedresource-post-externaloriginresourceconnector.md)|[externalOriginResourceConnector](../resources/externaloriginresourceconnector.md)|Create a new externalOriginResourceConnector object.|
|[Get](../api/externaloriginresourceconnector-get.md)|[externalOriginResourceConnector](../resources/externaloriginresourceconnector.md)|Read the properties and relationships of [externalOriginResourceConnector](../resources/externaloriginresourceconnector.md) object.|
|[Update](../api/externaloriginresourceconnector-update.md)|[externalOriginResourceConnector](../resources/externaloriginresourceconnector.md)|Update the properties of an externalOriginResourceConnector object.|
|[Delete](../api/customdataprovidedresource-delete-externaloriginresourceconnector.md)|None|Delete an externalOriginResourceConnector object.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|connectionInfo|[connectionInfo](../resources/connectioninfo.md)|**TODO: Add Description**|
|connectorType|connectorType|**TODO: Add Description**. The possible values are: `sapIag`, `sapAc`, `unknownFutureValue`.|
|createdBy|String|**TODO: Add Description**|
|createdDateTime|DateTimeOffset|**TODO: Add Description**|
|description|String|**TODO: Add Description**|
|displayName|String|**TODO: Add Description**|
|id|String|**TODO: Add Description** Inherited from [entity](../resources/entity.md). Inherits from [entity](../resources/entity.md)|
|modifiedBy|String|**TODO: Add Description**|
|modifiedDateTime|DateTimeOffset|**TODO: Add Description**|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.externalOriginResourceConnector",
  "baseType": "microsoft.graph.entity",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.externalOriginResourceConnector",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "connectorType": "String",
  "connectionInfo": {
    "@odata.type": "microsoft.graph.connectionInfo"
  },
  "createdBy": "String",
  "createdDateTime": "String (timestamp)",
  "modifiedBy": "String",
  "modifiedDateTime": "String (timestamp)"
}
```

