---
title: "scheduleEntity resource type"
description: "Represents a base type for schedule entries in Microsoft Teams Shifts, such as shifts, time off, and open shifts."
author: "aaku"
ms.localizationpriority: medium
ms.subservice: "teams"
doc_type: resourcePageType
ms.date: 04/23/2026
---

# scheduleEntity resource type

Namespace: microsoft.graph

Represents a base type for schedule entries in a [schedule](schedule.md). A `scheduleEntity` has a start and end time and a color theme, and is the base type for [shiftItem](shiftitem.md), [timeOffItem](timeoffitem.md), and [openShiftItem](openshiftitem.md).

## Properties

| Property | Type | Description |
|:---|:---|:---|
| endDateTime | DateTimeOffset | The end date and time for the **scheduleEntity**. Required. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| startDateTime | DateTimeOffset | The start date and time for the **scheduleEntity**. Required. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| theme | scheduleEntityTheme | The color of the schedule entry. The possible values are: `white`, `blue`, `green`, `purple`, `pink`, `yellow`, `gray`, `darkBlue`, `darkGreen`, `darkPurple`, `darkPink`, `darkYellow`, `unknownFutureValue`, `darkRed`, `cranberry`, `darkOrange`, `bronze`, `peach`, `gold`, `lime`, `forest`, `lightGreen`, `jade`, `lightTeal`, `darkTeal`, `steel`, `skyBlue`, `blueGray`, `lavender`, `lilac`, `plum`, `magenta`, `darkBrown`, `beige`, `charcoal`, `silver`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `darkRed` , `cranberry` , `darkOrange` , `bronze` , `peach` , `gold` , `lime` , `forest` , `lightGreen` , `jade` , `lightTeal` , `darkTeal` , `steel` , `skyBlue` , `blueGray` , `lavender` , `lilac` , `plum` , `magenta` , `darkBrown` , `beige` , `charcoal` , `silver`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.scheduleEntity"
}
-->
```json
{
  "@odata.type": "#microsoft.graph.scheduleEntity",
  "startDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)",
  "theme": "String"
}
```
