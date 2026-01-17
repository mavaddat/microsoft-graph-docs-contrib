---
title: "onPasswordSubmitListener resource type"
description: "**TODO: Add Description**"
author: "**TODO: Provide GitHub Name. See [topic-level metadata reference](https://eng.ms/docs/products/microsoft-graph-service/microsoft-graph/document-apis/metadata)**"
ms.date: 01/13/2026
ms.localizationpriority: medium
ms.subservice: "**TODO: Add MS subservice. See [topic-level metadata reference](https://eng.ms/docs/products/microsoft-graph-service/microsoft-graph/document-apis/metadata)**"
doc_type: resourcePageType
---

# onPasswordSubmitListener resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

**TODO: Add Description**


Inherits from [authenticationEventListener](../resources/authenticationeventlistener.md).


## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[List](../api/onpasswordsubmitlistener-list.md)|[onPasswordSubmitListener](../resources/onpasswordsubmitlistener.md) collection|Get a list of the onPasswordSubmitListener objects and their properties.|
|[Get](../api/onpasswordsubmitlistener-get.md)|[onPasswordSubmitListener](../resources/onpasswordsubmitlistener.md)|Read the properties and relationships of [onPasswordSubmitListener](../resources/onpasswordsubmitlistener.md) object.|
|[Update](../api/onpasswordsubmitlistener-update.md)|[onPasswordSubmitListener](../resources/onpasswordsubmitlistener.md)|Update the properties of an onPasswordSubmitListener object.|
|[Delete](../api/onpasswordsubmitlistener-delete.md)|None|Delete an onPasswordSubmitListener object.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|authenticationEventsFlowId|String|**TODO: Add Description** Inherited from [authenticationEventListener](../resources/authenticationeventlistener.md).|
|conditions|[authenticationConditions](../resources/authenticationconditions.md)|**TODO: Add Description** Inherited from [authenticationEventListener](../resources/authenticationeventlistener.md).|
|displayName|String|**TODO: Add Description** Inherited from [authenticationEventListener](../resources/authenticationeventlistener.md).|
|handler|[onPasswordSubmitHandler](../resources/onpasswordsubmithandler.md)|**TODO: Add Description**|
|id|String|**TODO: Add Description** Inherited from [entity](../resources/entity.md). Inherits from [entity](../resources/entity.md)|
|priority|Int32|**TODO: Add Description** Inherited from [authenticationEventListener](../resources/authenticationeventlistener.md).|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.onPasswordSubmitListener",
  "baseType": "microsoft.graph.authenticationEventListener",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.onPasswordSubmitListener",
  "id": "String (identifier)",
  "displayName": "String",
  "priority": "Integer",
  "conditions": {
    "@odata.type": "microsoft.graph.authenticationConditions"
  },
  "authenticationEventsFlowId": "String",
  "handler": {
    "@odata.type": "microsoft.graph.onPasswordSubmitHandler"
  }
}
```

