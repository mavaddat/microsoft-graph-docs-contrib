---
title: "sasTokenEvidence resource type"
description: "Represents a Shared Access Signature (SAS) token entity for a storage container."
author: "Lirlev48"
ms.localizationpriority: medium
ms.subservice: "security"
ms.date: 07/05/2026
doc_type: resourcePageType
---

# sasTokenEvidence resource type

Namespace: microsoft.graph.security

Represents the Shared Access Signature (SAS) token entity for a storage container.

Inherits from [alertEvidence](../resources/security-alertevidence.md).

## Properties

|Property|Type|Description|
|:-------|:---|:----------|
|signatureHash|String|The SAS signature hash, which is a unique identifier for each SAS.|
|allowedServices|String collection|All services accessible with this SAS.|
|allowedResourceTypes|String collection|All resource types accessible with this SAS.|
|permissions|String collection|All permissions granted to this SAS.|
|startDateTime|DateTimeOffset|The SAS activation time. This property can be null.|
|expiryDateTime|DateTimeOffset|The SAS expiration time.|
|allowedIpAddresses|String|All IP addresses accessible with this SAS. The default value is "Allows all IP addresses".|
|signedWith|String|The storage key that was used to generate the SAS.|
|protocol|String|The protocol that is allowed with this SAS.|
|storageResource|[microsoft.graph.security.azureResourceEvidence](security-azureresourceevidence.md)|The link to the storage resource that this SAS belongs to.|

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