---
title: "servicePrincipalEvidence resource type"
description: "Represents a ServicePrincipal reported in a security detection alert."
author: "Lirlev48"
ms.localizationpriority: medium
ms.subservice: "security"
ms.prod: "security"
doc_type: resourcePageType
---

# servicePrincipalEvidence resource type

Namespace: microsoft.graph.security

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents a ServicePrincipal that is reported in the security detection alert.

Inherits from [alertEvidence](../resources/security-alertevidence.md).

## Properties

|Property|Type|Description|
|:-------|:---|:----------|
|appId|String|The unique identifier for the associated application (its appId property).|
|appOwnerTenantId|String|Contains the tenant ID where the application is registered.|
|servicePrincipalName|String|The display name for the service principal.|
|servicePrincipalObjectId|String|The unique identifier for the service principal.|
|servicePrincipalType|[microsoft.graph.security.servicePrincipalType](#serviceprincipaltype-values)|Type of the service principal. Possible values are: `unknown`, `application`, `managedIdentity`, `legacy`, `unknownFutureValue`.|
|tenantId|String|The Microsoft Entra tenant ID of Service Principal.|

### servicePrincipalType values

|Member|Description|
|:-----|:----------|
|unknown|The service principal type isn't known.|
|application|The local representation or application instance of a global application object in a single tenant or directory.|
|managedIdentity|The service principal is a managed identity.|
|legacy|The service principal is a legacy app, which is either an app created before app registrations were introduced or an app created through legacy experiences.|
|unknownFutureValue|Evolvable enumeration value. Don't use.|

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.
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