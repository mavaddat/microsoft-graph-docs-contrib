---
title: "Create teamworkSection"
description: "Create a new section in a user's teamwork."
author: "jsinghmokha"
ms.localizationpriority: medium
ms.subservice: "teams"
doc_type: apiPageType
ms.date: 03/08/2026
---

# Create teamworkSection

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Create a new [section](../resources/teamworksection.md) in a user's [teamwork](../resources/userteamwork.md).

[!INCLUDE [national-cloud-support](../../includes/all-clouds.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "userteamwork_post_sections" } -->
[!INCLUDE [permissions-table](../includes/permissions/userteamwork-post-sections-permissions.md)]

## HTTP request

<!-- { "blockType": "ignored" } -->
```http
POST /users/{user-id}/teamwork/sections
```

## Request headers

| Header | Value |
|:-------|:------|
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| If-Match | The ETag value of a previously retrieved **userTeamwork** resource. Required for optimistic concurrency control. |

## Request body

In the request body, supply a JSON representation of a [teamworkSection](../resources/teamworksection.md) object.

The following table lists the properties that you can set when you create a **teamworkSection**.

| Property | Type | Description |
|:---------|:-----|:------------|
| displayIcon | [sectionDisplayIcon](../resources/sectiondisplayicon.md) | The icon displayed for the section. Optional. The **skinTone** property of the icon can't be set and is derived from user settings. |
| displayName | String | The display name of the section. Required. Maximum length is 50 characters. |
| isExpanded | Boolean | Indicates whether the section is expanded in the user interface. Optional. The default value is `true`. |
| sortType | sectionSortType | The sort order of items in the section. Optional. The default value is `userDefinedCustomOrder`. The valid values for user-defined sections are: `mostRecent`, `unreadThenMostRecent`, `userDefinedCustomOrder`, `unknownFutureValue`. The `nameAlphabetical` member isn't valid for user-defined sections. |

## Response

If successful, this method returns a `201 Created` response code and a [teamworkSection](../resources/teamworksection.md) object in the response body.

## Examples

### Request

The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "create_teamworksection",
  "sampleKeys": ["10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f"]
}-->
```http
POST https://graph.microsoft.com/beta/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections
Content-type: application/json
If-Match: W/"123456"

{
  "displayName": "Project Alpha",
  "displayIcon": {
    "iconType": "🚀",
    "displayName": "Rocket"
  },
  "sortType": "mostRecent"
}
```

### Response

The following example shows the response.

>**Note:** The response object shown here might be shortened for readability.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.teamworkSection"
}-->
```http
HTTP/1.1 201 Created
Content-type: application/json
Location: https://graph.microsoft.com/beta/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/c3d4e5f6-a7b8-9012-cdef-123456789012

{
  "@odata.type": "#microsoft.graph.teamworkSection",
  "@odata.etag": "W/\"123457\"",
  "id": "c3d4e5f6-a7b8-9012-cdef-123456789012",
  "displayName": "Project Alpha",
  "displayIcon": {
    "iconType": "🚀",
    "displayName": "Rocket",
    "contentUrl": null,
    "skinTone": null
  },
  "sectionType": "userDefined",
  "sortType": "mostRecent",
  "isExpanded": true,
  "isHierarchicalViewEnabled": false,
  "createdDateTime": "2026-03-08T10:00:00Z",
  "lastModifiedDateTime": "2026-03-08T10:00:00Z"
}
```

<!-- uuid: a7b89012-3456-789a-bcde-f01234567890
2026-03-08 00:00:00 UTC -->
<!--
{
  "type": "#page.annotation",
  "description": "Create teamworkSection",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}
-->
