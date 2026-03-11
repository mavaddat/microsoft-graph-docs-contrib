---
title: "recoveryPreviewJob: getChanges"
description: "Get a paginated collection of change objects that will be applied if the recovery operation is executed."
author: "mapamu"
ms.date: 03/04/2026
ms.localizationpriority: medium
ms.subservice: "entra-id"
doc_type: apiPageType
---

# recoveryPreviewJob: getChanges

Namespace: microsoft.graph.entraRecoveryServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get a paginated collection of [recoveryChangeObjectBase](../resources/entrarecoveryservices-recoverychangeobjectbase.md) objects that will be applied if a recovery operation is executed for the same snapshot and filtering criteria.

This method can only be called on a preview job that has a status of `successful`. The changes returned represent the differences between the current tenant state and the state at the time of the snapshot.

[!INCLUDE [national-cloud-support](../../includes/all-clouds.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "entrarecoveryservices-recoverypreviewjob-getchanges-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/entrarecoveryservices-recoverypreviewjob-getchanges-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /directory/recovery/snapshots/{snapshotId}/recoveryPreviewJobs/{jobId}/getChanges
```

## Function parameters

Don't supply a function parameter for this method.

## Optional query parameters

This method supports the `$top`, `$skip`, and `$select` OData query parameters to help customize the response. For general information, see [OData query parameters](/graph/query-parameters).

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a collection of [microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase](../resources/entrarecoveryservices-recoverychangeobjectbase.md) objects in the response body.

## Examples

### Example 1: Get changes showing objects that will be updated

The following example shows a request that retrieves changes where objects in the current tenant will be updated to match the snapshot state.

#### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "recoverypreviewjobthis.getchanges.example1"
}
-->
``` http
GET https://graph.microsoft.com/beta/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryPreviewJobs/d3f8e7e8-7e87-4a7f-9d2c-c1c2d7e8e1f1/getChanges
```

#### Response

The following example shows the response.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "Collection(microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase)"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection(microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase)",
  "@odata.count": 102424,
  "value": [
    {
      "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase",
      "objectId": "f71f21d6-1e7c-4a7f-9d2c-c1c2d7e8e1f1",
      "entityTypeName": "user",
      "recoveryAction": "update",
      "deltaFromCurrent": {
        "displayName": "Chris Green"
      },
      "currentState": {
        "displayName": "Christopher Green"
      }
    },
    {
      "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase",
      "objectId": "2a8f3e4d-7f1e-4c7b-8b1d-9a2f7b3e5c4d",
      "entityTypeName": "group",
      "recoveryAction": "update",
      "deltaFromCurrent": {
        "description": "Marketing team"
      },
      "currentState": {
        "description": "Sales and Marketing team"
      }
    }
  ],
  "@odata.nextLink": "https://graph.microsoft.com/beta/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryPreviewJobs/d3f8e7e8-7e87-4a7f-9d2c-c1c2d7e8e1f1/getChanges?$skip=2"
}
```

### Example 2: Get changes showing objects that will be restored

The following example shows changes where objects that were soft-deleted in the current tenant will be restored from the snapshot.

#### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "recoverypreviewjobthis.getchanges.example2"
}
-->
``` http
GET https://graph.microsoft.com/beta/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryPreviewJobs/d3f8e7e8-7e87-4a7f-9d2c-c1c2d7e8e1f1/getChanges?$skip=1000
```

#### Response

The following example shows the response.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "Collection(microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase)"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection(microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase)",
  "@odata.count": 102424,
  "value": [
    {
      "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase",
      "objectId": "8c2e9a4f-3d7b-4e1c-9f2a-5b8c1e2f3a4d",
      "entityTypeName": "user",
      "recoveryAction": "restore",
      "deltaFromCurrent": {
        "displayName": "Alex Johnson",
        "userPrincipalName": "alex.johnson@contoso.com",
        "accountEnabled": true
      },
      "currentState": null
    },
    {
      "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase",
      "objectId": "1f3a5c7e-4d2b-4e8f-9c1a-2b3d4e5f6a7b",
      "entityTypeName": "group",
      "recoveryAction": "restore",
      "deltaFromCurrent": {
        "displayName": "Finance Team",
        "mailEnabled": true,
        "securityEnabled": false
      },
      "currentState": null
    }
  ],
  "@odata.nextLink": "https://graph.microsoft.com/beta/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryPreviewJobs/d3f8e7e8-7e87-4a7f-9d2c-c1c2d7e8e1f1/getChanges?$skip=1002"
}
```

### Example 3: Get changes showing objects that will be soft-deleted

The following example shows changes where objects that exist in the current tenant but didn't exist in the snapshot will be soft-deleted.

#### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "recoverypreviewjobthis.getchanges.example3"
}
-->
``` http
GET https://graph.microsoft.com/beta/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryPreviewJobs/d3f8e7e8-7e87-4a7f-9d2c-c1c2d7e8e1f1/getChanges?$skip=2000
```

#### Response

The following example shows the response.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "Collection(microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase)"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection(microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase)",
  "@odata.count": 102424,
  "value": [
    {
      "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase",
      "objectId": "9d4f2e1c-7a3b-4f8e-9c2d-3e4f5a6b7c8d",
      "entityTypeName": "application",
      "recoveryAction": "softDelete",
      "deltaFromCurrent": null,
      "currentState": {
        "displayName": "Test Application",
        "appId": "a1b2c3d4-e5f6-4a5b-8c9d-0e1f2a3b4c5d"
      }
    }
  ],
  "@odata.nextLink": "https://graph.microsoft.com/beta/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryPreviewJobs/d3f8e7e8-7e87-4a7f-9d2c-c1c2d7e8e1f1/getChanges?$skip=2001"
}
```
