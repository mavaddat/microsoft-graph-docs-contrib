---
title: "oneDriveForBusinessBrowseSession: browse"
description: "Browse the files and folders within the oneDriveForBusinessBrowseSession."
author: "manikantsinghms"
ms.date: 09/23/2025
ms.localizationpriority: medium
ms.subservice: "m365-backup-storage"
doc_type: apiPageType
---

# oneDriveForBusinessBrowseSession: browse

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Browse the files and folders within the [oneDriveForBusinessBrowseSession](../resources/onedriveforbusinessbrowsesession.md).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "onedriveforbusinessbrowsesession-browse-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/onedriveforbusinessbrowsesession-browse-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /solutions/backupRestore/oneDriveForBusinessBrowseSessions/{oneDriveForBusinessBrowseSessionId}/browse
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

### Get top browsable locations

In the request body, supply an empty JSON object `{}` for this method to get the list of the top browsable locations.

### Browse a specify scope

In the request body, supply a JSON representation of the following parameters.

|Parameter|Type|Description|
|:---|:---|:---|
|browseLocationItemKey|String|The item key of the location that you want to browse. Optional.|
|browseResourceType|[browsableResourceType](../resources/enums.md#browsableresourcetype-values)|The type of the browsable location. The possible values are: `none`, `site`, `documentLibrary`, `folder`, `unknownFutureValue`. Optional.|
|filter|String|The search expression. Optional.|
|orderBy|[browseQueryOrder](../resources/enums.md#browsequeryorder-values)|Specifies the order in which the response is returned. Optional.|

The following table shows examples of possible formats for the **filter** expression. The filter is supported only on the **name** property.

|Property| Operator| Example|
|:---|:---|:---|
| name|`-contains`|`(name -contains 'contoso')`|

## Response

If successful, this function returns a `200 OK` response code and a collection of [browseQueryResponseItem](../resources/browsequeryresponseitem.md) objects in the response body.

## Examples

### Example 1: Get top browsable locations

The following example shows how to get the top browsable locations.

#### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "onedriveforbusinessbrowsesessionthis.browse.empty"
}
-->
``` http
POST https://graph.microsoft.com/beta/solutions/backupRestore/oneDriveForBusinessBrowseSessions/K74iLNw55YTzbgnba0zxZROipFxnManccFpzecIrjuaypwA/browse

{}

```

#### Response

The following example shows the response.

>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "Collection(microsoft.graph.browseQueryResponseItem)"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection(microsoft.graph.browseQueryResponseItem)",
  "@odata.count": 1,
  "value": [
    {
      "itemKey": "18473961-eedf-4151-94a7-fd8eb4aec0d7,62ff7090-d987-4711-9d5c-74c9452a192f",
      "name": "user0",
      "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com",
      "type": "site"
    }
  ]
}
```

### Example 2: Browse a specify resource

The following example shows how to specify the payload to browse specific files and folders.

#### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "onedriveforbusinessbrowsesessionthis.browse.body"
}
-->
``` http
POST https://graph.microsoft.com/beta/solutions/backupRestore/oneDriveForBusinessBrowseSessions/K74iLNw55YTzbgnba0zxZROipFxnManccFpzecIrjuaypwA/browse
Content-Type: application/json

{
  "browseLocationItemKey": "18473961-eedf-4151-94a7-fd8eb4aec0d7,62ff7090-d987-4711-9d5c-74c9452a192f",
  "browseResourceType": "site"
}
```

#### Response

The following example shows the response.

>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "Collection(microsoft.graph.browseQueryResponseItem)"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection(microsoft.graph.browseQueryResponseItem)",
  "@odata.count": 1,
  "value": [
    {
      "itemKey": "18473961-eedf-4151-94a7-fd8eb4aec0d7,62ff7090-d987-4711-9d5c-74c9452a192f,1c99fa35-f265-4d7e-88d1-37d83752b3a3",
      "name": "Documents",
      "webUrl": "https://contoso-my.sharepoint.com/personal/user0_contoso_onmicrosoft_com/Documents",
      "type": "documentLibrary",
      "itemsCount": 3
    }
  ]
}
```
