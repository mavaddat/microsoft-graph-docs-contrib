---
title: "sasTokenEvidence resource type"
description: "Represents a Shared Access Signature (SAS) token entity for a storage container."
author: "Lirlev48"
ms.localizationpriority: medium
ms.subservice: "security"
doc_type: resourcePageType
ms.date: 05/07/2026
---

# sasTokenEvidence resource type

Namespace: microsoft.graph.security

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents a Shared Access Signature (SAS) token entity for a storage container.

Inherits from [alertEvidence](../resources/security-alertevidence.md).

## Properties

|Property|Type|Description|
|:-------|:---|:----------|
|signatureHash|String|The SAS signature hash, which is the unique identifier for the SAS.|
|allowedServices|String collection|All of the services that are accessible with this SAS.|
|allowedResourceTypes|String collection|All of the resource types accessible with this SAS.|
|permissions|String collection|All of the permissions granted to this SAS.|
|startDateTime|DateTimeOffset|The SAS activation time. This property can be null.|
|expiryDateTime|DateTimeOffset|The SAS expiration time.|
|allowedIpAddresses|String|All IP addresses that are accessible with this SAS. The default value is "Allows all IP addresses".|
|signedWith|String|The storage key used to generate the SAS.|
|protocol|String|The protocol that is allowed for the SAS.|
|storageResource|[microsoft.graph.security.azureResourceEvidence](security-azureresourceevidence.md)|A link to this SAS's storage resource.|

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.
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
```