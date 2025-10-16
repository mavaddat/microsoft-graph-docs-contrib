---
title: "cloudPCSnapshot: importSnapshot"
description: "Import the snapshot from the customer-managed storage account using the provided information, and store it in the Azure storage account within the Cloud PC service on behalf of the customer."
author: "hyc3z"
ms.localizationpriority: medium
ms.subservice: "cloud-pc"
doc_type: apiPageType
ms.date: 10/10/2025
---

# cloudPCSnapshot: importSnapshot
Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Import the [snapshot](../resources/cloudpcsnapshot.md) from the customer-managed storage account using the provided information, and store it in the Azure storage account within the Cloud PC service on behalf of the customer. 

To provision a new Cloud PC for a licensed user, import a valid .vhd snapshot from a customer-managed storage account into the Azure storage account used by the Cloud PC service.

## Permissions
Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "cloudpcsnapshot_importsnapshot" } -->
[!INCLUDE [permissions-table](../includes/permissions/cloudpcsnapshot-importsnapshot-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /deviceManagement/virtualEndpoint/snapshots/importSnapshot
```

## Request headers
|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body
In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this method.

| Parameter | Type | Description |
|:---|:---|:---|
| assignedUserId     | String   | The unique identifier of the user assigned to the snapshot, who uses the imported snapshot to provision a new Cloud PC. |
| sourceFiles   | [cloudPcSnapshotImportActionDetail](../resources/cloudpcsnapshotimportactiondetail.md) collection  |Detailed source information for the files to be imported. |

## Response

If successful, this method returns a `200 OK` response code and a [cloudPcSnapshotImportActionResult](../resources/cloudpcsnapshotimportactionresult.md) object in the response body.

## Examples

### Request

The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "post_importsnapshot"
}
-->
``` http
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/snapshots/importSnapshot
```

### Response

The following example shows the response.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.cloudPcSnapshotImportActionResult"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.cloudPcSnapshotImportActionResult",
  "filename": "snapshotForCloudPc",
  "usageStatus": "notUsed",
  "importStatus": "inProgress",
  "assignedUserPrincipalName": "snapshot@contoso.com",
  "policyName": "Test_ProvisioningPolicy",
  "startDateTime": "2025-01-13T15:13:14Z",
  "endDateTime": null,
  "additionalDetail": null
}
```

