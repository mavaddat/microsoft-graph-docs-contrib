---
title: "sharePointBrowseSession: browse"
description: "Browse the files and folders within the sharepointBrowseSession"
author: "manikantsinghms"
ms.date: 09/23/2025
ms.localizationpriority: medium
ms.subservice: "m365-backup-storage"
doc_type: apiPageType
---

# sharePointBrowseSession: browse

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Browse the files and folders within the [sharePointBrowseSession](../resources/sharepointbrowsesession.md).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "sharepointbrowsesession-browse-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/sharepointbrowsesession-browse-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /solutions/backupRestore/sharePointBrowseSessions/{sharePointBrowseSessionId}/browse
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Users should make a request with an empty body to get the list of the top browsable locations.

In the request body, supply a JSON representation of the following parameters.

|Parameter|Type|Description|
|:---|:---|:---|
|browseLocationItemKey|String|The item key of the location that you want to browse. Optional.|
|browseResourceType|[browsableResourceType](../resources/enums.md#browsableresourcetype-values)|The type of the browsable location. Optional. The possible values are `none`, `site`, `documentLibrary`, `folder`, and `unknownFutureValue`. Optional.|
|filter|String|Contains the search expression. Optional.|
|orderBy|[browseQueryOrder](../resources/enums.md#browsequeryorder-values)|Specifies the order by which response should be ordered. Optional.|

The following table shows examples of possible formats for the filter expression. The filter is supported only on the `name` property.

|Property| Operator| Example|
|:---|:---|:---|
| `name` | `-contains` | `(name -contains 'contoso')` |

## Response

If successful, this function returns a `200 OK` response code and a [browseQueryResponseItem](../resources/browsequeryresponseitem.md) collection in the response body.

## Examples

### Example 1: Get top browsable locations

#### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "sharepointbrowsesessionthis.browse.empty"
}
-->
``` http
POST https://graph.microsoft.com/beta/solutions/backupRestore/sharePointBrowseSessions/m_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE/browse
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
            "itemKey": "f3846f8d-80a6-4480-ae20-5966ebdf2009,26380145-c085-4772-b5ef-94de6bc9447e",
            "name": "Communication site",
            "webUrl": "https://contoso.sharepoint.com",
            "type": "site"
        }
    ]
}
```

### Example 2: Browse a specify resource

#### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "sharepointbrowsesessionthis.browse.body"
}
-->
``` http
POST https://graph.microsoft.com/beta/solutions/backupRestore/sharePointBrowseSessions/m_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE/browse
Content-Type: application/json

{
    "browseLocationItemKey": "f3846f8d-80a6-4480-ae20-5966ebdf2009,26380145-c085-4772-b5ef-94de6bc9447e",
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
            "itemKey": "f3846f8d-80a6-4480-ae20-5966ebdf2009,26380145-c085-4772-b5ef-94de6bc9447e,3be2f282-276a-4a1a-8db0-8bf0849df84d",
            "name": "Documents",
            "webUrl": "https://contoso.sharepoint.com/Shared Documents",
            "type": "documentLibrary",
            "itemsCount": 205
        }
    ]
}
```
