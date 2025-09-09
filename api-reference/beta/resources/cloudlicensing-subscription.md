---
title: "subscription resource type"
description: "Represents a subscription which backs an allotment."
author: "patrick-starrin"
ms.date: 07/18/2025
ms.localizationpriority: medium
ms.subservice: "cloud-licensing"
doc_type: resourcePageType
---

# subscription resource type

Namespace: microsoft.graph.cloudLicensing

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents a subscription which backs an allotment.

## Properties
|Property|Type|Description|
|:---|:---|:---|
|nextLifecycleDate|DateTime|The date on which the current state will transition to the next state.|
|startDate|DateTime|The date when the subscription started.|
|state|[microsoft.graph.cloudLicensing.subscriptionState](#state-values) | The current lifecycle state of the subscription. The possible values are: `active`, `warning`, `suspended`, `lockedOut`, `deleted`, `unknownFutureValue`.<br/><br/>If new values are added to this [evolvable enum](/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations) in the future, you must use the `Prefer: include-unknown-enum-members` request header to get them.<br/><br/>The **state** property is a multi-valued enumeration and the property can contain multiple values in a comma-separated list. Not nullable. Read-only.|
|subscriptionId|String|Identifier for the subscription.|
|tags|[microsoft.graph.cloudLicensing.subscriptionTags](#tags-values) | A set of flags which provide additional information about the subscription. The possible values are: `none`, `trial`, `unknownFutureValue`.<br/><br/>If new values are added to this [evolvable enum](/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations) in the future, you must use the `Prefer: include-unknown-enum-members` request header to get them.<br/><br/>The **tags** property is a multi-valued enumeration and the property can contain multiple values in a comma-separated list. Not nullable. Read-only.|


### state values

| Member            | Description                                                            |
|:------------------|:-----------------------------------------------------------------------|
| active              | The allotment is backed by an active, in-date subscription.                  |
| warning              | The allotment is backed by a subscription which has expired but is still within the grace period.            |
| suspended             | The allotment is backed by a subscription which has expired, is not within the grace period, and has been suspended. Licenses assigned from this allotment will cease to provide benefit.                    |
| lockedOut            | The allotment is backed by a subscription which is in a locked-out / deprovisioned state. Licenses assigned from this allotment will cease to provide benefit.          |
| deleted           | The allotment and its backing subscription have been deleted. Licenses assigned from this allotment will cease to exist or provide benefit |
| unknownFutureValue| Evolvable enumeration sentinel value. Don't use.                       |


### tags values

| Member            | Description                                                            |
|:------------------|:-----------------------------------------------------------------------|
| none              | Indicates no flags are enabled.                  |
| trial              | Indicates that the licenses in this allotment are backed by a trial subscription.            |
| unknownFutureValue| Evolvable enumeration sentinel value. Don't use.                       |


## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.cloudLicensing.allotment",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.cloudLicensing.subscription",
  "nextLifecycleDate": "2025-09-30T00:00:00.000Z",
  "startDate": "2025-07-18T00:00:00.000Z",
  "state": "active",
  "subscriptionId": "405ee855-dd74-f695-8d7e-be35a6788fe8",
  "tags": "none"
}
```

