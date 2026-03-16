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
PATCH /directory/tenantGovernance/governancePolicyTemplates/default
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

[!INCLUDE [table-intro](../../includes/update-property-table-intro.md)]


|Property|Type|Description|
|:---|:---|:---|
|displayName|String|The display name of the policy template. |
|description|String|A description of the policy template.|
|multiTenantApplicationsToProvision|[microsoft.graph.tenantGovernanceServices.multiTenantApplicationsToProvision](../resources/tenantgovernance-multitenantapplicationstoprovision.md) collection|A collection of multitenant applications to be provisioned in the governed tenant when the governance relationship is established. |
|delegatedAdministrationRoleAssignments|[microsoft.graph.tenantGovernanceServices.delegatedAdministrationRoleAssignment](../resources/tenantgovernance-delegatedadministrationroleassignment.md) collection|A collection of delegated administration role assignments to be applied in the governed tenant when the governance relationship is established. |



## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.tenantGovernanceServices.governancePolicyTemplate](../resources/tenantgovernance-governancepolicytemplate.md) object in the response body.

## Examples

### Example 1: Update a custom governance policy template

#### Request

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
  "displayName": "String",
  "description": "String",
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


#### Response

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
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.governancePolicyTemplate",
  "displayName": "String",
  "description": "String",
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

### Example 2: Update the default governance policy template

#### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "update_governancepolicytemplate_default"
}
-->
``` http
PATCH https://graph.microsoft.com/beta/directory/tenantGovernance/governancePolicyTemplates/default
Content-Type: application/json

{
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


#### Response

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
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.governancePolicyTemplate",
  "id": "default",
  "displayName": "Default Policy Template",
  "description": "The system-provided default governance policy template",
  "version": "1.0",
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

