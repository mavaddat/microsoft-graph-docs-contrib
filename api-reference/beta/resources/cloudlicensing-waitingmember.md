---
title: "waitingMember resource type"
description: "List of over-assigned users who are in the waiting room for an allotment due to license capacity limits."
author: "patrick-starrin"
ms.date: 07/18/2025
ms.localizationpriority: medium
ms.subservice: "cloud-licensing"
doc_type: resourcePageType
---

# waitingMember resource type

Namespace: microsoft.graph.cloudLicensing

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents a user or device that got added to the waiting room for an allotment due to license capacity limits.

Inherits from [entity](../resources/entity.md)

## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[List](../api/cloudlicensing-allotment-list-waitingmembers.md)|[microsoft.graph.cloudLicensing.waitingMember](../resources/cloudlicensing-waitingmember.md) collection|Get a list of the waitingMember objects and their properties.|
|[Get](../api/cloudlicensing-waitingmember-get.md)|[microsoft.graph.cloudLicensing.waitingMember](../resources/cloudlicensing-waitingmember.md)|Read the properties and relationships of [microsoft.graph.cloudLicensing.waitingMember](../resources/cloudlicensing-waitingmember.md) object.|
|[List allotment](../api/cloudlicensing-waitingmember-list-allotment.md)|[microsoft.graph.cloudLicensing.allotment](../resources/cloudlicensing-allotment.md) collection|Get waiting members for an allotment by id.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|id|String|The unique identifier for the **waitingMember** that should be treated as an opaque identifier. Inherited from [entity](../resources/entity.md). Not nullable. Read-only.|
|waitingSinceDateTime|DateTimeOffset|Indicates when the user or device first began waiting for this license.|

## Relationships
|Relationship|Type|Description|
|:---|:---|:---|
|allotment|[microsoft.graph.cloudLicensing.allotment](../resources/cloudlicensing-allotment.md)|The allotment from which licenses are assigned. Not nullable.|
|assignedTo|[directoryObject](../resources/directoryobject.md)|The user or group to which licenses are assigned. Not nullable.|

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.cloudLicensing.waitingMember",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.cloudLicensing.waitingMember",
  "id": "String (identifier)",
  "waitingSinceDateTime": "String (timestamp)"
}
```

