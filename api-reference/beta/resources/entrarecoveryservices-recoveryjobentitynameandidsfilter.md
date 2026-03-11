---
title: "recoveryJobEntityNameAndIdsFilter resource type"
description: "Filters recovery jobs to only include changes for specific entities identified by type and ID."
author: "mapamu"
ms.date: 03/04/2026
ms.localizationpriority: medium
ms.subservice: "entra-id"
doc_type: resourcePageType
---

# recoveryJobEntityNameAndIdsFilter resource type

Namespace: microsoft.graph.entraRecoveryServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Filters recovery jobs to only include changes for specific entities identified by type and ID. Used as `filteringCriteria` in POST request bodies for preview and recovery jobs. Duplicate entity types in `filterValues` are not allowed and will return a `400 Bad Request` error.

Inherits from [microsoft.graph.entraRecoveryServices.recoveryJobFilteringCriteriaBase](../resources/entrarecoveryservices-recoveryjobfilteringcriteriabase.md).

## Properties
|Property|Type|Description|
|:---|:---|:---|
|filterValues|[microsoft.graph.entraRecoveryServices.entityTypeAndIds](../resources/entrarecoveryservices-entitytypeandids.md) collection|The list of entity type and ID pairs to include in the recovery job.|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.entraRecoveryServices.recoveryJobEntityNameAndIdsFilter"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryJobEntityNameAndIdsFilter",
  "filterValues": [
    {
      "@odata.type": "microsoft.graph.entraRecoveryServices.entityTypeAndIds"
    }
  ]
}
```
