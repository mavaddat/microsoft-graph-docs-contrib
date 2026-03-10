---
title: "default governancePolicyTemplate resource type"
description: "Represents the default policy template that defines the configuration for governance relationships that are automatically generated for newly created add-on tenants"
author: "hafowler"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# governancePolicyTemplate resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents the default policy template that defines the configuration for governance relationships that are automatically generated for newly created add-on tenants, including delegated administration role assignments and multi-tenant applications to provision. Policy templates are used when creating [governanceRequest](tenantgovernance-governancerequest.md) objects and are stored as [snapshots](tenantgovernance-relationshippolicy) in established [governanceRelationship](tenantgovernance-governancerelationship.md) objects.


Inherits from [microsoft.graph.entity](../resources/entity.md).


## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[Get](../api/tenantgovernance-governancepolicytemplate-get.md)|[microsoft.graph.tenantGovernanceServices.governancePolicyTemplate](../resources/tenantgovernance-governancepolicytemplate.md)|Read the properties of a [governancePolicyTemplate](../resources/tenantgovernance-governancepolicytemplate.md) object.|
|[Update](../api/tenantgovernance-governancepolicytemplate-update.md)|[microsoft.graph.tenantGovernanceServices.governancePolicyTemplate](../resources/tenantgovernance-governancepolicytemplate.md)|Update the properties of a governance policy template.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|createdDateTime|DateTimeOffset|The date and time when the template was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC.|
|delegatedAdministrationRoleAssignments|[microsoft.graph.tenantGovernanceServices.delegatedAdministrationRoleAssignment](../resources/tenantgovernance-delegatedadministrationroleassignment.md) collection|A collection of delegated administration role assignments to be applied in the governed tenant when the governance relationship is established.|
|description|String|A description of the default policy template. Value is "Default policy template used in automatically created governance relationships for add on tenants". Not configurable.|
|displayName|String|The display name of the policy template. Value is "default". Not configurable.|
|id|String|The unique identifier for the policy template. Value is "default".|
|lastModifiedDateTime|DateTimeOffset|The date and time when the template was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC.|
|multiTenantApplicationsToProvision|[microsoft.graph.tenantGovernanceServices.multiTenantApplicationsToProvision](../resources/tenantgovernance-multitenantapplicationstoprovision.md) collection|A collection of multi-tenant applications to be provisioned in the governed tenant when the governance relationship is established.|
|version|String|The version of the policy template. Version count increased by 1 when updated.|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.tenantGovernanceServices.governancePolicyTemplate",
  "baseType": "microsoft.graph.entity",
  "openType": "id"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceServices.governancePolicyTemplate",
  "id": "default",
  "displayName": "default",
  "description": "Default policy template used in automatically created governance relationships for add on tenants",
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

