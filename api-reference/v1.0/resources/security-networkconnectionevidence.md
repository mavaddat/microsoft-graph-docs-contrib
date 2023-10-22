---
title: "networkConnectionEvidence resource type"
description: "Represents a network connection entity."
author: "MSLironLevy"
ms.localizationpriority: medium
ms.prod: "security"
doc_type: resourcePageType
---

# networkConnectionEvidence resource type

Namespace: microsoft.graph.security

Represents network connection entity.

Inherits from [alertEvidence](../resources/security-alertevidence.md).

## Properties

| Property           | Type                                                            | Description                                                         |
|:-------------------|:----------------------------------------------------------------|:--------------------------------------------------------------------|
| sourceAddress      | [microsoft.graph.security.ipEvidence](./security-ipevidence.md) | An entity of type ‘ip’ that is the source for this connection.      |
| sourcePort         | Int32                                                           | The source port number, e.g. 80.                                    |
| destinationAddress | [microsoft.graph.security.ipEvidence](./security-ipevidence.md) | An entity of type ‘ip’ that is the destination for this connection. |
| destinationPort    | Int32                                                           | The destination port number, e.g. 80.                               |
| protocol           | [microsoft.graph.security.protocolType](#protocoltype-values)   | One of the following values.                                        |

### protocolType values

| Member             | Description                                                                                |
|:-------------------|:-------------------------------------------------------------------------------------------|
| tcp                | Fast, connectionless data transmission, used for tasks like streaming and gaming.          |
| udp                | Reliable, connection-oriented data transfer, essential for web browsing and file transfer. |
| unknownFutureValue | Evolvable enumeration value. Don't use.                                                    |

## Relationships
None.

## JSON representation

The following is a JSON representation of the resource.
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
  "protocol": "String",
}
```
