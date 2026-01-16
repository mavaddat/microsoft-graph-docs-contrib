---
title: "onPasswordSubmitCustomExtension resource type"
description: "**TODO: Add Description**"
author: "**TODO: Provide GitHub Name. See [topic-level metadata reference](https://eng.ms/docs/products/microsoft-graph-service/microsoft-graph/document-apis/metadata)**"
ms.date: 01/13/2026
ms.localizationpriority: medium
ms.subservice: "**TODO: Add MS subservice. See [topic-level metadata reference](https://eng.ms/docs/products/microsoft-graph-service/microsoft-graph/document-apis/metadata)**"
doc_type: resourcePageType
---

# onPasswordSubmitCustomExtension resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

**TODO: Add Description**


Inherits from [customAuthenticationExtension](../resources/customauthenticationextension.md).


## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[List](../api/onpasswordmigrationcustomextensionhandler-list-customextension.md)|[onPasswordSubmitCustomExtension](../resources/onpasswordsubmitcustomextension.md) collection|Get a list of the onPasswordSubmitCustomExtension objects and their properties.|
|[Create](../api/onpasswordmigrationcustomextensionhandler-post-customextension.md)|[onPasswordSubmitCustomExtension](../resources/onpasswordsubmitcustomextension.md)|Create a new onPasswordSubmitCustomExtension object.|
|[Get](../api/onpasswordsubmitcustomextension-get.md)|[onPasswordSubmitCustomExtension](../resources/onpasswordsubmitcustomextension.md)|Read the properties and relationships of [onPasswordSubmitCustomExtension](../resources/onpasswordsubmitcustomextension.md) object.|
|[Update](../api/onpasswordsubmitcustomextension-update.md)|[onPasswordSubmitCustomExtension](../resources/onpasswordsubmitcustomextension.md)|Update the properties of an onPasswordSubmitCustomExtension object.|
|[Delete](../api/onpasswordmigrationcustomextensionhandler-delete-customextension.md)|None|Delete an onPasswordSubmitCustomExtension object.|
|[validateAuthenticationConfiguration](../api/onpasswordsubmitcustomextension-validateauthenticationconfiguration.md)|[authenticationConfigurationValidation](../resources/authenticationconfigurationvalidation.md)|**TODO: Add Description**|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|authenticationConfiguration|[customExtensionAuthenticationConfiguration](../resources/customextensionauthenticationconfiguration.md)|**TODO: Add Description** Inherited from [customCalloutExtension](../resources/customcalloutextension.md).|
|behaviorOnError|[customExtensionBehaviorOnError](../resources/customextensionbehavioronerror.md)|**TODO: Add Description** Inherited from [customAuthenticationExtension](../resources/customauthenticationextension.md).|
|clientConfiguration|[customExtensionClientConfiguration](../resources/customextensionclientconfiguration.md)|**TODO: Add Description** Inherited from [customCalloutExtension](../resources/customcalloutextension.md).|
|description|String|**TODO: Add Description** Inherited from [customCalloutExtension](../resources/customcalloutextension.md).|
|displayName|String|**TODO: Add Description** Inherited from [customCalloutExtension](../resources/customcalloutextension.md).|
|endpointConfiguration|[customExtensionEndpointConfiguration](../resources/customextensionendpointconfiguration.md)|**TODO: Add Description** Inherited from [customCalloutExtension](../resources/customcalloutextension.md).|
|id|String|**TODO: Add Description** Inherited from [entity](../resources/entity.md). Inherits from [entity](../resources/entity.md)|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.onPasswordSubmitCustomExtension",
  "baseType": "microsoft.graph.customAuthenticationExtension",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.onPasswordSubmitCustomExtension",
  "id": "String (identifier)",
  "authenticationConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionAuthenticationConfiguration"
  },
  "clientConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionClientConfiguration"
  },
  "description": "String",
  "displayName": "String",
  "endpointConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionEndpointConfiguration"
  },
  "behaviorOnError": {
    "@odata.type": "microsoft.graph.customExtensionBehaviorOnError"
  }
}
```

