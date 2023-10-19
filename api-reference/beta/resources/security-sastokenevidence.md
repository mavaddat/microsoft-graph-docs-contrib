---
title: "sasTokenEvidence resource type"
description: "Represents a SAS token entity for storage container."
author: "MSLironLevy"
ms.localizationpriority: medium
ms.prod: "security"
doc_type: resourcePageType
---

# sasTokenEvidence resource type

Namespace: microsoft.graph.security

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents SAS token entity for storage container.

Inherits from [alertEvidence](../resources/security-alertevidence.md).

## Properties

| Property             | Type                                                                                  | Description                                                                             |
|:---------------------|:--------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------|
| signatureHash        | String                                                                                | The SAS signature hash - unique identifier for each SAS.                                |
| allowedServices      | String collection                                                                     | Set of all services accessible with this SAS.                                           |
| allowedResourceTypes | String collection                                                                     | Set of all resource types accessible with this SAS.                                     |
| permissions          | String collection                                                                     | Set of all permissions granted to this SAS.                                             |
| startDateTime        | DateTimeOffset                                                                        | SAS activation time - can be null.                                                      |
| expiryDateTime       | DateTimeOffset                                                                        | SAS expiration time.                                                                    |
| allowedIpAddresses   | String                                                                                | All IP addresses accessible with this SAS - default value is "Allows all IP addresses". |
| signedWith           | String                                                                                | The storage key which used to generate the SAS.                                         |
| protocol             | String                                                                                | Allowed protocol with this SAS.                                                         |
| storageResource      | [microsoft.graph.security.azureResourceEvidence](./security-azureResourceEvidence.md) | Link to storage resource that this SAS belongs to.                                      |

## Relationships

None.

## JSON representation

The following is a JSON representation of the resource.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.security.sasTokenEvidence"
}
-->

``` json
{
  "@odata.type": "#microsoft.graph.security.sasTokenEvidence",
  "signatureHash": "String",
  "allowedServices": [
    "String"
  ],
  "allowedResourceTypes": [
    "String"
  ],
  "permissions": [
    "String"
  ],
  "startDateTime": "String (timestamp)",
  "expiryDateTime": "String (timestamp)",
  "allowedIpAddresses": "String",
  "signedWith": "String",
  "protocol": "String",
  "storageResource": {
    "@odata.type": "microsoft.graph.security.azureResourceEvidence"
  }
}