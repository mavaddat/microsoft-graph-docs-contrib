---
title: "Create governancePolicyTemplate"
description: "Create a new governance policy template."
author: "hafowler"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: apiPageType
---

# Create governancePolicyTemplate

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Create a new [governancePolicyTemplate](../resources/tenantgovernance-governancepolicytemplate.md) that defines the configuration for establishing governance relationships, including role assignments and applications to provision.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- {
  "blockType": "permissions",
  "name": "tenantgovernanceservices-tenantgovernance-post-governancepolicytemplates-permissions"
}
-->
[!INCLUDE [permissions-table](../includes/permissions/tenantgovernance-tenantgovernance-post-governancepolicytemplates-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /directory/tenantGovernance/governancePolicyTemplates
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.tenantGovernanceServices.governancePolicyTemplate](../resources/tenantgovernance-governancepolicytemplate.md) object.

You can specify the following properties when creating a **governancePolicyTemplate**.

|Property|Type|Description|
|:---|:---|:---|
|displayName|String|The display name of the policy template. Required.|
|description|String|A description of the policy template. Required.|
|multiTenantApplicationsToProvision|[microsoft.graph.tenantGovernanceServices.multiTenantApplicationsToProvision](../resources/tenantgovernance-multitenantapplicationstoprovision.md) collection|A collection of multi-tenant applications to be provisioned in the governed tenant when the governance relationship is established. Required.|
|delegatedAdministrationRoleAssignments|[microsoft.graph.tenantGovernanceServices.delegatedAdministrationRoleAssignment](../resources/tenantgovernance-delegatedadministrationroleassignment.md) collection|A collection of delegated administration role assignments to be applied in the governed tenant when the governance relationship is established. Required.|



## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.tenantGovernanceServices.governancePolicyTemplate](../resources/tenantgovernance-governancepolicytemplate.md) object in the response body.

## Examples

### Request

The following example shows a request.
<!-- {
  "blockType": "request",
  "name": "create_governancepolicytemplate_from_"
}
-->
``` http
POST https://graph.microsoft.com/beta/directory/tenantGovernance/governancePolicyTemplates
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
HTTP/1.1 201 Created
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

