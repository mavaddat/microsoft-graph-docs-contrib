---
title: "List recoveryJobs"
description: "Get a list of recovery jobs for a specific snapshot."
author: "mapamu"
ms.date: 03/04/2026
ms.localizationpriority: medium
ms.subservice: "RecoveryServices"
doc_type: apiPageType
---

# List recoveryJobs

Namespace: microsoft.graph.entraRecoveryServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get a list of [recoveryJob](../resources/entrarecoveryservices-recoveryjob.md) objects for a specific snapshot.

[!INCLUDE [national-cloud-support](../../includes/all-clouds.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "entrarecoveryservices-snapshot-list-recoveryjobs-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/entrarecoveryservices-snapshot-list-recoveryjobs-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /directory/recovery/snapshots/{snapshotId}/recoveryJobs
```

## Optional query parameters

This method supports the `$select`, `$top`, `$filter`, and `$orderby` OData query parameters to help customize the response. For general information, see [OData query parameters](/graph/query-parameters).

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.entraRecoveryServices.recoveryJob](../resources/entrarecoveryservices-recoveryjob.md) objects in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "list_recoveryjob"
}
-->
``` http
GET https://graph.microsoft.com/beta/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryJobs
```

### Response

The following example shows the response.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "Collection(microsoft.graph.entraRecoveryServices.recoveryJob)"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#directory/recovery/snapshots('MjAyNC0wOC0yNlQwMjozMDowMFo=')/recoveryJobs",
  "value": [
    {
      "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryJob",
      "id": "3f4a6b60-7c1e-4e7c-9c7b-13f8d44b20c4",
      "status": "successful",
      "targetStateDateTime": "2024-08-26T02:30:00Z",
      "jobStartDateTime": "2024-08-26T08:30:00Z",
      "jobCompletionDateTime": "2024-08-26T13:30:00Z",
      "filteringCriteria": null,
      "totalChangedObjectsCalculated": 1024,
      "totalChangedLinksCalculated": 124,
      "totalObjectsModified": 1024,
      "totalLinksModified": 124,
      "totalFailedChanges": 0
    }
  ]
}
```
