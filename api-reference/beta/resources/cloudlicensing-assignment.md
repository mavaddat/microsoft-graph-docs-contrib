---
title: "assignment resource type"
description: "A license assignment, granting a license for the product-SKU contained within an allotment directly to the assigned user or indirectly to each member of the assigned group."
author: "kunal-chilka"
ms.date: 07/18/2025
ms.localizationpriority: medium
ms.subservice: "cloud-licensing"
doc_type: resourcePageType
---

# assignment resource type

Namespace: microsoft.graph.cloudLicensing

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

A license assignment, granting a license for the product-SKU contained within an allotment directly to the assigned user or indirectly to each member of the assigned group. Each unique user consumes one license from each allotment to which they are directly or indirectly assigned.

Inherits from [entity](../resources/entity.md)

## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[List](../api/cloudlicensing-allotment-list-assignments.md)|[microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md) collection|Get a list of the [microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md) objects and their properties.|
|[Create](../api/cloudlicensing-admincloudlicensing-post-assignments.md)|[microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md)|Create a new [microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md) object.|
|[Create for allotment](../api/cloudlicensing-allotment-post-assignments.md)|[microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md)|Create a new [microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md) object.|
|[Create for user](../api/cloudlicensing-usercloudlicensing-post-assignments.md)|[microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md)|Create a new [microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md) object.|
|[Create for group](../api/cloudlicensing-groupcloudlicensing-post-assignments.md)|[microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md)|Create a new [microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md) object.|
|[Get](../api/cloudlicensing-assignment-get.md)|[microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md)|Read the properties and relationships of [microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md) object.|
|[Update](../api/cloudlicensing-assignment-update.md)|[microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md)|Update the properties of a assignment object.|
|[reprocessAssignments](../api/cloudlicensing-assignment-reprocessassignments.md)|None|Reprocess existing license assignments for a user by posting to the user's assignments reprocessAssignments action.|
|[List allotment](../api/cloudlicensing-assignment-list-allotment.md)|[microsoft.graph.cloudLicensing.allotment](../resources/cloudlicensing-allotment.md) collection|Get a list of allotment objects.|
|[Remove assignment](../api/cloudlicensing-assignment-delete-allotment.md)|None|Remove a [microsoft.graph.cloudLicensing.allotment](../resources/cloudlicensing-allotment.md) object.|
|[List assignedTo](../api/cloudlicensing-assignment-list-assignedto.md)|[microsoft.graph.directoryObject](../resources/directoryobject.md) collection| Get the list of user or group to which licenses are assigned.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|disabledServicePlanIds|Guid collection|The list of disabled service plans for this assignment. Not nullable.|
|id|String|The unique identifier for the **assignment** that should be treated as an opaque identifier. Inherited from [entity](../resources/entity.md). Not nullable.|

## Relationships
|Relationship|Type|Description|
|:---|:---|:---|
|allotment|[allotment](../resources/cloudlicensing-allotment.md)|The allotment from which licenses are assigned. Not nullable.|
|assignedTo|[directoryObject](../resources/directoryobject.md)|The user or group to which licenses are assigned. Not nullable.|

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.cloudLicensing.assignment",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
  "disabledServicePlanIds": [
    "Guid"
  ],
  "id": "String (identifier)"
}
```

