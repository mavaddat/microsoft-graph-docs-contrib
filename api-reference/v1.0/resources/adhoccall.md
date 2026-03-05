---
title: "adhocCall resource type - Microsoft Graph"
description: "Learn about the adhocCall resource type in Microsoft Graph API for PSTN calls, one-to-one calls, and group calls. Includes properties and relationships."
author: "kanchm"
#customer intent: As a developer, I want to understand the properties of the `adhocCall` resource type so that I can integrate it into my application.
ms.reviewer: v-sukanyadas
ms.date: 02/27/2026
ms.localizationpriority: medium
ms.subservice: "cloud-communications"
doc_type: resourcePageType
toc.title: "Ad hoc call"
---

# adhocCall resource type

Namespace: microsoft.graph

The adhocCall resource type represents an ad hoc call in Microsoft Graph API, including PSTN calls, one-to-one calls, and group calls. Use this resource to manage call recordings and transcripts through the Microsoft Graph communications API.

This resource supports subscribing to [change notifications](/graph/change-notifications-overview).

## Properties

|Property|Type|Description|
|:---|:---|:---|
| ID |String|The unique identifier for the ad hoc call. Read-only.|

## Relationships

|Relationship|Type|Description|
|:---|:---|:---|
|recordings|[callRecording](../resources/callrecording.md) collection | The recordings of a call. Read-only. |
|transcripts|[callTranscript](../resources/calltranscript.md) collection | The transcripts of a call. Read-only. |

## JSON representation

The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.adhocCall",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.adhocCall",
  "id": "String (identifier)"
}
```

## Related content

* [Change notifications for Microsoft Teams resources](/graph/teams-change-notification-in-microsoft-teams-overview)
* [Get change notifications for transcripts and recordings using Microsoft Graph](/graph/teams-changenotifications-callrecording-and-calltranscript)
* [callRecording resource type](../resources/callrecording.md)
* [callTranscript resource type](../resources/calltranscript.md)