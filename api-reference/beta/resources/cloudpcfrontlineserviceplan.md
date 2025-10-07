---
title: "cloudPcFrontLineServicePlan resource type (deprecated)"
description: "Represents a service plan that is available for use by up to three users."
author: "Guoan-Tang"
ms.localizationpriority: medium
ms.subservice: "cloud-pc"
doc_type: resourcePageType
ms.date: 05/23/2024
toc.title: "Cloud PC frontline service plan (deprecated)"
---

# cloudPcFrontLineServicePlan resource type (deprecated)

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

> [!CAUTION]
> The [cloudPcFrontLineServicePlan](../resources/cloudpcfrontlineserviceplan.md) resource and its APIs are deprecated and will stop returning data on March 31, 2026. Going forward, use the [cloudPcManagedLicense](../resources/cloudpcmanagedlicense.md) API instead.

Represents a service plan that provides an allotment of three Cloud PCs for the admin to provision for up to three users, but can't be assigned to a specific user. This service plan enables the service to create a concept of a time-share across these provisioned users, where customers can deploy a larger number of users. Windows 365 enforces a limit on active users at a given time, effectively creating an innovative way to provide the personalized experience of a Cloud PC along with the improved economics of sharing.

## Methods

|Method|Return type|Description|
|:---|:---|:---|
|[List](../api/virtualendpoint-list-frontlineserviceplans.md)|[cloudPcFrontLineServicePlan](../resources/cloudpcfrontlineserviceplan.md) collection|Get a list of the [cloudPcFrontLineServicePlan](../resources/cloudpcfrontlineserviceplan.md) objects and their properties.|
|[Get](../api/cloudpcfrontlineserviceplan-get.md)|[cloudPcFrontLineServicePlan](../resources/cloudpcfrontlineserviceplan.md)|Get the properties and relationships of a [cloudPcFrontLineServicePlan](../resources/cloudpcfrontlineserviceplan.md) object.|

## Properties

|Property|Type|Description|
|:---|:---|:---|
|displayName|String|The display name of the frontline service plan. For example, `2vCPU/8GB/128GB Front-line` or `4vCPU/16GB/256GB Front-line`.|
|id|String|The unique identifier (ID) of the frontline service plan.|
|totalCount|Int32|The total number of frontline service plans purchased by the customer.|
|usedCount|Int32|The number of service plans that have been used for the account.|

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.cloudPcFrontLineServicePlan",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.cloudPcFrontLineServicePlan",
  "displayName": "String",
  "id": "String (identifier)",
  "usedCount": "Int32",
  "totalCount": "Int32"
}
```
