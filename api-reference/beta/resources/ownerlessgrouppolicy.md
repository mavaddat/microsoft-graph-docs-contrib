---
title: "ownerlessGroupPolicy resource type"
description: "Represents the configuration for managing groups that have lost their sole owner."
author: "Ananya-Sharma"
ms.date: 02/12/2026
ms.localizationpriority: medium
ms.subservice: "groups"
doc_type: resourcePageType
---

# ownerlessGroupPolicy resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents the configuration for managing groups that have lost their sole owner. Use this policy to send actionable notification emails to active members of ownerless groups to accept ownership. Administrators can configure notification duration, maximum members to notify, and control ownership eligibility by using security groups.

Inherits from [entity](../resources/entity.md).

## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[Get](../api/ownerlessgrouppolicy-get.md)|[ownerlessGroupPolicy](../resources/ownerlessgrouppolicy.md)|Read the properties of an [ownerlessGroupPolicy](../resources/ownerlessgrouppolicy.md) object.|
|[Update](../api/ownerlessgrouppolicy-update.md)|[ownerlessGroupPolicy](../resources/ownerlessgrouppolicy.md)|Create or update an [ownerlessGroupPolicy](../resources/ownerlessgrouppolicy.md) object.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|emailInfo|[emailDetails](../resources/emaildetails.md)|The email notification details for the ownerless group policy, including the sender, subject, and body.|
|enabledGroupIds|String collection|The collection of group IDs for which the policy is enabled.|
|id|String|The unique identifier for the policy. Inherited from [entity](../resources/entity.md).|
|isEnabled|Boolean|Indicates whether the ownerless group policy is enabled. Setting this property to `false` clears the values of all other policy parameters.|
|maxMembersToNotify|Int64|The maximum number of members to notify. Value range is 0-90. Members are sorted by oldest membership first.|
|notificationDurationInWeeks|Int64|The number of weeks for the notification duration. Value range is 1-7.|
|policyWebUrl|String|The URL to the policy documentation.|
|targetOwners|[targetOwners](../resources/targetowners.md)|The criteria for selecting target owners for the ownerless group.|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.ownerlessGroupPolicy",
  "baseType": "microsoft.graph.entity",
  "openType": "id"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.ownerlessGroupPolicy",
  "id": "String (identifier)",
  "isEnabled": "Boolean",
  "notificationDurationInWeeks": "Integer",
  "maxMembersToNotify": "Integer",
  "enabledGroupIds": [
    "String"
  ],
  "emailInfo": {
    "@odata.type": "microsoft.graph.emailDetails"
  },
  "policyWebUrl": "String",
  "targetOwners": {
    "@odata.type": "microsoft.graph.targetOwners"
  }
}
```
