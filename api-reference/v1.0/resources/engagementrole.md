---
title: "engagementRole resource type"
description: "Represents a predefined Viva Engage role."
author: "richafnu"
ms.date: 09/22/2025
ms.localizationpriority: medium
ms.subservice: "viva-engage"
doc_type: resourcePageType
---

# engagementRole resource type

Namespace: microsoft.graph

Represents a predefined Viva Engage role. Each role includes a unique identifier and display name and can be assigned to one or more users within the platform.

Inherits from [entity](../resources/entity.md).

## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[List assigned roles](../api/employeeexperienceuser-list-assignedroles.md)|[engagementRole](../resources/engagementrole.md)|Get a list of all the [roles](../resources/engagementrole.md) assigned to a user in Viva Engage.|
|[List members](../api/engagementrole-list-members.md)|[engagementRoleMember](../resources/engagementrolemember.md) collection|Get a list of users with assigned [roles](../resources/engagementrole.md) in Viva Engage.|
|[List roles](../api/employeeexperience-list-roles.md)|[engagementRole](../resources/engagementrole.md) collection|Get a list of all the [roles](../resources/engagementrole.md) that can be assigned in Viva Engage.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|displayName|String|The name of the role.|
|id|String|The unique identifier of the role. Read-only. Inherited from [entity](../resources/entity.md)|

## Relationships
| Relationship | Type | Description |
|:---|:---|:---|
|members|[engagementRoleMember](../resources/engagementrolemember.md) collection|TODO|

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.engagementRole",
  "baseType": "microsoft.graph.entity",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.engagementRole",
  "displayName": "String",
  "id": "String (identifier)"
}
```
