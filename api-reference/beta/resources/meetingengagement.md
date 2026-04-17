---
title: "meetingengagement resource type"
description: "Contains information associated with a meeting participant interaction in an attendanceRecord."
author: "garchiro7"
ms.localizationpriority: medium
ms.subservice: "cloud-communications"
doc_type: resourcePageType
ms.date: 04/17/2024
---

# meetingengagement resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Contains information associated with real-time participant interaction behaviors during a meeting reactions (like, love, applause, etc.), hand raises, camera toggles, and microphone mute/unmute events in an [attendanceRecord](attendancerecord.md).

## Properties

| Property   | Type                                    | Description |
| ---------- | --------------------------------------- | ----------- |
| `engagementType` | [engagementType](#engagementtype-values)  | The category of the engagement event. Required, non-nullable. |
| `engagementSubType` | String                     | The specific engagement action within the type (e.g., `like`, `love`, `applause`, `laugh`, `surprised` for reactions; `raiseHand` for hand; `cameraOn` for camera; `unmute`, `mute` for microphone). |
| `dateTime` | DateTime                   | The UTC date and time when the engagement event occurred. |


#### engagementType values

| Member               | Description |
| -------------------- | ----------- |
| `reaction`           | An emoji reaction (like, love, applause, laugh, surprised). |
| `hand`               | A hand raise event. |
| `camera`             | A camera toggle event. |
| `microphone`         | A microphone mute/unmute event. |
| `unknownFutureValue` | Evolvable enumeration sentinel value. Do not use. |

## Relationships
None.

## JSON representation

The following JSON representation shows the resource type.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.meetingengagement"
}-->

```json
{
    "engagementType": "String",
    "engagementSubType": "String",
    "dateTime": "String"
}  
```
