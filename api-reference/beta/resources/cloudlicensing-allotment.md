---
title: "allotment resource type"
description: "An independently manageable pool of licenses backed by a subscription."
author: "patrick-starrin"
ms.date: 07/18/2025
ms.localizationpriority: medium
ms.subservice: "cloud-licensing"
doc_type: resourcePageType
---

# allotment resource type

Namespace: microsoft.graph.cloudLicensing

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

An independently manageable pool of licenses backed by a subscription.

Inherits from [entity](../resources/entity.md)

## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[List](../api/cloudlicensing-admincloudlicensing-list-allotments.md)|[microsoft.graph.cloudLicensing.allotment](../resources/cloudlicensing-allotment.md) collection|Get a list of the allotment objects and their properties.|
|[Get](../api/cloudlicensing-allotment-get.md)|[microsoft.graph.cloudLicensing.allotment](../resources/cloudlicensing-allotment.md)|Read the properties and relationships of [microsoft.graph.cloudLicensing.allotment](../resources/cloudlicensing-allotment.md) object.|
|[List assignments](../api/cloudlicensing-allotment-list-assignments.md)|[microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md) collection|Get a list of license assignments which consume licenses from this allotment.|
|[Add assignment](../api/cloudlicensing-allotment-post-assignments.md)|[microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md)|Add assignments by posting to the assignments collection.|
|[List waitingMembers](../api/cloudlicensing-allotment-list-waitingmembers.md)|[microsoft.graph.cloudLicensing.waitingMember](../resources/cloudlicensing-waitingmember.md) collection|Get a list of over-assigned users who are in the waiting room for this allotment due to license capacity limits.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|allottedUnits|Int32|The number of licenses contained within the allotment. Not nullable. Read-only.|
|assignableTo|[microsoft.graph.cloudLicensing.assigneeTypes](#assigneetypes-values)|Identifies the types of directory objects to which the allotment can be assigned. The possible values are: `none`, `user`, `group`, `device`, `unknownFutureValue`.<br/><br/>If new values are added to this [evolvable enum](/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations) in the future, you must use the `Prefer: include-unknown-enum-members` request header to get them.<br/><br/>The **assigneeTypes** property is a multi-valued enumeration and the property can contain multiple values in a comma-separated list. Not nullable. Read-only.|
|consumedUnits|Int32|The number of licenses currently being consumed by assignments from this allotment. Not nullable. Read-only.|
|id|String|The unique identifier for the **allotment** that should be treated as an opaque identifier. Inherited from [entity](../resources/entity.md). Not nullable. Read-only.|
|services|[microsoft.graph.cloudLicensing.service](../resources/cloudlicensing-service.md) collection| The list of services which may be enabled or disabled for assignments from this allotment. Not nullable. Read-only.|
|skuId|Guid|Unique identifier (GUID) for the service SKU that is equal to the **skuId** property on the related [subscribedSku](subscribedsku.md) object. Read-only. Supports `$filter`. |
|skuPartNumber|String| Unique SKU display name that is equal to the **skuPartNumber** on the related [subscribedSku](subscribedsku.md) object; for example, `AAD_Premium`. Read-only. |


### assigneeTypes values

| Member            | Description                                                            |
|:------------------|:-----------------------------------------------------------------------|
| none              | No flags are enabled; this service can't be assigned.                  |
| user              | If enabled, this service can be assigned directly to users.            |
| group             | If enabled, this service can be assigned to groups.                    |
| device            | If enabled, this service can be assigned directly to devices.          |
| unknownFutureValue| Evolvable enumeration sentinel value. Don't use.                       |


## Relationships
|Relationship|Type|Description|
|:---|:---|:---|
|assignments|[microsoft.graph.cloudLicensing.assignment](../resources/cloudlicensing-assignment.md) collection|The list of license assignments which consume licenses from this allotment. Not nullable.|
|waitingMembers|[microsoft.graph.cloudLicensing.waitingMember](../resources/cloudlicensing-waitingmember.md) collection|List of over-assigned users who are in the waiting room for an allotment due to license capacity limits.|

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.cloudLicensing.allotment",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.cloudLicensing.allotment",
  "allottedUnits": "Integer",
  "assignableTo": "String",
  "consumedUnits": "Integer",
  "id": "String (identifier)",
  "services": [
    {
      "@odata.type": "microsoft.graph.cloudLicensing.service"
    }
  ],
  "skuId": "Guid",
  "skuPartNumber": "String"
}
```

