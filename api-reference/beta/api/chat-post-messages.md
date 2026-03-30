---
title: "Send message in a chat"
description: "Send a new message in a chat."
ms.localizationpriority: medium
author: "RamjotSingh"
ms.subservice: "teams"
doc_type: "apiPageType"
ms.date: 04/05/2024
---

# Send message in a chat

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Send a new [chatMessage](../resources/chatmessage.md) in the specified [chat](../resources/chat.md). This API cannot create a new chat; you must use the [list chats](chat-list.md) method to retrieve the ID of an existing chat before creating a chat message.

> **Note**: Using the regular create message flow for data migration is not recommended. For data migration scenarios, use the [import messages](#import-message) flow instead.

> **Note**: It is a violation of the [terms of use](/legal/microsoft-apis/terms-of-use) to use Microsoft Teams as a log file. Only send messages that people will read.

[!INCLUDE [national-cloud-support](../../includes/all-clouds.md)]

### Import message

This API can also be used to import messages into an existing chat during a migration session. To use this API as an import message API, the following conditions must be met:

- The request must be made in application context (app-only) with the **Teamwork.Migrate.All** application permission.
- The target chat must be in migration mode. To put a chat in migration mode, call [chat: startMigration](chat-startmigration.md).
- The **from** property must be specified to attribute the message to a user who belongs to the same tenant as the authenticated application.
- The **createdDateTime** property can be specified to set a custom timestamp for the imported message, subject to the following constraints:
  - The value must be greater than the **createdDateTime** of the target chat.
  - The value must not be in the future.

> [!NOTE]
> Only the application that called [startMigration](chat-startmigration.md) on the target chat can import messages into it. No other application can invoke this API on the chat until the owning application completes migration by calling [completeMigration](chat-completemigration.md).

> [!NOTE]
> Some imported messages may not be visible in the Teams client until migration is completed by calling [completeMigration](chat-completemigration.md) on the target chat.

For more information, see [Import third-party platform messages to Teams using Microsoft Graph](/microsoftteams/platform/graph-api/import-messages/import-external-messages-to-teams).

[!INCLUDE [national-cloud-support](../../includes/global-only.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "chat_post_messages" } -->
[!INCLUDE [permissions-table](../includes/permissions/chat-post-messages-permissions.md)]

## HTTP request

<!-- { "blockType": "ignored" } -->

```http
POST /chats/{chat-id}/messages
```

## Request headers

| Name          | Description   |
|:--------------|:--------------|
| Authorization | Bearer {code}. Required. |

## Request body

In the request body, supply a JSON representation of a [chatMessage](../resources/chatmessage.md) object.

## Response

If successful, this method returns a `201 Created` response code and a new [chatMessage](../resources/chatmessage.md) object in the response body.

## Examples

For a more comprehensive list of examples, see [Create chatMessage in a channel or a chat](chatmessage-post.md).

### Request

The following example shows a request.


# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "post_chatmessages_1",
  "sampleKeys": ["19:2da4c29f6d7041eca70b638b43d45437@thread.v2"]
}-->
```http
POST https://graph.microsoft.com/beta/chats/19:2da4c29f6d7041eca70b638b43d45437@thread.v2/messages
Content-type: application/json

{
  "body": {
     "content": "Hello world"
  }
}
```

# [C#](#tab/csharp)
[!INCLUDE [sample-code](../includes/snippets/csharp/post-chatmessages-1-csharp-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Go](#tab/go)
[!INCLUDE [sample-code](../includes/snippets/go/post-chatmessages-1-go-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/post-chatmessages-1-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/post-chatmessages-1-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PHP](#tab/php)
[!INCLUDE [sample-code](../includes/snippets/php/post-chatmessages-1-php-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PowerShell](#tab/powershell)
[!INCLUDE [sample-code](../includes/snippets/powershell/post-chatmessages-1-powershell-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Python](#tab/python)
[!INCLUDE [sample-code](../includes/snippets/python/post-chatmessages-1-python-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

### Response

The following example shows the response.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.chatMessage"
} -->

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#chats('19%3A2da4c29f6d7041eca70b638b43d45437%40thread.v2')/messages/$entity",
    "id": "1616991463150",
    "replyToId": null,
    "etag": "1616991463150",
    "messageType": "message",
    "createdDateTime": "2021-03-29T04:17:43.15Z",
    "lastModifiedDateTime": "2021-03-29T04:17:43.15Z",
    "lastEditedDateTime": null,
    "deletedDateTime": null,
    "subject": null,
    "summary": null,
    "chatId": "19:2da4c29f6d7041eca70b638b43d45437@thread.v2",
    "importance": "normal",
    "locale": "en-us",
    "webUrl": null,
    "channelIdentity": null,
    "onBehalfOf": null,
    "policyViolation": null,
    "eventDetail": null,
    "from": {
        "application": null,
        "device": null,
        "conversation": null,
        "user": {
            "id": "8ea0e38b-efb3-4757-924a-5f94061cf8c2",
            "displayName": "Robin Kline",
            "userIdentityType": "aadUser"
        }
    },
    "body": {
        "contentType": "text",
        "content": "Hello World"
    },
    "attachments": [],
    "mentions": [],
    "reactions": [],
    "messageHistory": []
}
```

### Example 2: Import message

> **Note**: The permission scope `Teamwork.Migrate.All` is required for this scenario. The target chat must be in migration mode.

#### Request

The following example shows how to import a message into a chat on behalf of a user using the `createdDateTime` and `from` keys in the request body.

<!-- {
  "blockType": "request",
  "name": "import_chatmessage",
  "sampleKeys": ["19:4b6bed8d24574f6a9e436813cb2617d8@thread.tacv2"]
}-->

```http
POST https://graph.microsoft.com/beta/chats/19:4b6bed8d24574f6a9e436813cb2617d8@thread.tacv2/messages

{
   "createdDateTime": "2019-02-04T19:58:15.511Z",
   "from": {
      "user": {
         "id": "8ea0e38b-efb3-4757-924a-5f94061cf8c2",
         "displayName": "Robin Kline",
         "userIdentityType": "aadUser"
      }
   },
   "body": {
      "contentType": "html",
      "content": "Hello World"
   }
}
```

#### Response

The following example shows the response.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.chatMessage"
} -->

```http
HTTP/1.1 200 OK

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#chats('19%3A4b6bed8d24574f6a9e436813cb2617d8%40thread.tacv2')/messages/$entity",
    "id": "1616991463150",
    "replyToId": null,
    "etag": "1616991463150",
    "messageType": "message",
    "createdDateTime": "2019-02-04T19:58:15.511Z",
    "lastModifiedDateTime": null,
    "deletedDateTime": null,
    "subject": null,
    "summary": null,
    "chatId": "19:4b6bed8d24574f6a9e436813cb2617d8@thread.tacv2",
    "importance": "normal",
    "locale": "en-us",
    "webUrl": null,
    "channelIdentity": null,
    "policyViolation": null,
    "eventDetail": null,
    "from": {
        "application": null,
        "device": null,
        "conversation": null,
        "user": {
            "id": "8ea0e38b-efb3-4757-924a-5f94061cf8c2",
            "displayName": "Robin Kline",
            "userIdentityType": "aadUser"
        }
    },
    "body": {
        "contentType": "html",
        "content": "Hello World"
    },
    "attachments": [],
    "mentions": [],
    "reactions": []
}
```

<!-- uuid: 16cd6b66-4b1a-43a1-adaf-3a886856ed98
2019-02-04 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create chatMessage",
  "keywords": "",
  "section": "documentation",
  "tocPath": "",
  "suppressions": [
  ]
}-->
