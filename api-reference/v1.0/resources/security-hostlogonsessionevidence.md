---
title: "hostLogonSessionEvidence resource type"
description: "Represents a logon session to a host by an account"
author: "MSLironLevy"
ms.localizationpriority: medium
ms.prod: "security"
doc_type: resourcePageType
---

# hostLogonSessionEvidence resource type

Namespace: microsoft.graph.security

Represents a logon session to a host by an account.

## Properties

| Property         | Type                                                                    | Description                                                       |
|:-----------------|:------------------------------------------------------------------------|:------------------------------------------------------------------|
| sessionId        | String                                                                  | The session id for the account reported in the alert, e.g. 0x3e7. |
| account          | [microsoft.graph.security.userEvidence](./security-userevidence.md)     | The Account associated with the logon session.                    |
| host             | [microsoft.graph.security.deviceEvidence](./security-deviceevidence.md) | The Host that the account had session on.                         |
| startUtcDateTime | DateTimeOffset                                                          | The session start time, if known.                                 |
| endUtcDateTime   | DateTimeOffset                                                          | The session end time, if known.                                   |

## Relationships

None.

## JSON representation

The following is a JSON representation of the resource.
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
