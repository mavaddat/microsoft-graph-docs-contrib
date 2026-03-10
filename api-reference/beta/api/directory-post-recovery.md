---
title: "Create recovery"
description: "Create a new recovery object."
author: "**TODO: Provide GitHub Name. See [topic-level metadata reference](https://eng.ms/docs/products/microsoft-graph-service/microsoft-graph/document-apis/metadata)**"
ms.date: 03/04/2026
ms.localizationpriority: medium
ms.subservice: "**TODO: Add MS subservice. See [topic-level metadata reference](https://eng.ms/docs/products/microsoft-graph-service/microsoft-graph/document-apis/metadata)**"
doc_type: apiPageType
---

# Create recovery

Namespace: microsoft.graph.entraRecoveryServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Create a new recovery object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "directory-post-recovery-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/directory-post-recovery-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST ** Collection URI for microsoft.graph.entraRecoveryServices.recovery not found
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.entraRecoveryServices.recovery](../resources/entrarecoveryservices-recovery.md) object.

You can specify the following properties when creating a **recovery**.

**TODO: Remove properties that don't apply**
|Property|Type|Description|
|:---|:---|:---|



## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.entraRecoveryServices.recovery](../resources/entrarecoveryservices-recovery.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "create_recovery_from_"
}
-->
``` http
POST https://graph.microsoft.com/beta** Collection URI for microsoft.graph.entraRecoveryServices.recovery not found
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.recovery"
}
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.entraRecoveryServices.recovery"
}
-->
``` http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.recovery",
  "id": "f1a6d5cd-dfa1-a1a3-fbcb-fdcc6f3e1677"
}
```

