---
title: "verifiableCredentialsAuthenticationMethodConfiguration resource type"
description: "Represents a Verifiable Credential authentication methods policy."
author: "tilarso"
ms.date: 04/29/2026
ms.localizationpriority: medium
ms.subservice: "entra-sign-in"
doc_type: resourcePageType
---

# verifiableCredentialsAuthenticationMethodConfiguration resource type

Namespace: microsoft.graph

Represents a Verifiable Credential authentication methods policy. Authentication methods policies define configuration settings and users or groups who are enabled to use the authentication method.


Inherits from [authenticationMethodConfiguration](../resources/authenticationmethodconfiguration.md).


## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[Create verifiableCredentialAuthenticationMethodTarget](../api/verifiablecredentialsauthenticationmethodconfiguration-post-includetargets.md)|[verifiableCredentialAuthenticationMethodTarget](../resources/verifiablecredentialauthenticationmethodtarget.md)|Create a new verifiableCredentialAuthenticationMethodTarget object.|
|[Delete](../api/verifiablecredentialsauthenticationmethodconfiguration-delete.md)|None|Delete a verifiableCredentialsAuthenticationMethodConfiguration object.|
|[Delete verifiableCredentialAuthenticationMethodTarget](../api/verifiablecredentialsauthenticationmethodconfiguration-delete-includetargets.md)|None|Delete a verifiableCredentialAuthenticationMethodTarget object.|
|[Get](../api/verifiablecredentialsauthenticationmethodconfiguration-get.md)|[verifiableCredentialsAuthenticationMethodConfiguration](../resources/verifiablecredentialsauthenticationmethodconfiguration.md)|Read the properties and relationships of [verifiableCredentialsAuthenticationMethodConfiguration](../resources/verifiablecredentialsauthenticationmethodconfiguration.md) object.|
|[List](../api/verifiablecredentialsauthenticationmethodconfiguration-list.md)|[verifiableCredentialsAuthenticationMethodConfiguration](../resources/verifiablecredentialsauthenticationmethodconfiguration.md) collection|Get a list of the verifiableCredentialsAuthenticationMethodConfiguration objects and their properties.|
|[List includeTargets](../api/verifiablecredentialsauthenticationmethodconfiguration-list-includetargets.md)|[verifiableCredentialAuthenticationMethodTarget](../resources/verifiablecredentialauthenticationmethodtarget.md) collection|Get a list of the verifiableCredentialAuthenticationMethodTarget objects and their properties.|
|[Update](../api/verifiablecredentialsauthenticationmethodconfiguration-update.md)|[verifiableCredentialsAuthenticationMethodConfiguration](../resources/verifiablecredentialsauthenticationmethodconfiguration.md)|Update the properties of a verifiableCredentialsAuthenticationMethodConfiguration object.|


## Properties
|Property|Type|Description|
|:---|:---|:---|
|excludeTargets|[excludeTarget](../resources/excludetarget.md) collection|Groups of users that are excluded from the policy. Inherited from [authenticationMethodConfiguration](../resources/authenticationmethodconfiguration.md).|
|id|String|The authentication method policy identifier.|
|state|authenticationMethodState|The possible values are: `enabled`, `disabled`. Inherited from [authenticationMethodConfiguration](../resources/authenticationmethodconfiguration.md). The possible values are: `enabled`, `disabled`.|

## Relationships
|Relationship|Type|Description|
|:---|:---|:---|
|includeTargets|[verifiableCredentialAuthenticationMethodTarget](../resources/verifiablecredentialauthenticationmethodtarget.md) collection|A collection of groups that are enabled to use the authentication method.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.verifiableCredentialsAuthenticationMethodConfiguration",
  "baseType": "microsoft.graph.authenticationMethodConfiguration",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.verifiableCredentialsAuthenticationMethodConfiguration",
  "id": "String (identifier)",
  "state": "String",
  "excludeTargets": [
    {
      "@odata.type": "microsoft.graph.excludeTarget"
    }
  ]
}
```

