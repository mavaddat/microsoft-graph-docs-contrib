---
title: "recoveryJobEntityNamesFilter resource type"
description: "Filters recovery jobs to only include changes for specified entity types."
author: "mapamu"
ms.date: 03/04/2026
ms.localizationpriority: medium
ms.subservice: "RecoveryServices"
doc_type: resourcePageType
---

# recoveryJobEntityNamesFilter resource type

Namespace: microsoft.graph.entraRecoveryServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Filters recovery jobs to only include changes for specified entity types (for example, only users, or only users and groups). Used as `filteringCriteria` in POST request bodies for preview and recovery jobs.

Inherits from [microsoft.graph.entraRecoveryServices.recoveryJobFilteringCriteriaBase](../resources/entrarecoveryservices-recoveryjobfilteringcriteriabase.md).

## Properties
|Property|Type|Description|
|:---|:---|:---|
|entityTypes|microsoft.graph.entraRecoveryServices.resourceTypeName collection|The list of entity types to include in the recovery job.|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.entraRecoveryServices.recoveryJobEntityNamesFilter"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryJobEntityNamesFilter",
  "entityTypes": [
    "String"
  ]
}
```
