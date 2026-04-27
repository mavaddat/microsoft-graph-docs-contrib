---
title: "m365CapabilityBase resource type"
description: "Abstract base type for cross-tenant M365 capabilities."
author: "lasharma"
ms.date: 04/23/2026
ms.localizationpriority: medium
ms.subservice: "entra-sign-in"
doc_type: resourcePageType
---

# m365CapabilityBase resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Abstract base type for cross-tenant M365 capabilities. This type cannot be instantiated directly. Instances are created using specific derived types. All capability instances in a collection are differentiated by the `@odata.type` property.

The following types derive from **m365CapabilityBase**:

- [crossTenantCalendarAvailabilityBasic](../resources/crosstenantcalendaravailabilitybasic.md)
- [crossTenantCalendarAvailabilityLimitedDetails](../resources/crosstenantcalendaravailabilitylimiteddetails.md)
- [crossTenantCalendarSharingFreeBusyDetail](../resources/crosstenantcalendarsharingfreebusydetail.md)
- [crossTenantCalendarSharingFreeBusyReviewer](../resources/crosstenantcalendarsharingfreebusyreviewer.md)
- [crossTenantCalendarSharingFreeBusySimple](../resources/crosstenantcalendarsharingfreebusysimple.md)
- [crossTenantMailTipsAll](../resources/crosstenantmailtipsall.md)
- [crossTenantMailTipsLimited](../resources/crosstenantmailtipslimited.md)
- [crossTenantMigration](../resources/crosstenantmigration.md)
- [crossTenantOpenProfileCard](../resources/crosstenantopenprofilecard.md)
- [crossTenantPlacesDeskBooking](../resources/crosstenantplacesdeskbooking.md)
- [crossTenantPlacesRoomBooking](../resources/crosstenantplacesroombooking.md)

## Methods
None.

## Properties
|Property|Type|Description|
|:---|:---|:---|
|inboundAccess|[m365CapabilityInboundAccess](../resources/m365capabilityinboundaccess.md)|The inbound access settings for the capability.|
|lastModifiedDateTime|DateTimeOffset|The automatically-updated last modified timestamp for the capability.|
|name|String|The name or identifier of the capability. Key.|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "name",
  "@odata.type": "microsoft.graph.m365CapabilityBase",
  "baseType": "",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.m365CapabilityBase",
  "name": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "inboundAccess": {
    "@odata.type": "microsoft.graph.m365CapabilityInboundAccess"
  }
}
```
