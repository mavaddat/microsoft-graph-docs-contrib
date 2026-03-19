---
title: "List configurationSnapshots"
description: "Get a list of the configurationBaseline objects that represent configuration snapshots."
author: "swatyario"
ms.date: 01/19/2026
ms.localizationpriority: medium
ms.subservice: "tenant-administration"
doc_type: apiPageType
---

# List configurationSnapshots

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get a list of [configurationBaseline](../resources/configurationbaseline.md) objects that represent configuration snapshots and their properties.

[!INCLUDE [national-cloud-support](../../includes/global-only.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "configurationmanagement_list_configurationsnapshots" } -->
[!INCLUDE [permissions-table](../includes/permissions/configurationmanagement-list-configurationsnapshots-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /admin/configurationManagement/configurationSnapshots
```

## Optional query parameters

This method supports the `$select`, `$filter`, `$orderBy`, and `$top` OData query parameters to help customize the response. For general information, see [OData query parameters](/graph/query-parameters).

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [configurationBaseline](../resources/configurationbaseline.md) objects in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "list_configurationsnapshots"
}
-->
``` http
GET https://graph.microsoft.com/beta/admin/configurationManagement/configurationSnapshots
```

### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "Collection(microsoft.graph.configurationBaseline)"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#admin/configurationManagement/configurationSnapshots",
  "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET admin/configurationManagement/configurationSnapshots?$select=description,displayName",
  "value": [
    {
      "id": "5b15be20-897f-4b79-85a6-97871c708f6f",
      "displayName": "Demo Baseline",
      "description": "This is a baseline with SharedMailbox, AcceptedDomain and MailContact",
      "parameters": [],
      "resources": [
        {
          "displayName": "TestSharedMailbox Resource",
          "resourceType": "microsoft.exchange.sharedmailbox",
          "properties": {
            "DisplayName": "TestSharedMailbox",
            "Alias": "testSharedMailbox",
            "Identity": "TestSharedMailbox",
            "Ensure": "Present"
          }
        },
        {
          "displayName": "Accepted Domain",
          "resourceType": "microsoft.exchange.accepteddomain",
          "properties": {
            "Identity": "contoso.onmicrosoft.com",
            "DomainType": "InternalRelay",
            "Ensure": "Present"
          }
        }
      ]
    }
  ]
}
```
