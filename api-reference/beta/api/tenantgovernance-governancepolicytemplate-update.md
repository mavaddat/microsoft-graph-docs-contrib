---
title: "Update governancePolicyTemplate"
description: "Update the properties of a governance policy template."
author: "hafowler"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: apiPageType
---

# Update governancePolicyTemplate

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Update the properties of a [governancePolicyTemplate](../resources/tenantgovernance-governancepolicytemplate.md) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "tenantgovernanceservices-governancepolicytemplate-update-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/tenantgovernance-governancepolicytemplate-update-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
PATCH /directory/tenantGovernance/governancePolicyTemplates/{governancePolicyTemplateId}
PATCH /directory/tenantGovernance/governanceRequests/{governanceRequestId}/governancePolicyTemplate
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

[!INCLUDE [table-intro](../../includes/update-property-table-intro.md)]


**TODO: Remove properties that don't apply**
|Property|Type|Description|
|:---|:---|:---|
|displayName|String|**TODO: Add Description** Required.|
|description|String|**TODO: Add Description** Required.|
|governedTenantCanTerminate|Boolean|**TODO: Add Description** Required.|
|version|String|**TODO: Add Description** Required.|
|createdDateTime|DateTimeOffset|**TODO: Add Description** Required.|
|lastModifiedDateTime|DateTimeOffset|**TODO: Add Description** Required.|
|multiTenantApplicationsToProvision|[microsoft.graph.tenantGovernanceServices.multiTenantApplicationsToProvision](../resources/tenantgovernance-multitenantapplicationstoprovision.md) collection|**TODO: Add Description** Required.|
|delegatedAdministrationRoleAssignments|[microsoft.graph.tenantGovernanceServices.delegatedAdministrationRoleAssignment](../resources/tenantgovernance-delegatedadministrationroleassignment.md) collection|**TODO: Add Description** Required.|



## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.tenantGovernanceServices.governancePolicyTemplate](../resources/tenantgovernance-governancepolicytemplate.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "update_governancepolicytemplate"
}
-->
``` http
PATCH https://graph.microsoft.com/beta/directory/tenantGovernance/governancePolicyTemplates/{governancePolicyTemplateId}
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.governancePolicyTemplate",
  "displayName": "String",
  "description": "String",
  "governedTenantCanTerminate": "Boolean",
  "version": "String",
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
HTTP/1.1 200 OK
Content-Type: application/json

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
```

