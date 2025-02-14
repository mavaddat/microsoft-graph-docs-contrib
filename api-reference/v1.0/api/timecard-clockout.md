---
title: "timeCard: clockOut"
description: "Clock Out to end a timecard."
author: lemike
ms.date: 01/17/2025
ms.localizationpriority: medium
ms.subservice: teams
doc_type: apiPageType
---

# timeCard: clockOut

Namespace: microsoft.graph

Clock out to end a [timeCard](../resources/timeCard.md).

[!INCLUDE [national-cloud-support](../../includes/global-only.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "timecard_clockout" } -->
[!INCLUDE [permissions-table](../includes/permissions/timecard-clockout-permissions.md)]

> [!IMPORTANT]
> When you use the Schedule.ReadWrite.All application permission, you must include the `MS-APP-ACTS-AS` header in the request.

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
```http
POST /teams/{teamsId}/schedule/timeCards/{timeCardId}/clockOut
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
|notes|[itemBody](../resources/itembody.md)|Notes for the clock out.|

## Response

If successful, this method returns a `204 No Content` response code.


## Example

### Request
The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "timecardthis.clockout"
}
-->
```http
POST https://graph.microsoft.com/v1.0/teams/871dbd5c-3a6a-4392-bfe1-042452793a50/schedule/timeCards/TCK_95c44dff-bc12-4de2-8a9a-9772e4421eb4/clockOut
Content-type: application/json

{
    "isAtApprovedLocation": true,
    "notes": {
        "contentType": "text",
        "content": "clocking out"
    }
}
```

### Response

The following example shows the response.

<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 204 No Content
```

