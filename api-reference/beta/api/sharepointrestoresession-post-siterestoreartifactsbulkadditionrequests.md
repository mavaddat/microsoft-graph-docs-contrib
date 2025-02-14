---
title: "Create siteRestoreArtifactsBulkAdditionRequests"
description: "Create a new siteRestoreArtifactsBulkAdditionRequest object associated with a sharePointRestoreSession."
author: "vidula-verma"
ms.localizationpriority: medium
ms.subservice: "m365-backup-storage"
doc_type: apiPageType
ms.date: 12/11/2024
---

# Create siteRestoreArtifactsBulkAdditionRequests

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Create a new [siteRestoreArtifactsBulkAdditionRequest](../resources/siterestoreartifactsbulkadditionrequest.md) object associated with a [sharePointRestoreSession](../resources/sharepointrestoresession.md).

The initial status upon creation of the restore session is `active`. When all the sites are added to the corresponding SharePoint restore session and the restore session is activated, the status becomes `completed`. If any failures are encountered during resource resolution, the status of the restore session becomes `completedWithErrors`.

[!INCLUDE [national-cloud-support](../../includes/global-only.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "sharepointrestoresession-post-siterestoreartifactsbulkadditionrequests-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/sharepointrestoresession-post-siterestoreartifactsbulkadditionrequests-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /solutions/backupRestore/sharePointRestoreSessions/{sharePointRestoreSessionId}/siteRestoreArtifactsBulkAdditionRequests
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

In the request body, supply a JSON representation of the [siteRestoreArtifactsBulkAdditionRequest](../resources/siterestoreartifactsbulkadditionrequest.md) object.

## Response

If successful, this method returns a `201 Created` response code and a [siteRestoreArtifactsBulkAdditionRequest](../resources/siterestoreartifactsbulkadditionrequest.md) object in the response body.

## Examples

### Request

The following example shows a request that adds a list of sites to the specified SharePoint restore session in a bulk operation.

# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "create_siterestoreartifactsbulkadditionrequest_from_"
}
-->
``` http
POST https://graph.microsoft.com/beta/solutions/backupRestore/sharePointRestoreSessions/959ba739-70b5-43c4-8c90-b2c22014f18b/siteRestoreArtifactsBulkAdditionRequests
Content-Type: application/json

{
  "displayName": "SPO-BulkRestoreArtifacts",
  "siteWebUrls": [
    "https: //contoso1.sharepoint.com",
    "https: //contoso2.sharepoint.com",
    "https: //contoso3.sharepoint.com"
  ],
  "protectionTimePeriod": {
    "startDateTime": "2024-01-01T00:00:00Z",
    "endDateTime": "2024-01-08T00:00:00Z"
  },
  "destinationType": "new",
  "tags": "fastRestore",
  "restorePointPreference": "latest"
}
```

# [C#](#tab/csharp)
[!INCLUDE [sample-code](../includes/snippets/csharp/create-siterestoreartifactsbulkadditionrequest-from--csharp-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [CLI](#tab/cli)
[!INCLUDE [sample-code](../includes/snippets/cli/create-siterestoreartifactsbulkadditionrequest-from--cli-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Go](#tab/go)
[!INCLUDE [sample-code](../includes/snippets/go/create-siterestoreartifactsbulkadditionrequest-from--go-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/create-siterestoreartifactsbulkadditionrequest-from--java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/create-siterestoreartifactsbulkadditionrequest-from--javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PHP](#tab/php)
[!INCLUDE [sample-code](../includes/snippets/php/create-siterestoreartifactsbulkadditionrequest-from--php-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [PowerShell](#tab/powershell)
[!INCLUDE [sample-code](../includes/snippets/powershell/create-siterestoreartifactsbulkadditionrequest-from--powershell-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Python](#tab/python)
[!INCLUDE [sample-code](../includes/snippets/python/create-siterestoreartifactsbulkadditionrequest-from--python-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

### Response

The following example shows the response.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.siteRestoreArtifactsBulkAdditionRequest"
}
-->
``` http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "/solutions/backupRestore/$metadata#siteRestoreArtifactsBulkAdditionRequest/$entity",
  "id": "4437afcf-e520-463c-90a7-ca96401d8039",
  "destinationType": "new",
  "tags": "fastRestore",
  "restorePointPreference": "latest",
  "displayName": "SPO-BulkRestoreArtifacts",
  "status": "active",
  "createdDateTime": "2024-12-03T07:47:57.6011358Z",
  "lastModifiedDateTime": "2024-12-03T07:47:57.6011358Z",
  "siteWebUrls": [],
  "protectionTimePeriod": {
    "startDateTime": "2024-01-01T00:00:00Z",
    "endDateTime": "2024-01-08T00:00:00Z"
  },
  "createdBy": {
    "user": {
      "identity": "fb70be35-8c8e-4c8a-b55d-f8cd95c5e23a"
    }
  },
  "lastModifiedBy": {
    "user": {
      "identity": "fb70be35-8c8e-4c8a-b55d-f8cd95c5e23a"
    }
  }
}
```
