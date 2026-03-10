---
title: "Create recoveryJobBase"
description: "Create a new recoveryJobBase object."
author: "**TODO: Provide GitHub Name. See [topic-level metadata reference](https://eng.ms/docs/products/microsoft-graph-service/microsoft-graph/document-apis/metadata)**"
ms.date: 03/04/2026
ms.localizationpriority: medium
ms.subservice: "**TODO: Add MS subservice. See [topic-level metadata reference](https://eng.ms/docs/products/microsoft-graph-service/microsoft-graph/document-apis/metadata)**"
doc_type: apiPageType
---

# Create recoveryJobBase

Namespace: microsoft.graph.entraRecoveryServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Create a new recoveryJobBase object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "entrarecoveryservices-recovery-post-jobs-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/entrarecoveryservices-recovery-post-jobs-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /directory/recovery/jobs
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.entraRecoveryServices.recoveryJobBase](../resources/entrarecoveryservices-recoveryjobbase.md) object.

You can specify the following properties when creating a **recoveryJobBase**.

**TODO: Remove properties that don't apply**
|Property|Type|Description|
|:---|:---|:---|
|status|microsoft.graph.entraRecoveryServices.recoveryStatus|**TODO: Add Description**. The possible values are: `initialized`, `running`, `successful`, `failed`, `abandoned`, `unknownFutureValue`, `calculating`, `loadingData`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `calculating` , `loadingData`. Required.|
|targetStateDateTime|DateTimeOffset|**TODO: Add Description** Required.|
|jobStartDateTime|DateTimeOffset|**TODO: Add Description** Required.|
|jobCompletionDateTime|DateTimeOffset|**TODO: Add Description** Optional.|
|filteringCriteria|[microsoft.graph.entraRecoveryServices.recoveryJobFilteringCriteriaBase](../resources/entrarecoveryservices-recoveryjobfilteringcriteriabase.md)|**TODO: Add Description** Optional.|
|totalChangedObjectsCalculated|Int32|**TODO: Add Description** Optional.|
|totalChangedLinksCalculated|Int32|**TODO: Add Description** Optional.|



## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.entraRecoveryServices.recoveryJobBase](../resources/entrarecoveryservices-recoveryjobbase.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "create_recoveryjobbase_from_"
}
-->
``` http
POST https://graph.microsoft.com/beta/directory/recovery/jobs
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryJobBase",
  "status": "String",
  "targetStateDateTime": "String (timestamp)",
  "jobStartDateTime": "String (timestamp)",
  "jobCompletionDateTime": "String (timestamp)",
  "filteringCriteria": {
    "@odata.type": "microsoft.graph.entraRecoveryServices.recoveryJobFilteringCriteriaBase"
  },
  "totalChangedObjectsCalculated": "Integer",
  "totalChangedLinksCalculated": "Integer"
}
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.entraRecoveryServices.recoveryJobBase"
}
-->
``` http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryJobBase",
  "id": "f483f69c-f380-dd56-6e00-a3d25299540c",
  "status": "String",
  "targetStateDateTime": "String (timestamp)",
  "jobStartDateTime": "String (timestamp)",
  "jobCompletionDateTime": "String (timestamp)",
  "filteringCriteria": {
    "@odata.type": "microsoft.graph.entraRecoveryServices.recoveryJobFilteringCriteriaBase"
  },
  "totalChangedObjectsCalculated": "Integer",
  "totalChangedLinksCalculated": "Integer"
}
```

