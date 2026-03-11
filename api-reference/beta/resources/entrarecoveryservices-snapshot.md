---
title: "snapshot resource type"
description: "Represents a backup snapshot of the tenant's directory data at a specific point in time."
author: "mapamu"
ms.date: 03/04/2026
ms.localizationpriority: medium
ms.subservice: "entra-id"
doc_type: resourcePageType
---

# snapshot resource type

Namespace: microsoft.graph.entraRecoveryServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents a backup snapshot of the tenant's directory data at a specific point in time. Snapshots define the timestamps to which a tenant's state can be recovered. The `id` property is a base64-encoded representation of the snapshot timestamp.

Inherits from [microsoft.graph.entity](../resources/entity.md).

## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[List snapshots](../api/entrarecoveryservices-recovery-list-snapshots.md)|[microsoft.graph.entraRecoveryServices.snapshot](../resources/entrarecoveryservices-snapshot.md) collection|Get a list of the snapshot objects and their properties.|
|[Get snapshot](../api/entrarecoveryservices-snapshot-get.md)|[microsoft.graph.entraRecoveryServices.snapshot](../resources/entrarecoveryservices-snapshot.md)|Read the properties and relationships of a snapshot object.|
|[Create recoveryJob](../api/entrarecoveryservices-snapshot-post-recoveryjobs.md)|[microsoft.graph.entraRecoveryServices.recoveryJob](../resources/entrarecoveryservices-recoveryjob.md)|Create a new recovery job to restore directory objects to this snapshot's state.|
|[Create recoveryPreviewJob](../api/entrarecoveryservices-snapshot-post-recoverypreviewjobs.md)|[microsoft.graph.entraRecoveryServices.recoveryPreviewJob](../resources/entrarecoveryservices-recoverypreviewjob.md)|Create a new preview job to enumerate changes required to restore to this snapshot's state.|
|[List recoveryJobs](../api/entrarecoveryservices-snapshot-list-recoveryjobs.md)|[microsoft.graph.entraRecoveryServices.recoveryJob](../resources/entrarecoveryservices-recoveryjob.md) collection|Get a list of recovery jobs for this snapshot.|
|[List recoveryPreviewJobs](../api/entrarecoveryservices-snapshot-list-recoverypreviewjobs.md)|[microsoft.graph.entraRecoveryServices.recoveryPreviewJob](../resources/entrarecoveryservices-recoverypreviewjob.md) collection|Get a list of preview jobs for this snapshot.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|createdDateTime|DateTimeOffset|The date and time when the snapshot was created.|
|id|String|The unique identifier for the snapshot. This is the base64-encoded representation of the snapshot timestamp. Inherited from [entity](../resources/entity.md).|
|totalChangedObjects|Int32|The total count of objects in this snapshot.|

## Relationships
|Relationship|Type|Description|
|:---|:---|:---|
|recoveryJobs|[microsoft.graph.entraRecoveryServices.recoveryJob](../resources/entrarecoveryservices-recoveryjob.md) collection|Collection of recovery jobs created for this snapshot.|
|recoveryPreviewJobs|[microsoft.graph.entraRecoveryServices.recoveryPreviewJob](../resources/entrarecoveryservices-recoverypreviewjob.md) collection|Collection of preview jobs created for this snapshot.|

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.entraRecoveryServices.snapshot",
  "baseType": "microsoft.graph.entity",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.snapshot",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "totalChangedObjects": "Integer"
}
```
