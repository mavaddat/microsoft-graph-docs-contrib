---
title: "timeCard: clockIn"
description: "Clock in to start a timecard."
author: lemike
ms.date: 01/17/2025
ms.localizationpriority: medium
ms.subservice: teams
doc_type: apiPageType
---

# timeCard: clockIn

Namespace: microsoft.graph

Clock in to start a [timeCard](../resources/timeCard.md).

[!INCLUDE [national-cloud-support](../../includes/global-only.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "timecard_clockin" } -->
[!INCLUDE [permissions-table](../includes/permissions/timecard-clockin-permissions.md)]

> [!IMPORTANT]
> When you use the Schedule.ReadWrite.All application permission, you must include the `MS-APP-ACTS-AS` header in the request.

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
```http
POST /teams/{teamId}/schedule/timeCards/clockIn
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
| Content-type | application/json. Required.|
| MS-APP-ACTS-AS | The ID of the user on behalf of whom the app is acting. Required when you use the application permission scope. |

## Request body

In the request body, provide a JSON object with the following parameters.

|Parameter|Type|Description|
|:---|:---|:---|
|isAtApprovedLocation|Boolean|Indicates whether this action happens at an approved location.|
|notes|[itemBody](../resources/itembody.md)|Notes for the clock in.|

## Response

If successful, this method returns a `201 Created` response code and a [timeCard](../resources/timeCard.md) object in the response body.

## Example

### Request
The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "timecardthis.clockin"
}
-->
``` http
POST https://graph.microsoft.com/v1.0/teams/fd15cad8-80f6-484f-9666-3caf695fbf32/schedule/timeCards/clockin
Content-type: application/json

{
  "isAtApprovedLocation": true,
  "notes": {
    "content": "Started late due to traffic",
    "contentType": "text"
  }
}
```


### Response

The following example shows the response.

>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.timeCard"
} -->

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "id": "TCK_95c44dff-bc12-4de2-8a9a-9772e4421eb4",
  "createdDateTime": "2025-01-07T21:35:36.311Z",
  "lastModifiedDateTime": "2025-01-07T21:35:36.311Z",
  "userId": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
  "state": "clockedIn",
  "confirmedBy": "none",
  "clockOutEvent": null,
  "notes": null,
  "lastModifiedBy": {
    "application": null,
    "device": null,
    "user": {
      "id": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
      "displayName": "Alice Bradford"
    }
  },
  "clockInEvent": {
    "dateTime": "2025-01-07T21:35:36.311Z",
    "isAtApprovedLocation": true,
    "notes": {
      "contentType": "text",
      "content": "Started late due to traffic"
    }
  },
  "breaks": [],
  "originalEntry": {
    "clockOutEvent": null,
    "clockInEvent": {
      "dateTime": "2025-01-07T21:35:36.311Z",
      "isAtApprovedLocation": true,
      "notes": {
        "contentType": "text",
        "content": "Started late due to traffic"
      }
    },
    "breaks": []
  },
  "createdBy": {
    "application": null,
    "device": null,
    "user": {
      "id": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
      "displayName": "Alice Bradford"
    }
  }
}
```

