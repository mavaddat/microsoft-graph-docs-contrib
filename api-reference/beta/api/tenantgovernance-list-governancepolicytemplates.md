---
title: "List governancePolicyTemplates"
description: "Get a list of governance policy templates."
author: "hafowler"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: apiPageType
---

# List governancePolicyTemplates

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Get a list of the [governancePolicyTemplate](../resources/tenantgovernance-governancepolicytemplate.md) objects and their properties. Policy templates define the configuration that will be applied when establishing governance relationships.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "tenantgovernanceservices-tenantgovernance-list-governancepolicytemplates-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/tenantgovernance-list-governancepolicytemplates-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /directory/tenantGovernance/governancePolicyTemplates
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

If successful, this method returns a `200 OK` response code and a collection of [governancePolicyTemplate](../resources/governancepolicytemplate.md) objects in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "list_governancepolicytemplate"
}
-->
``` http
GET https://graph.microsoft.com/beta/directory/tenantGovernance/governancePolicyTemplates
```


### Response

The following example shows the response.
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.tenantGovernanceServices.governancePolicyTemplate"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.tenantGovernanceServices.governancePolicyTemplate",
      "id": "fa0c9c2e-b7c4-4468-e737-6c03920c6e3f",
      "displayName": "String",
      "description": "String",
      "governedTenantCanTerminate": "Boolean",
      "version": "String",
      "createdDateTime": "String (timestamp)",
      "lastModifiedDateTime": "String (timestamp)",
      "multiTenantApplicationsToProvision": [
        {
          "@odata.type": "microsoft.graph.tenantGovernanceServices.multiTenantApplicationsToProvision"
        }
      ],
      "delegatedAdministrationRoleAssignments": [
        {
          "@odata.type": "microsoft.graph.tenantGovernanceServices.delegatedAdministrationRoleAssignment"
        }
      ]
    }
  ]
}
```

