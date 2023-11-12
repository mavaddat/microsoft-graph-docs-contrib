---
title: "servicePrincipalEvidence resource type"
description: "Represents a ServicePrincipal reported as part of a security detection alert."
author: "MSLironLevy"
ms.localizationpriority: medium
ms.prod: "security"
doc_type: resourcePageType
---

# servicePrincipalEvidence resource type

Namespace: microsoft.graph.security

Represents a ServicePrincipal that is reported as part of the security detection alert.

Inherits from [alertEvidence](../resources/security-alertevidence.md).

## Properties

| Property                 | Type                                                                          | Description                                                                           |
|:-------------------------|:------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------|
| servicePrincipalName     | String                                                                        | The display name for the service principal.                                           |
| servicePrincipalObjectId | String                                                                        | The unique identifier for the service principal.                                      |
| appId                    | String                                                                        | The unique identifier for the associated application (its appId property).            |
| appOwnerTenantId         | String                                                                        | Contains the tenant id where the application is registered.                           |
| tenantId                 | String                                                                        | The AAD tenant id of Service Principal.                                               |
| servicePrincipalType     | [microsoft.graph.security.servicePrincipalType](#serviceprincipaltype-values) | Type of the service principal: 'Unknown', 'Application', 'ManagedIdentity', 'Legacy'. |

### servicePrincipalType values

| Member             | Description                                                                                                                                                            |
|:-------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| unknown            | Unknown service principal type.                                                                                                                                        |
| application        | This type of service principal represents the local representation, or application instance, of a global application object in a single tenant or directory.           |
| managedIdentity    | This type of service principal is used to represent a managed identity.                                                                                                |
| legacy             | This type of service principal represents a legacy app, which is an app created before app registrations were introduced or an app created through legacy experiences. |
| unknownFutureValue | Evolvable enumeration value. Don't use.                                                                                                                                |

## Relationships

None.

## JSON representation

The following is a JSON representation of the resource.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.security.servicePrincipalEvidence"
}
-->

``` json
{
  "@odata.type": "#microsoft.graph.security.servicePrincipalEvidence",
  "servicePrincipalName": "String",
  "servicePrincipalObjectId": "String",
  "appId": "String",
  "appOwnerTenantId": "String",
  "tenantId": "String",
  "servicePrincipalType": "String"
}
```