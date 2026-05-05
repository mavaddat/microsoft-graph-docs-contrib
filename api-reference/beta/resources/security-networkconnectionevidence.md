---
title: "networkConnectionEvidence resource type"
description: "Represents a network connection entity."
author: "Lirlev48"
ms.localizationpriority: medium
ms.subservice: "security"
ms.prod: "security"
doc_type: resourcePageType
---

# networkConnectionEvidence resource type

Namespace: microsoft.graph.security

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents a network connection entity.

Inherits from [alertEvidence](../resources/security-alertevidence.md).

## Properties

|Property|Type|Description|
|:-------|:-----|:--------|
|sourceAddress|[microsoft.graph.security.ipEvidence](./security-ipevidence.md)|An entity of type 'ip' that is the source for this connection.|
|sourcePort|Int32|The source port number, for example, 80.|
|destinationAddress|[microsoft.graph.security.ipEvidence](./security-ipevidence.md)|An entity of type 'ip' that is the destination for this connection.|
|destinationPort|Int32|The destination port number, for example, 80.|
|protocol|[microsoft.graph.security.protocolType](#protocoltype-values)|The protocol type. Possible values are 'tcp', 'udp', 'unknownFutureValue'.|

### protocolType values

|Member|Description|
|:-----|:----------|
|tcp|Reliable, connection-oriented data transfer, essential for web browsing and file transfer.|
|udp|Fast, connectionless data transmission, used for tasks like streaming and gaming.|
|unknownFutureValue|Evolvable enumeration value. Don't use.|

## Relationships

None.

## JSON representation

<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.security.networkConnectionEvidence"
} -->

The following JSON representation shows the resource type.

``` json
{
  "@odata.type": "#microsoft.graph.security.networkConnectionEvidence",
  "sourceAddress": {
    "@odata.type": "microsoft.graph.security.ipEvidence"
  },
  "sourcePort": "Int32",
  "destinationAddress": {
    "@odata.type": "microsoft.graph.security.ipEvidence"
  },
  "destinationPort": "Int32",
  "protocol": "String"
}
```
