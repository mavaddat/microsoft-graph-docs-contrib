---
title: "governancePolicyTemplate resource type"
description: "Represents a policy template that defines the configuration for governance relationships."
author: "hafowler"
ms.date: 03/10/2026
ms.localizationpriority: medium
ms.subservice: "entra-tenantgovernance"
doc_type: resourcePageType
---

# governancePolicyTemplate resource type

Namespace: microsoft.graph.tenantGovernanceServices

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents a policy template that defines the configuration for governance relationships, including delegated administration role assignments and multi-tenant applications to provision. Policy templates are used when creating [governanceRequest](tenantgovernance-governancerequest.md) objects and are stored as snapshots in established [governanceRelationship](tenantgovernance-governancerelationship.md) objects.


Inherits from [microsoft.graph.entity](../resources/entity.md).


## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[List](../api/tenantgovernance-list-governancepolicytemplates.md)|[microsoft.graph.tenantGovernanceServices.governancePolicyTemplate](../resources/tenantgovernance-governancepolicytemplate.md) collection|Get a list of the [governancePolicyTemplate](../resources/tenantgovernance-governancepolicytemplate.md) objects and their properties.|
|[Create](../api/tenantgovernance-post-governancepolicytemplates.md)|[microsoft.graph.tenantGovernanceServices.governancePolicyTemplate](../resources/tenantgovernance-governancepolicytemplate.md)|Create a new governance policy template.|
|[Get](../api/tenantgovernance-governancepolicytemplate-get.md)|[microsoft.graph.tenantGovernanceServices.governancePolicyTemplate](../resources/tenantgovernance-governancepolicytemplate.md)|Read the properties of a [governancePolicyTemplate](../resources/tenantgovernance-governancepolicytemplate.md) object.|
|[Update](../api/tenantgovernance-governancepolicytemplate-update.md)|[microsoft.graph.tenantGovernanceServices.governancePolicyTemplate](../resources/tenantgovernance-governancepolicytemplate.md)|Update the properties of a governance policy template.|
|[Delete](../api/tenantgovernance-delete-governancepolicytemplates.md)|None|Delete a governance policy template.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|createdDateTime|DateTimeOffset|The date and time when the template was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC.|
|delegatedAdministrationRoleAssignments|[microsoft.graph.tenantGovernanceServices.delegatedAdministrationRoleAssignment](../resources/tenantgovernance-delegatedadministrationroleassignment.md) collection|A collection of delegated administration role assignments to be applied in the governed tenant when the governance relationship is established.|
|description|String|A description of the policy template.|
|displayName|String|The display name of the policy template.|
|governedTenantCanTerminate|Boolean|Indicates whether the governed tenant can terminate the relationship. When set to `true`, the governed tenant can initiate termination.|
|id|String|The unique identifier for the policy template. Inherited from [entity](../resources/entity.md).|
|lastModifiedDateTime|DateTimeOffset|The date and time when the template was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC.|
|multiTenantApplicationsToProvision|[microsoft.graph.tenantGovernanceServices.multiTenantApplicationsToProvision](../resources/tenantgovernance-multitenantapplicationstoprovision.md) collection|A collection of multi-tenant applications to be provisioned in the governed tenant when the governance relationship is established.|
|version|String|The version of the policy template.|

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
  "id": "String (identifier)",
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

