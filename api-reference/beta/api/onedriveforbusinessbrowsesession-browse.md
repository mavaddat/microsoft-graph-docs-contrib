---
title: "oneDriveForBusinessBrowseSession: browse"
description: "Browse the files and folder within the oneDriveForBusiness browseSession"
author: "manikantsinghms"
ms.date: 09/23/2025
ms.localizationpriority: medium
ms.subservice: "m365-backup-storage"
doc_type: apiPageType
---

# oneDriveForBusinessBrowseSession: browse

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Browse API call let you browse files and folder present within a [BrowseSession](../resources/browsesessionbase.md).

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

|Name|Description|5-
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Client should make request with empty body to get the list of the top browsable locations.

In the request body, supply a JSON representation of the following parameters.

|Parameter|Type|Description|
|:---|:---|:---|
|browseLocationItemKey|String|The item key of the location that you want to browse. Optional.|
|browseResourceType|[browsableResourceType](../resources/enums.md#browsableresourcetype-values)|The type of the browsable location. Optional. The possible values are `none`, `site`, `documentLibrary`, `folder` and `unknownFutureValue`. Optional.|
|filter|String|Contains the [searchExpression](../api/onedriveforbusinessbrowsesession-browse.md#search-expression-examples). Optional.|
|orderBy|[browseQueryOrder](../resources/enums.md#browsequeryorder-values)|Specifies the order by which response should be ordered. Optional.|

## Response

If successful, this function returns a `200 OK` response code and a [browseQueryResponseItem](../resources/browsequeryresponseitem.md) collection in the response body.

### Search expression examples
The following table shows the possible formats for the filter expression.
Filter is supported only on `name` property.

| Property                                 | Operator                                | Example                                                                  |
| ------------------------------------------- | ----------------------------------------------------------------- | --------------------------------------------------- |
| `name`      | `-contains` |   `(name -contains 'contoso')`  |

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "onedriveforbusinessbrowsesessionthis.browse"
}
-->
``` http
POST /solutions/backupRestore/oneDriveForBusinessBrowseSessions/{oneDriveForBusinessBrowseSessionId}/browse

```
<!-- 
To be removed
GET https://graph.microsoft.com/beta/solutions/backupRestore/oneDriveForBusinessBrowseSessions/{oneDriveForBusinessBrowseSessionId}/browse(nextFetchToken='parameterValue')
 -->


### Response

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
  "value": [
    {
      "@odata.type": "microsoft.graph.browseQueryResponseItem"
    }
  ]
}
```

