---
title: "deviceEnrollmentPlatformRestriction resource type"
description: "Platform specific enrollment restrictions"
author: "jaiprakashmb"
ms.localizationpriority: medium
ms.subservice: "intune"
doc_type: resourcePageType
ms.date: 08/01/2024
---

# deviceEnrollmentPlatformRestriction resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Platform specific enrollment restrictions

## Properties
|Property|Type|Description|
|:---|:---|:---|
|platformBlocked|Boolean|Block the platform from enrolling|
|personalDeviceEnrollmentBlocked|Boolean|Block personally owned devices from enrolling|
|osMinimumVersion|String|Min OS version supported|
|osMaximumVersion|String|Max OS version supported|
|blockedManufacturers|String collection|Collection of blocked Manufacturers.|
|blockedSkus|String collection|Collection of blocked Skus.|

## Relationships
None

## JSON Representation
Here is a JSON representation of the resource.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.deviceEnrollmentPlatformRestriction"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.deviceEnrollmentPlatformRestriction",
  "platformBlocked": true,
  "personalDeviceEnrollmentBlocked": true,
  "osMinimumVersion": "String",
  "osMaximumVersion": "String",
  "blockedManufacturers": [
    "String"
  ],
  "blockedSkus": [
    "String"
  ]
}
```