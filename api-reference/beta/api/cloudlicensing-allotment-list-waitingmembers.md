---
title: "List waitingMember objects"
description: "Get a list of over-assigned users who are in the waiting room due to license capacity limits."
author: "patrick-starrin"
ms.date: 07/18/2025
ms.localizationpriority: medium
ms.subservice: "cloud-licensing"
doc_type: apiPageType
---

# List waitingMember objects

Namespace: microsoft.graph.cloudLicensing

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get a list of over-assigned users who are in the waiting room due to license capacity limits. Use `/admin/cloudLicensing/allotments/{allotmentId}/waitingMembers` to retrieve all [microsoft.graph.cloudLicensing.waitingmember](../resources/cloudlicensing-waitingmember.md) for a specific allotment. Use `/users/{userId}/cloudLicensing/waitingMembers` to retrieve all allotments that a specific user is waiting for.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "cloudlicensing-allotment-list-waitingmembers-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/cloudlicensing-allotment-list-waitingmembers-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /admin/cloudLicensing/allotments/{allotmentId}/waitingMembers
GET /users/{userId}/cloudLicensing/waitingMembers
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](/graph/query-parameters).

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [waitingMember](../resources/cloudlicensing-waitingmember.md) objects in the response body.

## Examples

### Example 1: List waiting members for a specific allotment

#### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "list_waitingmember"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/rkocgef3dgjhnu3gmu2mqhbdbmwcymnf6fk3k6a7zbui5e7gfpmi/waitingMembers
```

#### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.cloudLicensing.waitingMember"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.waitingMember",
      "id": "49caea1b-ad15-64f1-70c5-5c5e3563d19c",
      "waitingSinceDateTime": "2024-09-22T17:11:10.6635939+00:00"
    }
  ]
}
```

### Example 2: List waiting members with assignee details

The following example shows how to list waiting members for an allotment and include details about who is waiting.

#### Request
<!-- {
  "blockType": "request",
  "name": "list_waitingmember_expanded"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/2b7fc5fe-2267-404e-ada7-32b321f116ee/waitingMembers?$expand=assignedTo($select=id,displayName)
```

#### Response
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.cloudLicensing.waitingMember"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.waitingMember",
      "id": "1fb53c08-3f20-4b4e-b2f0-7d8fbb6bcaea",
      "waitingSinceDateTime": "2024-09-22T17:11:10.6635939+00:00",
      "assignedTo": {
        "@odata.type": "#microsoft.graph.user",
        "id": "a6c034b8-621b-dee3-6abb-52cbce801fe9",
        "displayName": "John Smith"
      }
    },
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.waitingMember",
      "id": "2gc64d19-4g30-5c5f-c3g1-8e9gcc7dcbfb",
      "waitingSinceDateTime": "2024-09-22T18:25:15.7746040+00:00",
      "assignedTo": {
        "@odata.type": "#microsoft.graph.user",
        "id": "b7d145c9-722c-5dbb-53dc-63gf714f63gb",
        "displayName": "Jane Doe"
      }
    },
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.waitingMember",
      "id": "3hd75e2a-5h41-6d6g-d4h2-9f0hdd8edc0c",
      "waitingSinceDateTime": "2024-09-22T19:30:20.8857151+00:00",
      "assignedTo": {
        "@odata.type": "#microsoft.graph.group",
        "id": "d8ee6ba1-2b90-4e77-90e8-3e52a09bc35a",
        "displayName": "Marketing Team"
      }
    }
  ]
}
```

### Example 3: List all allotments a user is waiting for

The following example shows how to get all allotments that a specific user is waiting for licenses from.

#### Request
<!-- {
  "blockType": "request",
  "name": "list_user_waitingmembers"
}
-->
``` http
GET https://graph.microsoft.com/beta/users/f7bcb3b5-57c3-40e3-8075-4e9060a052ab/cloudLicensing/waitingMembers?$expand=allotment($select=id,skuPartNumber,allottedUnits,consumedUnits)
```

#### Response
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.cloudLicensing.waitingMember"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.waitingMember",
      "id": "4ie86f3b-6i52-7e7h-e5i3-af1iee9fed1d",
      "waitingSinceDateTime": "2024-09-20T14:45:30.1234567+00:00",
      "allotment": {
        "@odata.type": "#microsoft.graph.cloudLicensing.allotment",
        "id": "2b7fc5fe-2267-404e-ada7-32b321f116ee",
        "skuPartNumber": "QUANTUM_TELEPORTER_AUTO_FAILOVER",
        "allottedUnits": 32,
        "consumedUnits": 32
      }
    },
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.waitingMember",
      "id": "5jf97g4c-7j63-8f8i-f6j4-bg2jff0gfe2e",
      "waitingSinceDateTime": "2024-09-21T10:20:45.9876543+00:00",
      "allotment": {
        "@odata.type": "#microsoft.graph.cloudLicensing.allotment",
        "id": "8abc12de-3456-7890-fghi-jklmnopqrstu",
        "skuPartNumber": "TIME_TRAVEL_BACKUP_RESTORE",
        "allottedUnits": 50,
        "consumedUnits": 50
      }
    }
  ]
}
```

### Example 4: Get waiting members ordered by wait time

The following example shows how to get waiting members for an allotment ordered by how long they've been waiting (FIFO queue).

#### Request
<!-- {
  "blockType": "request",
  "name": "list_waitingmember_ordered"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/rkocgef3dgjhnu3gmu2mqhbdbmwcymnf6fk3k6a7zbui5e7gfpmi/waitingMembers?$orderby=waitingSinceDateTime asc&$expand=assignedTo($select=id,displayName)
```

#### Response
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.cloudLicensing.waitingMember"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.waitingMember",
      "id": "1fb53c08-3f20-4b4e-b2f0-7d8fbb6bcaea",
      "waitingSinceDateTime": "2024-09-20T09:15:30.1234567+00:00",
      "assignedTo": {
        "@odata.type": "#microsoft.graph.user",
        "id": "a6c034b8-621b-dee3-6abb-52cbce801fe9",
        "displayName": "Alice First"
      }
    },
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.waitingMember",
      "id": "2gc64d19-4g30-5c5f-c3g1-8e9gcc7dcbfb",
      "waitingSinceDateTime": "2024-09-21T14:20:45.9876543+00:00",
      "assignedTo": {
        "@odata.type": "#microsoft.graph.user",
        "id": "b7d145c9-722c-5dbb-53dc-63gf714f63gb",
        "displayName": "Bob Second"
      }
    }
  ]
}
```