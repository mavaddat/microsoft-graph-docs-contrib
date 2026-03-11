---
title: "recoveryPreviewJob: cancel"
description: "Cancel a preview job."
author: "mapamu"
ms.date: 03/04/2026
ms.localizationpriority: medium
ms.subservice: "entra-id"
doc_type: apiPageType
---

# recoveryPreviewJob: cancel

Namespace: microsoft.graph.entraRecoveryServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Cancel a running [recoveryJobBase](../resources/entrarecoveryservices-recoveryjobbase.md) object (either a preview or recovery job). The job must be in a non-terminal state (`initialized`, `calculating`, `loadingData`, or `running`). After cancellation, the job status changes to `abandoned`.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "entrarecoveryservices-recoverypreviewjob-cancel-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/entrarecoveryservices-recoverypreviewjob-cancel-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /directory/recovery/snapshots/{snapshotId}/recoveryPreviewJobs/{recoveryPreviewJobId}/cancel
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this action returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "recoverypreviewjobthis.cancel"
}
-->
``` http
POST https://graph.microsoft.com/beta/directory/recovery/snapshots/{snapshotId}/recoveryPreviewJobs/{recoveryPreviewJobId}/cancel
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true
}
-->
``` http
HTTP/1.1 204 No Content
```

