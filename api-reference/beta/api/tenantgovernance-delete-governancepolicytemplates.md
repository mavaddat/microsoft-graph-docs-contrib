---
title: "Delete governancePolicyTemplate"
description: "Delete a governance policy template."
author: "hafowler"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: apiPageType
---

# Delete governancePolicyTemplate

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Delete a [governancePolicyTemplate](../resources/tenantgovernance-governancepolicytemplate.md) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "tenantgovernanceservices-tenantgovernance-delete-governancepolicytemplates-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/tenantgovernance-tenantgovernance-delete-governancepolicytemplates-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
DELETE /directory/tenantGovernance/governancePolicyTemplates/{governancePolicyTemplateId}/$ref
DELETE /directory/tenantGovernance/governanceRequests/{governanceRequestId}/governancePolicyTemplate/$ref
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "delete_governancepolicytemplate"
}
-->
``` http
DELETE https://graph.microsoft.com/beta/directory/tenantGovernance/governancePolicyTemplates/{governancePolicyTemplateId}
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

