---
title: "Update recoveryJob"
description: "Update the properties of a recoveryJob object."
author: "**TODO: Provide GitHub Name. See [topic-level metadata reference](https://eng.ms/docs/products/microsoft-graph-service/microsoft-graph/document-apis/metadata)**"
ms.date: 03/04/2026
ms.localizationpriority: medium
ms.subservice: "**TODO: Add MS subservice. See [topic-level metadata reference](https://eng.ms/docs/products/microsoft-graph-service/microsoft-graph/document-apis/metadata)**"
doc_type: apiPageType
---

# Update recoveryJob

Namespace: microsoft.graph.entraRecoveryServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Update the properties of a recoveryJob object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "entrarecoveryservices-recoveryjob-update-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/entrarecoveryservices-recoveryjob-update-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
PATCH /directory/recovery/snapshots/{snapshotId}/recoveryJobs/{recoveryJobId}
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

[!INCLUDE [table-intro](../../includes/update-property-table-intro.md)]


**TODO: Remove properties that don't apply**
|Property|Type|Description|
|:---|:---|:---|
|status|microsoft.graph.entraRecoveryServices.recoveryStatus|**TODO: Add Description** Inherited from [microsoft.graph.entraRecoveryServices.recoveryJobBase](../resources/entrarecoveryservices-recoveryjobbase.md). The possible values are: `initialized`, `running`, `successful`, `failed`, `abandoned`, `unknownFutureValue`, `calculating`, `loadingData`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `calculating` , `loadingData`. Required.|
|targetStateDateTime|DateTimeOffset|**TODO: Add Description** Inherited from [microsoft.graph.entraRecoveryServices.recoveryJobBase](../resources/entrarecoveryservices-recoveryjobbase.md). Required.|
|jobStartDateTime|DateTimeOffset|**TODO: Add Description** Inherited from [microsoft.graph.entraRecoveryServices.recoveryJobBase](../resources/entrarecoveryservices-recoveryjobbase.md). Required.|
|jobCompletionDateTime|DateTimeOffset|**TODO: Add Description** Inherited from [microsoft.graph.entraRecoveryServices.recoveryJobBase](../resources/entrarecoveryservices-recoveryjobbase.md). Optional.|
|filteringCriteria|[microsoft.graph.entraRecoveryServices.recoveryJobFilteringCriteriaBase](../resources/entrarecoveryservices-recoveryjobfilteringcriteriabase.md)|**TODO: Add Description** Inherited from [microsoft.graph.entraRecoveryServices.recoveryJobBase](../resources/entrarecoveryservices-recoveryjobbase.md). Optional.|
|totalChangedObjectsCalculated|Int32|**TODO: Add Description** Inherited from [microsoft.graph.entraRecoveryServices.recoveryJobBase](../resources/entrarecoveryservices-recoveryjobbase.md). Optional.|
|totalChangedLinksCalculated|Int32|**TODO: Add Description** Inherited from [microsoft.graph.entraRecoveryServices.recoveryJobBase](../resources/entrarecoveryservices-recoveryjobbase.md). Optional.|
|totalObjectsModified|Int32|**TODO: Add Description** Optional.|
|totalLinksModified|Int32|**TODO: Add Description** Optional.|
|totalFailedChanges|Int32|**TODO: Add Description** Optional.|



## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.entraRecoveryServices.recoveryJob](../resources/entrarecoveryservices-recoveryjob.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "update_recoveryjob"
}
-->
``` http
PATCH https://graph.microsoft.com/beta/directory/recovery/snapshots/{snapshotId}/recoveryJobs/{recoveryJobId}
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryJob",
  "status": "String",
  "targetStateDateTime": "String (timestamp)",
  "jobStartDateTime": "String (timestamp)",
  "jobCompletionDateTime": "String (timestamp)",
  "filteringCriteria": {
    "@odata.type": "microsoft.graph.entraRecoveryServices.recoveryJobFilteringCriteriaBase"
  },
  "totalChangedObjectsCalculated": "Integer",
  "totalChangedLinksCalculated": "Integer",
  "totalObjectsModified": "Integer",
  "totalLinksModified": "Integer",
  "totalFailedChanges": "Integer"
}
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryJob",
  "id": "b9a1406c-a461-4ed5-5203-49ef8eddb2b9",
  "status": "String",
  "targetStateDateTime": "String (timestamp)",
  "jobStartDateTime": "String (timestamp)",
  "jobCompletionDateTime": "String (timestamp)",
  "filteringCriteria": {
    "@odata.type": "microsoft.graph.entraRecoveryServices.recoveryJobFilteringCriteriaBase"
  },
  "totalChangedObjectsCalculated": "Integer",
  "totalChangedLinksCalculated": "Integer",
  "totalObjectsModified": "Integer",
  "totalLinksModified": "Integer",
  "totalFailedChanges": "Integer"
}
```

