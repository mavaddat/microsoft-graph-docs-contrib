---
title: "assignmentError resource type"
description: "Represents an error impacting synchronization of license assignments in the directory."
author: "kchilka07"
ms.date: 07/18/2025
ms.localizationpriority: medium
ms.subservice: "cloud-licensing"
doc_type: resourcePageType
---

# assignmentError resource type

Namespace: microsoft.graph.cloudLicensing

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents an error impacting synchronization of license assignments in the directory. This error can prevent the license assignment from taking effect or from being updated.

Inherits from [entity](../resources/entity.md)

## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[List](../api/cloudlicensing-admincloudlicensing-list-assignmenterrors.md)|[microsoft.graph.cloudLicensing.assignmentError](../resources/cloudlicensing-assignmenterror.md) collection|Get a list of the [microsoft.graph.cloudLicensing.assignmentError](../resources/cloudlicensing-assignmenterror.md) objects and their properties.|
|[Get](../api/cloudlicensing-assignmenterror-get.md)|[microsoft.graph.cloudLicensing.assignmentError](../resources/cloudlicensing-assignmenterror.md)|Read the properties and relationships of [microsoft.graph.cloudLicensing.assignmentError](../resources/cloudlicensing-assignmenterror.md) object.|
|[List assignedTo](../api/cloudlicensing-assignmenterror-list-assignedto.md)|[microsoft.graph.directoryObject](../resources/directoryobject.md) collection|Get the list of user or group to which licenses are assigned.|
|[List usageRight](../api/cloudlicensing-assignmenterror-list-usageright.md)|[microsoft.graph.cloudLicensing.usageRight](../resources/cloudlicensing-usageright.md) collection|Get a list of the usageRight objects affected by an assignmentError. A usageRight is only returned if there's a preexisting usageRight in effect, which is prevented from updating by this assignmentError.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|code|String|The error code associated with the assignment synchronization failure.|
|id|String|The unique identifier for the **assignmentError** that should be treated as an opaque identifier. Inherited from [entity](../resources/entity.md). Not nullable. Read-only.|
|message|String|The error message associated with the assignment synchronization failure.|
|occurrenceDateTime|DateTimeOffset|The date and time at which the error most recently occurred.|
|skuId|Guid| Unique identifier (GUID) for the service SKU that is equal to the **skuId** property on the related [subscribedSku](subscribedsku.md) object. Read-only. Supports `$filter`. |

## Relationships
|Relationship|Type|Description|
|:---|:---|:---|
|assignedTo|[directoryObject](../resources/directoryobject.md)|The user to whom licenses are assigned. Not nullable. Read-only.|
|usageRight|[usageRight](../resources/cloudlicensing-usageright.md)|The affected usageRight, if one exists. Read-only.|

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.cloudLicensing.assignmentError",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.cloudLicensing.assignmentError",
  "code": "String",
  "id": "String (identifier)",
  "message": "String",
  "occurrenceDateTime": "String (timestamp)",
  "skuId": "Guid"
}
```

