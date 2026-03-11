---
title: "Get relatedTenant"
description: "Read the properties and relationships of microsoft.graph.tenantGovernanceServices.relatedTenant object."
author: "akhil-potturi"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: apiPageType
---

# Get relatedTenant

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Read the properties and relationships of [microsoft.graph.tenantGovernanceServices.relatedTenant](../resources/tenantgovernance-relatedtenant.md) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "tenantgovernance-relatedtenant-get-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/tenantgovernance-relatedtenant-get-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /directory/tenantGovernance/relatedTenants/{relatedTenantId}
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](/graph/query-parameters).

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.tenantGovernanceServices.relatedTenant](../resources/tenantgovernance-relatedtenant.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "get_relatedtenant"
}
-->
``` http
GET https://graph.microsoft.com/beta/directory/tenantGovernance/relatedTenants/{relatedTenantId}
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.tenantGovernanceServices.relatedTenant"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.relatedTenant",
  "id": "a3b7c912-45de-4f8a-b2c1-8e9f0a1b2c3d",
  "createdDateTime": "2026-02-15T05:34:29.4426526Z",
  "b2BRegistrationMetrics": {
    "initial": {
      "createdDateTime": "2026-02-13T20:54:25Z",
      "watermarkDateTime": "2026-02-12T00:00:00Z",
      "inboundTotalUsers": 1,
      "outboundTotalUsers": 0
    },
    "recent": {
      "updateDateTime": "2026-02-16T23:13:49Z",
      "watermarkDateTime": "2026-02-15T00:00:00Z",
      "inboundTotalUsers": 0,
      "outboundTotalUsers": 0
    }
  },
  "b2BSignInActivityMetrics": {
    "initial": {
      "createdDateTime": "2026-02-17T08:08:23Z",
      "watermarkDateTime": "2026-02-15T00:00:00Z",
      "inboundMonthlyTotalUsers": 1,
      "outboundMonthlyTotalUsers": 0,
      "inboundMonthlyTotalApplications": 10,
      "outboundMonthlyTotalApplications": 0
    },
    "recent": {
      "updateDateTime": "2026-02-17T08:08:23Z",
      "watermarkDateTime": "2026-02-15T00:00:00Z",
      "inboundMonthlyTotalUsers": 1,
      "outboundMonthlyTotalUsers": 0,
      "inboundMonthlyTotalApplications": 10,
      "outboundMonthlyTotalApplications": 0
    }
  },
  "appB2BSignInActivityMetrics": {
    "initial": {
      "createdDateTime": "2026-02-17T08:08:23Z",
      "watermarkDateTime": "2026-02-15T00:00:00Z",
      "inboundMonthlyTotalUsers": 1,
      "outboundMonthlyTotalUsers": 0,
      "inboundMonthlyTotalApplications": 1,
      "outboundMonthlyTotalApplications": 0
    },
    "recent": {
      "updateDateTime": "2026-02-17T08:08:23Z",
      "watermarkDateTime": "2026-02-15T00:00:00Z",
      "inboundMonthlyTotalUsers": 1,
      "outboundMonthlyTotalUsers": 0,
      "inboundMonthlyTotalApplications": 1,
      "outboundMonthlyTotalApplications": 0
    }
  },
  "multiTenantApplicationMetrics": null,
  "billingMetrics": null
}
```

