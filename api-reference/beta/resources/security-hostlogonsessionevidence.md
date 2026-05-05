---
title: "hostLogonSessionEvidence resource type"
description: "Represents a logon session to a host by an account"
author: "Lirlev48"
ms.localizationpriority: medium
ms.prod: "security"
doc_type: resourcePageType
---

# hostLogonSessionEvidence resource type

Namespace: microsoft.graph.security

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents a logon session to a host by an account.

Inherits from [alertEvidence](../resources/security-alertevidence.md).

## Properties

|Property|Type|Description|
|:-----------------|:------------------------------------------------------------------------|:--------------------------------------------------------------------------|
|sessionId|String|The session ID for the account reported in the alert, for example, 0x3e7.|
|account|[microsoft.graph.security.userEvidence](./security-userevidence.md)|The Account that is associated with the logon session ID.|
|host|[microsoft.graph.security.deviceEvidence](./security-deviceevidence.md)|The host for the session.|
|startUtcDateTime|DateTimeOffset|The session start time, if known.|
|endUtcDateTime|DateTimeOffset|The session end time, if known.|

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.security.hostLogonSessionEvidence"
}
-->

``` json
{
  "@odata.type": "#microsoft.graph.security.hostLogonSessionEvidence",
  "sessionId": "String",
  "account": {
    "@odata.type": "microsoft.graph.security.userEvidence"
  },
  "host": {
    "@odata.type": "microsoft.graph.security.deviceEvidence"
  },
  "startUtcDateTime": "String (timestamp)",
  "endUtcDateTime": "String (timestamp)"
}
```
