---
title: "cloudPC: bulkResize (deprecated)"
description: "Bulk resizes a set of Cloud PC devices."
author: "liguojing929"
ms.localizationpriority: medium
ms.subservice: "cloud-pc"
doc_type: apiPageType
ms.date: 06/20/2024
---

# cloudPC: bulkResize (deprecated)

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

> [!CAUTION]
> This API is deprecated and will stop returning data on February 28, 2025. Going forward, use the [cloudPcBulkResize](/graph/api/resources/cloudpcbulkresize?view=graph-rest-beta&preserve-view=true) resource and its supported APIs.

Perform a bulk resize action to resize a group of [cloudPCs](../resources/cloudpc.md) that successfully pass [validation](cloudpc-validatebulkresize.md). If any devices can't be resized, those devices indicate "resize failed". The remaining devices are `provisioned` for the resize process.

[!INCLUDE [national-cloud-support](../../includes/global-us.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "cloudpc_bulkresize" } -->
[!INCLUDE [permissions-table](../includes/permissions/cloudpc-bulkresize-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->

``` http
POST /deviceManagement/virtualEndpoint/cloudPCs/bulkResize
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

|Property|Type|Description|
|:---|:---|:---|
|cloudPcIds|String collection|A list of the IDs for the Cloud PC devices that are to be resized.|
|targetServicePlanId|String|The configuration for resizing, including the desired number of virtual CPUs (vCPU) and storage size.|

## Response

If successful, this method returns a `200 OK` response code and the requested [cloudPcRemoteActionResult](../resources/cloudpcremoteactionresult.md) object collection in the response body.

## Examples

### Request

The following example shows a request.

# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "cloudpc.bulkResize"
}
-->
``` http
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/cloudPCs/bulkResize
Content-Type: application/json

{
  "cloudPcIds": [
    "30d0e128-de93-41dc-89ec-33d84bb662a0", 
    "7c82a3e3-9459-44e4-94d9-b92f93bf78dd"
  ],
  "targetServicePlanId": "662009bc-7732-4f6f-8726-25883518b33e"
}
```

# [C#](#tab/csharp)
[!INCLUDE [sample-code](../includes/snippets/csharp/cloudpcbulkresize-csharp-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [CLI](#tab/cli)
[!INCLUDE [sample-code](../includes/snippets/cli/cloudpcbulkresize-cli-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Go](#tab/go)
[!INCLUDE [sample-code](../includes/snippets/go/cloudpcbulkresize-go-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/cloudpcbulkresize-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/cloudpcbulkresize-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PHP](#tab/php)
[!INCLUDE [sample-code](../includes/snippets/php/cloudpcbulkresize-php-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Python](#tab/python)
[!INCLUDE [sample-code](../includes/snippets/python/cloudpcbulkresize-python-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

### Response

The following example shows the response.

<!-- {
  "blockType": "response",
  "@odata.type": "Collection(microsoft.graph.cloudPcRemoteActionResult)",
  "name": "cloudpc.bulkResize"
}
-->

``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "value": [
      {
        "@odata.type":"https://graph.microsoft.com/beta/$metadata#microsoft.graph.cloudPcRemoteActionResult",
        "actionName": "Resize",
        "actionState": "pending",
        "startDateTime": "2021-06-23T09:28:32.8260335Z",
        "lastUpdatedDateTime": "2021-06-23T09:28:32.8260338Z",
        "cloudPcId": "30d0e128-de93-41dc-89ec-33d84bb662a0",
        "managedDeviceId": "bdc8e6dd-0455-4412-83d9-c818664fe1f1",
        "statusDetails": null,
        "statusDetail": null
      },
      {
        "@odata.type":"https://graph.microsoft.com/beta/$metadata#microsoft.graph.cloudPcRemoteActionResult",
        "actionName": "Resize",
        "actionState": "failed",
        "startDateTime": "2021-06-23T09:28:32.8260335Z",
        "lastUpdatedDateTime": "2021-06-23T09:28:32.8260338Z",
        "cloudPcId": "7c82a3e3-9459-44e4-94d9-b92f93bf78dd",
        "managedDeviceId": "e87f50c7-fa7f-4687-aade-dd45f3d65970",
        "statusDetails": null,
        "statusDetail": null
      }
    ]
}
```
