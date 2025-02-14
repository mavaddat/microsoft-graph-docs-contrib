---
title: "List timeCard objects"
description: "Retrieve a list of timeCard entries in the schedule."
author: lemike
ms.date: 01/17/2025
ms.localizationpriority: medium
ms.subservice: teams
doc_type: apiPageType
---

# List timeCard

Namespace: microsoft.graph

Retrieve a list of [timeCard](../resources/timecard.md) entries in a [schedule](../resources/schedule.md).

[!INCLUDE [national-cloud-support](../../includes/global-only.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "schedule_list_timecards" } -->
[!INCLUDE [permissions-table](../includes/permissions/schedule-list-timecards-permissions.md)]

> [!IMPORTANT]
> When you use the Schedule.Read.All and Schedule.ReadWrite.All application permissions, you must include the `MS-APP-ACTS-AS` header in the request.

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /teams/{teamsId}/schedule/timeCards
```

## Optional query parameters

This method supports the `$filter`, `$orderby`, `$top`, `$skipToken` OData query parameters to help customize the response. For general information, see [OData query parameters](/graph/query-parameters).

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
| MS-APP-ACTS-AS | The ID of the user on behalf of whom the app is acting. Required when you use the application permission scope. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [timeCard](../resources/timecard.md) objects in the response body.

## Example

### Request
The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "list_timecard"
}
-->
``` http
GET https://graph.microsoft.com/v1.0/teams/871dbd5c-3a6a-4392-bfe1-042452793a50/schedule/timeCards
```

### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.timeCard"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "TCK_ed816e2c-7c7a-44ff-9761-dc3df92a17ef",
      "createdDateTime": "2025-01-07T14:40:01.601Z",
      "lastModifiedDateTime": "2025-01-07T19:43:54.555Z",
      "userId": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
      "state": "clockedOut",
      "confirmedBy": "none",
      "notes": null,
      "lastModifiedBy": {
        "application": null,
        "device": null,
        "user": {
          "id": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
          "displayName": "Alice Bradford",
        }
      },
      "clockInEvent": {
        "dateTime": "2025-01-07T14:40:01.601Z",
        "isAtApprovedLocation": null,
        "notes": null
      },
      "clockOutEvent": {
        "dateTime": "2025-01-07T19:43:54.555Z",
        "isAtApprovedLocation": null,
        "notes": null
      },
      "breaks": [
        {
          "breakId": "BRK_d659f765-8c16-4a40-a6c8-2a1cf407b859",
          "notes": null,
          "start": {
            "dateTime": "2025-01-07T16:42:35.406Z",
            "isAtApprovedLocation": null,
            "notes": null
          },
          "end": {
            "dateTime": "2025-01-07T16:53:40.671Z",
            "isAtApprovedLocation": null,
            "notes": null
          }
        }
      ],
      "originalEntry": {
        "clockInEvent": {
          "dateTime": "2025-01-07T14:40:01.601Z",
          "isAtApprovedLocation": null,
          "notes": null
        },
        "clockOutEvent": {
          "dateTime": "2025-01-07T19:43:54.555Z",
          "isAtApprovedLocation": null,
          "notes": null
        },
        "breaks": [
          {
            "breakId": "BRK_d659f765-8c16-4a40-a6c8-2a1cf407b859",
            "notes": null,
            "start": {
              "dateTime": "2025-01-07T16:42:35.406Z",
              "isAtApprovedLocation": null,
              "notes": null
            },
            "end": {
              "dateTime": "2025-01-07T16:53:40.671Z",
              "isAtApprovedLocation": null,
              "notes": null
            }
          }
        ]
      },
      "createdBy": {
        "application": null,
        "device": null,
        "user": {
          "id": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
          "displayName": "Alice Bradford"
        }
      }
    },
    {
      "id": "TCK_3e74d9a1-f45f-4da3-95df-be72a8af448d",
      "createdDateTime": "2025-01-08T15:44:09.545Z",
      "lastModifiedDateTime": "2025-01-08T19:45:25.048Z",
      "userId": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
      "state": "clockedOut",
      "confirmedBy": "none",
      "notes": null,
      "lastModifiedBy": {
        "application": null,
        "device": null,
        "user": {
          "id": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
          "displayName": "Alice Bradford",
        }
      },
      "clockInEvent": {
        "dateTime": "2025-01-08T15:44:09.545Z",
        "isAtApprovedLocation": null,
        "notes": null
      },
      "clockOutEvent": {
        "dateTime": "2025-01-07T19:45:25.048Z",
        "isAtApprovedLocation": null,
        "notes": null
      },
      "breaks": [],
      "originalEntry": {
        "clockInEvent": {
          "dateTime": "2025-01-07T15:44:09.545Z",
          "isAtApprovedLocation": null,
          "notes": null
        },
        "clockOutEvent": {
          "dateTime": "2025-01-07T19:45:25.048Z",
          "isAtApprovedLocation": null,
          "notes": null
        },
        "breaks": []
      },
      "createdBy": {
        "application": null,
        "device": null,
        "user": {
          "id": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
          "displayName": "Alice Bradford",
        }
      }
    }
  ]
}
```
