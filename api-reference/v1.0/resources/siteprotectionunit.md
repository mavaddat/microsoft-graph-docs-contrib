---
title: "siteProtectionUnit resource type"
description: "Represents a SharePoint site that has a SharePoint protection policy applied."
author: "tushar20"
ms.reviewer: "manikantsinghms"
ms.localizationpriority: medium
ms.subservice: "m365-backup-storage"
doc_type: resourcePageType
ms.date: 08/06/2024
---

# siteProtectionUnit resource type

Namespace: microsoft.graph

Represents a SharePoint site that has a [SharePoint protection policy](sharepointprotectionpolicy.md) applied.

Inherits from [protectionUnitBase](../resources/protectionunitbase.md).

## Methods

|Method|Return type|Description|
|:---|:---|:---|
|[List](../api/backuprestoreroot-list-siteprotectionunits.md)|[siteProtectionUnit](../resources/siteprotectionunit.md) collection|Get a list of [siteProtectionUnit](../resources/siteprotectionunit.md) objects and their properties.|

## Properties

|Property|Type|Description|
|:---|:---|:---|
|createdBy|[identitySet](../resources/identityset.md)|The identity of  the person who created the protection unit. Inherited from [protectionUnitBase](../resources/protectionunitbase.md).|
|createdDateTime|DateTimeOffset|The time of creation of the protection unit. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [protectionUnitBase](../resources/protectionunitbase.md).|
|error|[publicError](../resources/publicerror.md)|Contains error details if enabling or disabling the protection unit fails. Inherited from [protectionUnitBase](../resources/protectionunitbase.md).|
|id|String|Unique identifier of the protection policy associated with this protection unit.|
|lastModifiedBy|[identitySet](../resources/identityset.md)|The identity of the person who last modified the protection unit. Inherited from [protectionUnitBase](../resources/protectionunitbase.md).|
|lastModifiedDateTime|DateTimeOffset|The time the protection unit was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [protectionUnitBase](../resources/protectionunitbase.md).|
|offboardRequestedDateTime|DateTimeOffset|The date and time when protection unit offboard was requested. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [protectionUnitBase](../resources/protectionunitbase.md).|
|policyId|String|Unique identifier of the protection policy associated with this protection unit. Inherited from [protectionUnitBase](../resources/protectionunitbase.md).|
|siteId|String|Unique identifier of the SharePoint site.|
|siteName|String|Name of the SharePoint site.|
|siteWebUrl|String|The web URL of the SharePoint site.|
|status|[protectionUnitStatus](../resources/protectionunitbase.md#protectionunitstatus-values)|The individual enablement/disablement/removal status of the protection unit. The possible values are: `protectRequested`, `protected`, `unprotectRequested`, `unprotected`, `removeRequested`, `unknownFutureValue`, `offboardRequested`, `offboarded`, `cancelOffboardRequested`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `offboardRequested`, `offboarded`, `cancelOffboardRequested`. Inherited from [protectionUnitBase](../resources/protectionunitbase.md).|

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.siteProtectionUnit",
  "baseType": "microsoft.graph.protectionUnitBase",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.siteProtectionUnit",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "error": {"@odata.type": "microsoft.graph.publicError"},
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "offboardRequestedDateTime": "String (timestamp)",
  "policyId": "String",
  "siteId": "String",
  "siteName": "String",
  "siteWebUrl": "String",
  "status": "String"
}
```

