---
title: "managedDeviceMobileAppConfigurationSettingState resource type"
description: "Managed Device Mobile App Configuration Setting State for a given device."
author: "jaiprakashmb"
ms.localizationpriority: medium
ms.subservice: "intune"
doc_type: resourcePageType
ms.date: 08/01/2024
---

# managedDeviceMobileAppConfigurationSettingState resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Managed Device Mobile App Configuration Setting State for a given device.

## Properties
|Property|Type|Description|
|:---|:---|:---|
|setting|String|The setting that is being reported|
|settingName|String|Localized/user friendly setting name that is being reported|
|instanceDisplayName|String|Name of setting instance that is being reported.|
|state|[complianceStatus](../resources/intune-shared-compliancestatus.md)|The compliance state of the setting. Possible values are: `unknown`, `notApplicable`, `compliant`, `remediated`, `nonCompliant`, `error`, `conflict`, `notAssigned`.|
|errorCode|Int64|Error code for the setting|
|errorDescription|String|Error description|
|userId|String|UserId|
|userName|String|UserName|
|userEmail|String|UserEmail|
|userPrincipalName|String|UserPrincipalName.|
|sources|[settingSource](../resources/intune-deviceconfig-settingsource.md) collection|Contributing policies|
|currentValue|String|Current value of setting on device|
|settingInstanceId|String|SettingInstanceId|

## Relationships
None

## JSON Representation
Here is a JSON representation of the resource.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.managedDeviceMobileAppConfigurationSettingState"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.managedDeviceMobileAppConfigurationSettingState",
  "setting": "String",
  "settingName": "String",
  "instanceDisplayName": "String",
  "state": "String",
  "errorCode": 1024,
  "errorDescription": "String",
  "userId": "String",
  "userName": "String",
  "userEmail": "String",
  "userPrincipalName": "String",
  "sources": [
    {
      "@odata.type": "microsoft.graph.settingSource",
      "id": "String",
      "displayName": "String",
      "sourceType": "String"
    }
  ],
  "currentValue": "String",
  "settingInstanceId": "String"
}
```