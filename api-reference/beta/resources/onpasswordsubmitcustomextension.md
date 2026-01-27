---
title: "onPasswordSubmitCustomExtension resource type"
description: "Custom authentication extension for the OnPasswordSubmit event, used for Just-In-Time migration from legacy authentication providers."
author: "diadabal"
ms.date: 01/13/2026
ms.localizationpriority: medium
ms.subservice: "entra-sign-in"
doc_type: resourcePageType
---

# onPasswordSubmitCustomExtension resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Custom authentication extension for the OnPasswordSubmit event. This extension enables organizations to validate user credentials against legacy authentication systems during the sign-in process, facilitating Just-In-Time (JIT) migration scenarios where passwords cannot be exported from the legacy system.

When a user attempts to sign in, this extension calls a customer-provided API endpoint to validate the password against the legacy system. Upon successful validation, the user's credentials are persisted in Microsoft Entra ID, completing the migration for that user.

Inherits from [customAuthenticationExtension](../resources/customauthenticationextension.md).

## Methods

Custom authentication extensions are managed through the base type endpoint. See [customAuthenticationExtension](../resources/customauthenticationextension.md) for available methods.

|Method|Return type|Description|
|:---|:---|:---|
|[List customAuthenticationExtensions](../api/identitycontainer-list-customauthenticationextensions.md)|[customAuthenticationExtension](../resources/customauthenticationextension.md) collection|Get a list of customAuthenticationExtension objects, including onPasswordSubmitCustomExtension.|
|[Create customAuthenticationExtension](../api/identitycontainer-post-customauthenticationextensions.md)|[customAuthenticationExtension](../resources/customauthenticationextension.md)|Create a new onPasswordSubmitCustomExtension object.|
|[Get customAuthenticationExtension](../api/customauthenticationextension-get.md)|[customAuthenticationExtension](../resources/customauthenticationextension.md)|Read the properties of an onPasswordSubmitCustomExtension object.|
|[Update customAuthenticationExtension](../api/customauthenticationextension-update.md)|None|Update the properties of an onPasswordSubmitCustomExtension object.|
|[Delete customAuthenticationExtension](../api/customauthenticationextension-delete.md)|None|Delete an onPasswordSubmitCustomExtension object.|
|[validateAuthenticationConfiguration](../api/customauthenticationextension-validateauthenticationconfiguration.md)|[authenticationConfigurationValidation](../resources/authenticationconfigurationvalidation.md)|Validate the authentication configuration of the custom extension.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|authenticationConfiguration|[customExtensionAuthenticationConfiguration](../resources/customextensionauthenticationconfiguration.md)|Configuration for securing the API call to the external system. Inherited from [customAuthenticationExtension](../resources/customauthenticationextension.md).|
|behaviorOnError|[customExtensionBehaviorOnError](../resources/customextensionbehavioronerror.md)|Error handling behavior if the external API fails or is unreachable. Inherited from [customAuthenticationExtension](../resources/customauthenticationextension.md).|
|clientConfiguration|[customExtensionClientConfiguration](../resources/customextensionclientconfiguration.md)|HTTP client configuration including timeout and retry settings. Inherited from [customAuthenticationExtension](../resources/customauthenticationextension.md).|
|description|String|Description of the custom authentication extension. Inherited from [customAuthenticationExtension](../resources/customauthenticationextension.md).|
|displayName|String|Display name for the custom authentication extension. Inherited from [customAuthenticationExtension](../resources/customauthenticationextension.md).|
|endpointConfiguration|[customExtensionEndpointConfiguration](../resources/customextensionendpointconfiguration.md)|HTTP endpoint configuration for the external API. Inherited from [customAuthenticationExtension](../resources/customauthenticationextension.md).|
|id|String|Unique identifier for the custom authentication extension. Inherited from [customAuthenticationExtension](../resources/customauthenticationextension.md).|

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
  "displayName": "String",
  "description": "String",
  "endpointConfiguration": {
    "@odata.type": "microsoft.graph.httpRequestEndpoint",
    "targetUrl": "String"
  },
  "authenticationConfiguration": {
    "@odata.type": "microsoft.graph.azureAdTokenAuthentication",
    "resourceId": "String"
  },
  "clientConfiguration": {
    "timeoutInMilliseconds": 1024,
    "maximumRetries": 1024
  },
  "behaviorOnError": {
    "@odata.type": "microsoft.graph.customExtensionBehaviorOnError"
  }
}
```

