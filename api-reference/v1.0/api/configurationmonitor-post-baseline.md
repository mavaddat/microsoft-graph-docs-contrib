---
title: "Create configurationBaseline"
description: "Create a new configurationBaseline object."
author: "**TODO: Provide GitHub Name. See [topic-level metadata reference](https://eng.ms/docs/products/microsoft-graph-service/microsoft-graph/document-apis/metadata)**"
ms.date: 03/17/2026
ms.localizationpriority: medium
ms.subservice: "**TODO: Add MS subservice. See [topic-level metadata reference](https://eng.ms/docs/products/microsoft-graph-service/microsoft-graph/document-apis/metadata)**"
doc_type: apiPageType
---

# Create configurationBaseline

Namespace: microsoft.graph



Create a new configurationBaseline object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "configurationmonitor-post-baseline-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/configurationmonitor-post-baseline-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /admin/configurationManagement/configurationSnapshots
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

In the request body, supply a JSON representation of the [configurationBaseline](../resources/configurationbaseline.md) object.

You can specify the following properties when creating a **configurationBaseline**.

**TODO: Remove properties that don't apply**
|Property|Type|Description|
|:---|:---|:---|
|displayName|String|**TODO: Add Description** Required.|
|description|String|**TODO: Add Description** Required.|
|parameters|[baselineParameter](../resources/baselineparameter.md) collection|**TODO: Add Description** Required.|
|resources|[baselineResource](../resources/baselineresource.md) collection|**TODO: Add Description** Required.|



## Response

If successful, this method returns a `201 Created` response code and a [configurationBaseline](../resources/configurationbaseline.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "create_configurationbaseline_from_"
}
-->
``` http
POST https://graph.microsoft.com/v1.0/admin/configurationManagement/configurationSnapshots
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.configurationBaseline",
  "displayName": "String",
  "description": "String",
  "parameters": [
    {
      "@odata.type": "microsoft.graph.baselineParameter"
    }
  ],
  "resources": [
    {
      "@odata.type": "microsoft.graph.baselineResource"
    }
  ]
}
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.configurationBaseline"
}
-->
``` http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.configurationBaseline",
  "id": "51511c1b-8700-1ba8-d667-0891eda8015f",
  "displayName": "String",
  "description": "String",
  "parameters": [
    {
      "@odata.type": "microsoft.graph.baselineParameter"
    }
  ],
  "resources": [
    {
      "@odata.type": "microsoft.graph.baselineResource"
    }
  ]
}
```

